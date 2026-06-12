---
title: "Borked package stuck in install queue"
date: 2009-08-05
forum: General Help
---

### Post by benbeecher on 2009-08-05
I managed to screw up my python configuration - I've since fixed it, but in the course of fixing it I somehow caused an error in dpkg, and now the package that caused the error is stuck in my install queue and reattempts to install every time I use apt. I ignored the errors for a while, but today I got a new error message added on (the unicode errors at the bottom), and I'd love some help in figuring out whats broken (and how to fix it :) )

Setting up python-nwsserver (1.5.2-4) ...
INFO: using unknown version '/usr/bin/python3.0' (debian_defaults not up-to-date?)
Starting the NWS serverTraceback (most recent call last):
  File "/usr/local/dram/twisted/twisted/application/app.py", line 690, in run
    runApp(config)
  File "/usr/local/dram/twisted/twisted/scripts/twistd.py", line 23, in runApp
    _SomeApplicationRunner(config).run()
  File "/usr/local/dram/twisted/twisted/application/app.py", line 411, in run
    self.application = self.createOrGetApplication()
  File "/usr/local/dram/twisted/twisted/application/app.py", line 494, in createOrGetApplication
    application = getApplication(self.config, passphrase)
--- <exception caught here> ---
  File "/usr/local/dram/twisted/twisted/application/app.py", line 505, in getApplication
    application = service.loadApplication(filename, style, passphrase)
  File "/usr/local/dram/twisted/twisted/application/service.py", line 390, in loadApplication
    application = sob.loadValueFromFile(filename, 'application', passphrase)
  File "/usr/local/dram/twisted/twisted/persisted/sob.py", line 210, in loadValueFromFile
    exec fileObj in d, d
  File "/etc/nws.tac", line 23, in <module>
    from nwss.server import NwsService
exceptions.ImportError: No module named nwss.server

Failed to load application: No module named nwss.server

 (failed).
invoke-rc.d: initscript nwsserver, action "start" failed.
dpkg: error processing python-nwsserver (--configure):
 subprocess post-installation script returned error exit status 1

Processing triggers for python-support ...
Compiling /var/lib/python-support/python2.5/httplib2/iri2uri.py ...
Sorry: UnicodeError: ("\\N escapes not supported (can't load unicodedata module)",)
Compiling /var/lib/python-support/python2.5/simplejson/tests/test_unicode.py ...
Sorry: UnicodeError: ("\\N escapes not supported (can't load unicodedata module)",)
Compiling /var/lib/python-support/python2.5/sphinx/directives/desc.py ...
Sorry: UnicodeError: ("\\N escapes not supported (can't load unicodedata module)",)
Compiling /var/lib/python-support/python2.5/sphinx/roles.py ...
Sorry: UnicodeError: ("\\N escapes not supported (can't load unicodedata module)",)
Compiling /var/lib/python-support/python2.5/tidy/test_tidy.py ...
Sorry: UnicodeError: ("\\N escapes not supported (can't load unicodedata module)",)
Compiling /var/lib/python-support/python2.5/turbogears/tests/test_controllers.py ...
Sorry: UnicodeError: ("\\N escapes not supported (can't load unicodedata module)",)
Compiling /var/lib/python-support/python2.6/plwm/outline.py ...
SyntaxError: ('invalid syntax', ('/var/lib/python-support/python2.6/plwm/outline.py', 65, 30, '            sx, sy, sw, sh, as = namepos\n'))

Compiling /var/lib/python-support/python2.6/pmock.py ...
SyntaxError: ('invalid syntax', ('/var/lib/python-support/python2.6/pmock.py', 313, 12, '    def with(self, *arg_constraints, **kwarg_constraints):\n'))

Compiling /var/lib/python-support/python2.6/pydoctor/ast_pp.py ...
SyntaxError: ('invalid syntax', ('/var/lib/python-support/python2.6/pydoctor/ast_pp.py', 116, 20, '        for (mod, as) in node.names:\n'))

Compiling /var/lib/python-support/python2.6/pyscript/groups.py ...
SyntaxError: ('invalid syntax', ('/var/lib/python-support/python2.6/pyscript/groups.py', 390, 6, "    as = options.get('as', a2)\n"))

Errors were encountered while processing:
 python-nwsserver
E: Sub-process /usr/bin/dpkg returned an error code (1)


/usr/share/python$ cat debian_defaults 
[DEFAULT]
# the default python version
default-version = python2.6

# all supported python versions
supported-versions = python2.5, python2.6

# formerly supported python versions
old-versions = python2.3, python2.4

# unsupported versions, including older versions
unsupported-versions = python2.3, python2.4

Thanks in advance!

---

### Post by Nexusx6 on 2009-08-05
Please wrap code that you put in your message in a Code tag. You can do this by pressing the Pound symbol next to the Quote tags and pasting your code in there.

That being said, try:
```
sudo dpkg-reconfigure -a
```
then
```
sudo apt-get update
```

---

