---
title: "cann't run googlecl please help"
date: 2010-06-28
forum: General Help
---

### Post by brijith on 2010-06-28
Hi all Please help me ...  

I am using Ubuntu9.10. I am trying to use googlecl to list docs in google doc account. When run the command to list it I am getting

```
brijith@dellware:~/Desktop$ google docs list
Please specify user: brijithp
/usr/lib/pymodules/python2.6/atom/http.py:225: DeprecationWarning: socket.ssl() is deprecated.  Use ssl.wrap_socket() instead.
  ssl = socket.ssl(p_sock, None, None)
/usr/lib/pymodules/python2.6/atom/http.py:226: DeprecationWarning: FakeSocket is deprecated, and won't be in 3.x.  Use the result of ssl.wrap_socket() directly instead.
  fake_sock = httplib.FakeSocket(p_sock, ssl)
Traceback (most recent call last):
  File "/usr/bin/google", line 448, in <module>
    main()
  File "/usr/bin/google", line 442, in main
    run_once(options, args)
  File "/usr/bin/google", line 320, in run_once
    if client.RequestAccess():
  File "/usr/lib/pymodules/python2.6/googlecl/service.py", line 197, in request_access
    request_token = self.FetchOAuthRequestToken()
  File "/usr/lib/pymodules/python2.6/gdata/service.py", line 403, in FetchOAuthRequestToken
    response = self.http_client.request('GET', str(request_token_url))
  File "/usr/lib/pymodules/python2.6/atom/http.py", line 135, in request
    connection.endheaders()
  File "/usr/lib/python2.6/httplib.py", line 892, in endheaders
    self._send_output()
  File "/usr/lib/python2.6/httplib.py", line 764, in _send_output
    self.send(msg)
  File "/usr/lib/python2.6/httplib.py", line 743, in send
    self.sock.sendall(str)
AttributeError: sendall
brijith@dellware:~/Desktop$
```

---

### Post by tom.h.miller on 2010-09-08
Someone just reported the same error that you're seeing. The issue seems to lie with python-gdata. I recommended upgrading to the latest version, but I don't know if that will solve the problem.

You can visit the issue tracker at [http://code.google.com/p/googlecl/issues/detail?id=280]("http://code.google.com/p/googlecl/issues/detail?id=280") to follow the progress of this problem.

---

