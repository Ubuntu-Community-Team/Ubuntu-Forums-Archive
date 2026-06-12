---
title: "cant  add new repository"
date: 2011-11-09
forum: General Help
---

### Post by jndmose on 2011-11-09
i normally get this reply please help

Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 77, in <module>
    ppa_info = get_ppa_info_from_lp(user, ppa_name)
  File "/usr/lib/python2.7/dist-packages/softwareproperties/ppa.py", line 65, in get_ppa_info_from_lp
    lp_page = urlopen(req).read()
  File "/usr/lib/python2.7/urllib2.py", line 126, in urlopen
    return _opener.open(url, data, timeout)
  File "/usr/lib/python2.7/urllib2.py", line 394, in open
    response = self._open(req, data)
  File "/usr/lib/python2.7/urllib2.py", line 412, in _open
    '_open', req)
  File "/usr/lib/python2.7/urllib2.py", line 372, in _call_chain
    result = func(*args)
  File "/usr/lib/python2.7/urllib2.py", line 1209, in https_open
    return self.do_open(httplib.HTTPSConnection, req)
  File "/usr/lib/python2.7/urllib2.py", line 1171, in do_open
    raise URLError(err)
urllib2.URLError: <urlopen error [Errno 8] _ssl.c:503: EOF occurred in violation of protocol>

---

### Post by notgary on 2011-11-10
A [bug report]("https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/867580") was filed for this very issue about a month ago, and has since been amrked as a duplicate of a private bug report. Reports are ususally made private if they contain sensitive information from a users computer or if it is considered a security vulnerability.

---

### Post by notgary on 2011-11-10
I've sent an email to both the Ubuntu Desktop and Ubuntu Users mailing lists to see if anyone can shed some light on why the bug report is private.

---

### Post by notgary on 2011-11-10
The [bug report]("https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/837203") has been made public, and it seems there are a lot of duplicates that people have been reporting :P

You could try adding your two cents there since that's where it seems most likely to be resolved.

---

