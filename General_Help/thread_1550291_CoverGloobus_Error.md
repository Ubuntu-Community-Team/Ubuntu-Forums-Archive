---
title: "CoverGloobus Error"
date: 2010-08-10
forum: General Help
---

### Post by maniacss on 2010-08-10
Hello. I tried running CoverGloobus from the command line, it didn't start and I get this -

```
 [WARNING] Using default Configuration
[INFO] UI: Theme: BadChoice
Traceback (most recent call last):
  File "/usr/share/covergloobus/covergloobus.py", line 531, in <module>
    sys.exit(cg.main())
  File "/usr/share/covergloobus/covergloobus.py", line 87, in main
    self.init() #Init configurations
  File "/usr/share/covergloobus/covergloobus.py", line 108, in init
    self.change_song()
  File "/usr/share/covergloobus/covergloobus.py", line 461, in change_song
    self.track.artist, self.track.album, c)
  File "/usr/share/covergloobus/WEBServices.py", line 60, in amazon_download_cover
    web = urllib.urlopen(URL)
  File "/usr/lib/python2.6/urllib.py", line 86, in urlopen
    return opener.open(url)
  File "/usr/lib/python2.6/urllib.py", line 205, in open
    return getattr(self, name)(url)
  File "/usr/lib/python2.6/urllib.py", line 344, in open_http
    h.endheaders()
  File "/usr/lib/python2.6/httplib.py", line 904, in endheaders
    self._send_output()
  File "/usr/lib/python2.6/httplib.py", line 776, in _send_output
    self.send(msg)
  File "/usr/lib/python2.6/httplib.py", line 735, in send
    self.connect()
  File "/usr/lib/python2.6/httplib.py", line 716, in connect
    self.timeout)
  File "/usr/lib/python2.6/socket.py", line 514, in create_connection
    raise error, msg
IOError: [Errno socket error] [Errno 110] Connection timed out 
```Everything was working fine last time I used it and now suddenly this bs.. I tried reinstalling it and deleting the .cfg file but it didn't work. Any help would be very appreciated. :)

---

### Post by maniacss on 2010-08-10
bump

---

### Post by maniacss on 2010-08-10
bump :/

---

### Post by maniacss on 2010-08-11
...nobody? :|

---

