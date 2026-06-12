---
title: "gmailfs not working !!"
date: 2006-03-23
forum: General Help
---

### Post by man_stupendous on 2006-03-23
Hi!,

I am using Hedgehog 5.04.
I have these installed version
1. fuse-utils : 2.2.1ubuntu1 ( from hedgehog)
2. python-2.4 : 2.4.1 ( from hedgehog)
3. python-gmail :  0.0.8 + cvs20050208-2ubuntu2 ( from dapper )
4. python2.4-openssl - 0.6.1ubuntu3 ( from dapper )
4. gmailfs - 0.6.2ubuntu1 ( from dapper )


Now after having installed all of these, when i do : 

# mount.gmailfs none /mnt/gmailfs/ -o username=<my_uname>, password=<my-passwd>, fsname=zOlRRa

it is giving me this error :


Traceback (most recent call last):
  File "/usr/bin/mount.gmailfs", line 162, in ?
    main(mountpoint, odata, useEncfs)
  File "/usr/bin/mount.gmailfs", line 88, in main
    gmailfs.main(mountpoint, odata)
  File "/usr/share/gmailfs/gmailfs.py", line 1133, in main
    server = Gmailfs(mountpoint, odata)
  File "/usr/share/gmailfs/gmailfs.py", line 603, in __init__
    self.ga.login()
  File "/usr/lib/python2.4/site-packages/libgmail/__init__.py", line 271, in login
    pageData = self._retrievePage(req)
  File "/usr/lib/python2.4/site-packages/libgmail/__init__.py", line 296, in _retrievePage
    resp = urllib2.urlopen(req)
  File "/usr/lib/python2.4/urllib2.py", line 130, in urlopen
    return _opener.open(url, data)
  File "/usr/lib/python2.4/urllib2.py", line 364, in open
    response = meth(req, response)
  File "/usr/lib/python2.4/urllib2.py", line 468, in http_response
    code, msg, hdrs = response.code, response.msg, response.info()
AttributeError: addinfourl instance has no attribute 'code'

What is the problem ?
My connection to the net is thru a proxy which i have given in gmail.conf.

---

### Post by wannabelinuxconvert on 2006-03-23
Remove everything you've installed and then install Fuse from 

[http://fuse.sourceforge.net/]("http://fuse.sourceforge.net/")

Following their installation instructions from about half way down the page.

And then head on over to 

[http://richard.jones.name/google-hacks/gmail-filesystem/gmail-filesystem.html]("http://richard.jones.name/google-hacks/gmail-filesystem/gmail-filesystem.html")

And follow the installation instructions from there word for word and you'll have it up and running in no time. That's what I found because the packages from Synaptic are outdated and badly configured.

Hope this helps.

Mic

---

