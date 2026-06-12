---
title: "Software-center don't start"
date: 2010-07-07
forum: General Help
---

### Post by Olioso on 2010-07-07
Hi,
I have installet ubuntu lucid and it works fine.
After the installation of other user software like keepass and truecrypt, the software-center utility doesn't start.
I start it but the process start and after few second it exit from top utility. No screen output it doesn't start.
I tried to start in terminal and receive this log:
Traceback (most recent call last):
  File "/usr/bin/software-center", line 80, in <module>
    app = SoftwareCenterApp(datadir, xapian_base_path)
  File "/usr/share/software-center/softwarecenter/app.py", line 221, in __init__
    self.config = get_config()
  File "/usr/share/software-center/softwarecenter/backend/config.py", line 43, in get_config
    _software_center_config = SoftwareCenterConfig(SOFTWARE_CENTER_CONFIG_FILE)
  File "/usr/share/software-center/softwarecenter/backend/config.py", line 30, in __init__
    self.read(self.configfile)
  File "/usr/lib/python2.6/ConfigParser.py", line 286, in read
    self._read(fp, filename)
  File "/usr/lib/python2.6/ConfigParser.py", line 482, in _read
    raise MissingSectionHeaderError(fpname, lineno, line)
ConfigParser.MissingSectionHeaderError: File contains no section headers.
file: /home/lucaolioso/.config/softwarecenter/softwarecenter.cfg, line: 1
'\x1f\x8b\x08\x00\x00\x00\x00\x00\x02\xff\xb5\xbd\xe9z\xdb\xc6\xb2(\xfa\xdfO!!^4`B\x14)\x0fI\x08\xb5\xf8\xd9\xb2l+\x1ec9#\xa5\xf8k\x0c$!\x81\x83\x00P#y\x9e\xe7\xbc\xc7y\xb1[U=\xa0\x01\x82\x92\xb3\xf6\xbe+\xcb"\xd0\xe8\xb9\xab'
Can anyone help me.
Regards
Luca

---

### Post by cariboo on 2010-07-07
Try deleting /home/lucaolioso/.config/softwarecenter/softwarecenter.cfg

To see if that helps. A new config file will be created when you start the application.

---

