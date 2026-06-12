---
title: "How to fake lsb_release ?"
date: 2011-11-15
forum: General Help
---

### Post by Rime2 on 2011-11-15
I'm trying to install the 32 bit libraries, but it keeps failing because lsb_release doesn't work.  Removing and reinstalling lsb_release doesn't work.   Hard coding an lsb_release doesn't work either : it runs just fine if I run it by hand, but fails with an unexpected operator error on line 11 if I try to install the libraries.  

Any clue*4s appreciated...

Thanks !

Step 1 : Learning that the package for lsb_release is lsb-release
root@vm1:/usr/bin# apt-get autoremove lsb_release
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package lsb_release
root@vm1:/usr/bin# apt-get install lsb_release
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package lsb_release

Step 2 : removing and installing lsb_release
root@vm1:/usr/bin# apt-get autoremove lsb-release
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  lsb-release python-central
0 upgraded, 0 newly installed, 2 to remove and 27 not upgraded.
After this operation, 487 kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 99295 files and directories currently installed.)
Removing lsb-release ...
Removing python-central ...
Processing triggers for man-db ...
root@vm1:/usr/bin# apt-get install lsb-release
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  python-central
Suggested packages:
  lsb
The following NEW packages will be installed:
  lsb-release python-central
0 upgraded, 2 newly installed, 0 to remove and 27 not upgraded.
Need to get 0 B/52.2 kB of archives.
After this operation, 487 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Selecting previously deselected package python-central.
(Reading database ... 99260 files and directories currently installed.)
Unpacking python-central (from .../python-central_0.6.15ubuntu5_all.deb) ...
Selecting previously deselected package lsb-release.
Unpacking lsb-release (from .../lsb-release_4.0-0ubuntu11_all.deb) ...
Processing triggers for man-db ...
Setting up python-central (0.6.15ubuntu5) ...
Setting up lsb-release (4.0-0ubuntu11) ...
Processing triggers for python-central ...

Step 3 : Learning that it still doesn't work
root@vm1:/usr/bin# /usr/bin/lsb_release
Traceback (most recent call last):
  File "/usr/bin/lsb_release", line 26, in <module>
    import lsb_release
ImportError: No module named lsb_release

Step 4 : attempting to install with fake lsb_release
root@vm1:/usr/bin# apt-get install ia32-libs
Reading package lists... Done
Building dependency tree
Reading state information... Done
(snip)
Setting up lib32ncursesw5 (5.7+20101128-1) ...
Setting up ia32-libs (20090808ubuntu13) ...
No LSB modules are available.
[: 11: Distributor: unexpected operator
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

Hard coded lsb_release :
root@vm1:/usr/bin# cat /usr/bin/lsb_release.new
#!/usr/bin/python

# lsb_release command for Debian
# (C) 2005-08 Chris Lawrence <lawrencc@debian.org>

#    This package is free software; you can redistribute it and/or modify
#    it under the terms of the GNU General Public License as published by
#    the Free Software Foundation; version 2 dated June, 1991.

#    This package is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU General Public License for more details.

#    You should have received a copy of the GNU General Public License
#    along with this package; if not, write to the Free Software
#    Foundation, Inc., 59 Temple Place - Suite 330, Boston, MA
#    02111-1307, USA.

from optparse import OptionParser
import sys
import commands
import os
import re

# import lsb_release

def main():
    parser = OptionParser()
    parser.add_option('-v', '--version', dest='version', action='store_true',
                      default=False,
                      help="show LSB modules this system supports")
    parser.add_option('-i', '--id', dest='id', action='store_true',
                      default=False,
                      help="show distributor ID")
    parser.add_option('-d', '--description', dest='description',
                      default=False, action='store_true',
                      help="show description of this distribution")
    parser.add_option('-r', '--release', dest='release',
                      default=False, action='store_true',
                      help="show release number of this distribution")
    parser.add_option('-c', '--codename', dest='codename',
                      default=False, action='store_true',
                      help="show code name of this distribution")
    parser.add_option('-a', '--all', dest='all',
                      default=False, action='store_true',
                      help="show all of the above information")
    parser.add_option('-s', '--short', dest='short',
                      action='store_true', default=False,
                      help="show requested information in short format")

    (options, args) = parser.parse_args()
    if args:
        parser.error("No arguments are permitted")

    short = (options.short)
    none = not (options.all or options.version or options.id or
                options.description or options.codename or options.release)

    print >> sys.stderr, "No LSB modules are available."

    if options.id or options.all:
        print 'Distributor ID: Ubuntu'

    if options.description or options.all:
        print 'Description: Ubuntu 11.04'

    if options.release or options.all:
        print 'Release: 11.04'

    if options.codename or options.all:
        print 'Codename: natty'

if __name__ == '__main__':
    main()

---

### Post by Rime2 on 2011-11-15
lsb_fakery : found a web page where somebody had the output of lsb_release -as, and that worked.  32 bit libraries successfully installed, and now it's complaining about :
ImportError: /usr/local/lib/python2.7/lib-dynload/pyexpat.so: undefined symbol: PyUnicodeUCS4_Decode    Sigh.  

    if none or options.all or options.version:
        print >> sys.stderr, "No LSB modules are available."

    if options.id or options.all:
        if short:
            print 'Ubuntu'
        else:
            print 'Distributor ID:      Ubuntu'

    if options.description or options.all:
        if short:
            print 'Ubuntu 11.04'
        else:
            print 'Description: Ubuntu 11.04'

    if options.release or options.all:
        if short:
            print '11.04'
        else:
            print 'Release:     11.04'

    if options.codename or options.all:
        if short:
            print 'natty'
        else:
            print 'Codename: natty'

Finally got libraries installed.  On to the next issue....

---

