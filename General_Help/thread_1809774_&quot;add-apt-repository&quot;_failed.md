---
title: "&quot;add-apt-repository&quot; failed"
date: 2011-07-22
forum: General Help
---

### Post by raja.genupula on 2011-07-22
```
assassin@genupulas:~$ sudo add-apt-repository ppa:ingalex/super-boot-manager
Exception in thread Thread-1:
Traceback (most recent call last):
  File "/usr/lib/python2.7/threading.py", line 552, in __bootstrap_inner
    self.run()
  File "/usr/lib/python2.7/dist-packages/softwareproperties/ppa.py", line 63, in run
    self.add_ppa_signing_key(self.ppa_path)
  File "/usr/lib/python2.7/dist-packages/softwareproperties/ppa.py", line 79, in add_ppa_signing_key
    lp_page = urlopen(req).read()
  File "/usr/lib/python2.7/urllib2.py", line 126, in urlopen
    return _opener.open(url, data, timeout)
  File "/usr/lib/python2.7/urllib2.py", line 391, in open
    response = self._open(req, data)
  File "/usr/lib/python2.7/urllib2.py", line 409, in _open
    '_open', req)
  File "/usr/lib/python2.7/urllib2.py", line 369, in _call_chain
    result = func(*args)
  File "/usr/lib/python2.7/urllib2.py", line 1193, in https_open
    return self.do_open(httplib.HTTPSConnection, req)
  File "/usr/lib/python2.7/urllib2.py", line 1156, in do_open
    r = h.getresponse(buffering=True)
  File "/usr/lib/python2.7/httplib.py", line 1027, in getresponse
    response.begin()
  File "/usr/lib/python2.7/httplib.py", line 407, in begin
    version, status, reason = self._read_status()
  File "/usr/lib/python2.7/httplib.py", line 371, in _read_status
    raise BadStatusLine(line)
BadStatusLine: ''

```

thanks in advance

---

### Post by ardinotow on 2011-10-21
that because your network connection is slow, try adding repository again when your internet/network connection stable

---

