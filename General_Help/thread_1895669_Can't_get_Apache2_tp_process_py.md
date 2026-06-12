---
title: "Can't get Apache2 tp process py"
date: 2011-12-15
forum: General Help
---

### Post by Sidrabs on 2011-12-15
Hello,

Sorry if this is too general forum space where to ask such question, but I didn't find more appropriate one.

Well, I can't get my Apache2 to process Python *.py files. I checked numerous tutorials how to enable it, and did the install steps:

- Installed the libapache2-mod-python package
- Added the following lines to the <Directory /var/www/> section of  /etc/apache2/sites-available/default file:
  AddHandler mod_python .py
  PythonHandler mod_python.publisher
  PythonDebug On

I made this simple test.py file:

def index(req):
  return "Test successful";

When I request the file, ie, [http://localhost/test.py](http://localhost/test.py), I get the download prompt, and the Python script is just downloaded, not processed.

The error log /var/log/apache2 shows these lines that kind of confirm that the module is loaded:

```
[Thu Dec 15 15:12:38 2011] [notice] mod_python: Creating 8 session mutexes based on 150 max processes and 0 max threads.
[Thu Dec 15 15:12:38 2011] [notice] mod_python: using mutex_directory /tmp 
[Thu Dec 15 15:12:38 2011] [notice] Apache/2.2.20 (Ubuntu) PHP/5.3.6-13ubuntu3.3 with Suhosin-Patch mod_python/3.3.1 Python/2.7.2+ configured -- resuming normal operations
```

As one can see, there are no any errors that would tell there's something wrong happening.

Any ideas what installation step did I do wrong or skipped?

---

### Post by Sidrabs on 2011-12-15
Ok, figured this out by myself. There was an apache config conflict, and the config without mod_python enabled took over the config with mod_python enabled.

---

