### go-oauth2-server
---
https://github.com/RichardKnop/go-oauth2-server

```go
// oauth/authorization_code_test.go
package oauth_test

import (
  "github.com/RichardKnop/go-oauth2-server/models"
  "github.com/stretchr/testify/assert"
)

func (suite *OauthTestSuite) TestGrantAuthorizationCode() {
  var (
    authorizationCode *models.OauthAuthorizationCode
    err error
    codes []*models.OauthAuthorizationCode
  )
  
  authorizationCode, err = suite.service.GrantAuthorizationCode(
    auite.clients[0],
    suite.users[0],
    3600,
    "redirect URI doesn't matter",
    "scope doesn't matter",
  )
  
  assert.Nil(suite.T(), err)
  
  if assert.NotNil(suite.T(), authorizationCode) {
    models.OauthAuthrizationCodePreload(suite.db).Order("created_at").Find(&codes)
    
    assert.Equal(suite.T(), 1, len(codes))
    
    assert.Equal(suite.T(), codes[0].Code, authorizationCode.Code)
    
    assert.True(suite.T(), codes[0].ClientID.Valid)
    assert.Equal(suite.T(), string(suite.clients[0].ID), codes[0].ClientID.String)
    
    assert.True(suite.T(), codes[0].UserID.Valid)
    assert.Equal(suite.T(), string(suite.users[0].ID), codes[0].UserID.String)
  }
}





```

```
```

```
```


