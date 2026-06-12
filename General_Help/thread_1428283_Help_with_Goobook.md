---
title: "Help with Goobook"
date: 2010-03-12
forum: General Help
---

### Post by chaanakya_chiraag on 2010-03-12
Hey guys!  I'm running Ubuntu Karmic Koala with Fluxbox.  I am trying to use goobook, but it won't let me log in to the google server.  When I type in ```
goobook.py reload
``` it gives me ```
Traceback (most recent call last):
  File "/home/chiraag/scripts/goobook.py", line 294, in <module>
    main()
  File "/home/chiraag/scripts/goobook.py", line 288, in main
    goobk.fetch()
  File "/home/chiraag/scripts/goobook.py", line 134, in fetch
    client = self.__get_client()
  File "/home/chiraag/scripts/goobook.py", line 81, in __get_client
    client.ClientLogin(email=self.email, password=self.password, service='cp', source='goobook')
  File "/usr/local/lib/python2.6/dist-packages/gdata/client.py", line 442, in client_login
    captcha_token=captcha_token, captcha_response=captcha_response)
  File "/usr/local/lib/python2.6/dist-packages/gdata/client.py", line 360, in request_client_login_token
    raise BadAuthentication('Incorrect username or password')
gdata.client.BadAuthentication: Incorrect username or password
```My .netrc contains:
```
machine google.com
    login EMAIL ADDRESS
    password PASSWORD
```

Any help would be appreciated.  Thanks!
- Chiraag

---

### Post by chaanakya_chiraag on 2010-03-14
*Bump*  Anyone?

---

### Post by chaanakya_chiraag on 2010-03-18
*Bump* again.  Anyone have a clue of what is going on here?  Thanks!

---

