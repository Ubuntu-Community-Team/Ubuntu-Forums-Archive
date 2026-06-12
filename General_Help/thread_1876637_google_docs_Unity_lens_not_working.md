---
title: "google docs Unity lens not working"
date: 2011-11-06
forum: General Help
---

### Post by iamnigel on 2011-11-06
I'm using Ubuntu 11.10, and the Gdocs (google docs) unity lens is not working.

After I typed "unity-lens-gdocs.py" into my terminal, this came up, implying that I had the wrong username and password, but it's definitely correct:

iamnigel@ubuntu:~$ gksu gedit /usr/bin/unity-lens-gdocs.py
iamnigel@ubuntu:~$ unity-lens-gdocs.py
(process:2511): libunity-DEBUG: unity-scope-factory.vala:57: Searching for Scopes in /usr/share/unity/lenses/gdocs
Traceback (most recent call last):
  File "/usr/bin/unity-lens-gdocs.py", line 279, in <module>
    daemon = Daemon()
  File "/usr/bin/unity-lens-gdocs.py", line 48, in __init__
    self._scope = UserScope();
  File "/usr/bin/unity-lens-gdocs.py", line 126, in __init__
    self._client.source);
  File "/usr/lib/pymodules/python2.7/gdata/client.py", line 442, in client_login
    captcha_token=captcha_token, captcha_response=captcha_response)
  File "/usr/lib/pymodules/python2.7/gdata/client.py", line 360, in request_client_login_token
    raise BadAuthentication('Incorrect username or password')
gdata.client.BadAuthentication: Incorrect username or password
iamnigel@ubuntu:~$

---

### Post by bluexrider on 2011-11-06
Sounds like a program issue with G-docs. Try [http://docs.google.com/support/](http://docs.google.com/support/)

---

