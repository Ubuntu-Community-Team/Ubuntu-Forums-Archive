---
title: "Software center wont start:/"
date: 2010-09-11
forum: General Help
---

### Post by cnordskog on 2010-09-11
I have recently been having problem starting my software center.
even opening it in sudo in the terminal does not work anymore and I get this error report.

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
file: /home/cnordskog/.config/softwarecenter/softwarecenter.cfg, line: 1
'\xd9\xd5\x05\xf9 \xa1c\xd7\x00\x00\x00\x11\xdd\xacf\xd9\x00\x00\x00\xa9\x00\x00\x02\x00\x00\x00\x10\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00'

---

### Post by davidmohammed on 2010-09-11
this is a guess - it appears it is having some problem reading the software center config file - try renaming the folder to something else and see if it gets recreated correctly when you restart software centre

i.e.

mv /home/cnordskog/.config/softwarecenter /home/cnordskog/.config/softwarecenter_backup

---

### Post by cnordskog on 2010-09-11
Thank you:P That seemed to work:P

---

