---
title: "Xlibs in dapper 5"
date: 2006-03-17
forum: General Help
---

### Post by Zer0d on 2006-03-17
Im trying to install cedega but cedega 5.1 depends on one package named xlibs:
```
dpkg -i cedega_5.1_i386.deb
Selecting previously deselected package cedega.
(Reading database ... 75975 files and directories currently installed.)
Unpacking cedega (from cedega_5.1_i386.deb) ...
dpkg: dependency problems prevent configuration of cedega:
 cedega depends on xlibs (>> 4.1.0); however:
  Package xlibs is not installed.
dpkg: error processing cedega (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 cedega

```

When i installed cedega in breezy it was no problems and it was running fine.
How can i fix this and what is causing it and why is it working in Breezy and not Dapper Drake Flight 5?

I also tried to get xlibs with apt-get but then i get this message:
```
apt-get install xlibs
Reading package lists... Done
Building dependency tree... Done
Package xlibs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libxft1 xkeyboard-config
E: Package xlibs has no installation candidate

```

Cedega gets installed it just ignores the error, but when it is installed it wont run at all.

---

### Post by Zer0d on 2006-03-17
I got it working by following guide:
[http://www.transgaming.com/showthread.php?msg=59595&forum=1262&thread=59562](http://www.transgaming.com/showthread.php?msg=59595&forum=1262&thread=59562)

But i need to run cedega from the terminal or else it wont start.

---

### Post by Zer0d on 2006-03-17
Something is still wrong hmm:
```
Traceback (most recent call last):
  File "/bin/lsb_release", line 20, in ?
    from optparse import OptionParser
  File "/usr/lib/transgaming_cedega/lib/python2.3/optparse.py", line 72, in ?
    import textwrap
  File "/usr/lib/transgaming_cedega/lib/python2.3/textwrap.py", line 10, in ?
    import string, re
  File "/usr/lib/transgaming_cedega/lib/python2.3/re.py", line 5, in ?
    from sre import *
  File "/usr/lib/transgaming_cedega/lib/python2.3/sre.py", line 97, in ?
    import sre_compile
  File "/usr/lib/transgaming_cedega/lib/python2.3/sre_compile.py", line 17, in ?
    assert _sre.MAGIC == MAGIC, "SRE module mismatch"
AssertionError: SRE module mismatch
Traceback (most recent call last):
  File "/bin/lsb_release", line 20, in ?
    from optparse import OptionParser
  File "/usr/lib/transgaming_cedega/lib/python2.3/optparse.py", line 72, in ?
    import textwrap
  File "/usr/lib/transgaming_cedega/lib/python2.3/textwrap.py", line 10, in ?
    import string, re
  File "/usr/lib/transgaming_cedega/lib/python2.3/re.py", line 5, in ?
    from sre import *
  File "/usr/lib/transgaming_cedega/lib/python2.3/sre.py", line 97, in ?
    import sre_compile
  File "/usr/lib/transgaming_cedega/lib/python2.3/sre_compile.py", line 17, in ?
    assert _sre.MAGIC == MAGIC, "SRE module mismatch"
AssertionError: SRE module mismatch
Traceback (most recent call last):
  File "/bin/lsb_release", line 20, in ?
    from optparse import OptionParser
  File "/usr/lib/transgaming_cedega/lib/python2.3/optparse.py", line 72, in ?
    import textwrap
  File "/usr/lib/transgaming_cedega/lib/python2.3/textwrap.py", line 10, in ?
    import string, re
  File "/usr/lib/transgaming_cedega/lib/python2.3/re.py", line 5, in ?
    from sre import *
  File "/usr/lib/transgaming_cedega/lib/python2.3/sre.py", line 97, in ?
    import sre_compile
  File "/usr/lib/transgaming_cedega/lib/python2.3/sre_compile.py", line 17, in ?
    assert _sre.MAGIC == MAGIC, "SRE module mismatch"
AssertionError: SRE module mismatch
Traceback (most recent call last):
  File "/usr/lib/transgaming_cedega/setup_wizard_gui.py", line 150, in on_forward_button_clicked
    p2p_gui.check_for_updates(self, 1) # 1 means we're calling from the wizard
  File "/usr/lib/transgaming_cedega/p2p_gui.py", line 162, in check_for_updates
    ret.append(get_latest_version(caller_gui, calling_from_wizard))
  File "/usr/lib/transgaming_cedega/p2p_gui.py", line 189, in get_latest_version
    install_cedega_engine_helper.install_cedega_engine(install_cedega_engine.INSTALL_DOWNLOAD_CHECK_UPDATES)
  File "/usr/lib/transgaming_cedega/install_cedega_engine.py", line 121, in install_cedega_engine
    self.get_latest_version()
  File "/usr/lib/transgaming_cedega/install_cedega_engine.py", line 245, in get_latest_version
    except socket.gaierror, e:
NameError: global name 'socket' is not defined
Traceback (most recent call last):
  File "/bin/lsb_release", line 20, in ?
    from optparse import OptionParser
  File "/usr/lib/transgaming_cedega/lib/python2.3/optparse.py", line 72, in ?
    import textwrap
  File "/usr/lib/transgaming_cedega/lib/python2.3/textwrap.py", line 10, in ?
    import string, re
  File "/usr/lib/transgaming_cedega/lib/python2.3/re.py", line 5, in ?
    from sre import *
  File "/usr/lib/transgaming_cedega/lib/python2.3/sre.py", line 97, in ?
    import sre_compile
  File "/usr/lib/transgaming_cedega/lib/python2.3/sre_compile.py", line 17, in ?
    assert _sre.MAGIC == MAGIC, "SRE module mismatch"
AssertionError: SRE module mismatch
Traceback (most recent call last):
  File "/bin/lsb_release", line 20, in ?
    from optparse import OptionParser
  File "/usr/lib/transgaming_cedega/lib/python2.3/optparse.py", line 72, in ?
    import textwrap
  File "/usr/lib/transgaming_cedega/lib/python2.3/textwrap.py", line 10, in ?
    import string, re
  File "/usr/lib/transgaming_cedega/lib/python2.3/re.py", line 5, in ?
    from sre import *
  File "/usr/lib/transgaming_cedega/lib/python2.3/sre.py", line 97, in ?
    import sre_compile
  File "/usr/lib/transgaming_cedega/lib/python2.3/sre_compile.py", line 17, in ?
    assert _sre.MAGIC == MAGIC, "SRE module mismatch"
AssertionError: SRE module mismatch
Traceback (most recent call last):
  File "/bin/lsb_release", line 20, in ?
    from optparse import OptionParser
  File "/usr/lib/transgaming_cedega/lib/python2.3/optparse.py", line 72, in ?
    import textwrap
  File "/usr/lib/transgaming_cedega/lib/python2.3/textwrap.py", line 10, in ?
    import string, re
  File "/usr/lib/transgaming_cedega/lib/python2.3/re.py", line 5, in ?
    from sre import *
  File "/usr/lib/transgaming_cedega/lib/python2.3/sre.py", line 97, in ?
    import sre_compile
  File "/usr/lib/transgaming_cedega/lib/python2.3/sre_compile.py", line 17, in ?
    assert _sre.MAGIC == MAGIC, "SRE module mismatch"
AssertionError: SRE module mismatch
```

When i try to install games i cedega i get these messages in terminal:
```
Updating TransGaming config and registry info
WARNING: Your old config file has been moved to config.old. Any modifications you made to this file
will have to be replaced.
Invalid path 'c:\windows' for windows directory: does not exist
Perhaps you have not properly edited or created your Wine configuration file.
This is (supposed to be) '/home/zer0d/.cedega/Warcraft 3 ROC/TFT/config'
cp: target `/home/zer0d/.cedega/Warcraft 3 ROC/TFT/c_drive/windows/' is not a directory: No such file or directory
ln: creating symbolic link `/home/zer0d/.cedega/Warcraft 3 ROC/TFT/c_drive/windows/system32/regsvr32' to `/home/zer0d/.cedega/.winex_ver/winex-5.1/winex/bin/regsvr32': No such file or directory
ln: creating symbolic link `/home/zer0d/.cedega/Warcraft 3 ROC/TFT/c_drive/windows/system32/regsvr32.so' to `/home/zer0d/.cedega/.winex_ver/winex-5.1/winex/bin/regsvr32.so': No such file or directory
ln: creating symbolic link `/home/zer0d/.cedega/Warcraft 3 ROC/TFT/c_drive/windows/system32/regsvr32.exe' to `/home/zer0d/.cedega/.winex_ver/winex-5.1/winex/bin/regsvr32': No such file or directory
ln: creating symbolic link `/home/zer0d/.cedega/Warcraft 3 ROC/TFT/c_drive/windows/system32/regsvr32.exe.so' to `/home/zer0d/.cedega/.winex_ver/winex-5.1/winex/bin/regsvr32.so': No such file or directory
ln: creating symbolic link `/home/zer0d/.cedega/Warcraft 3 ROC/TFT/c_drive/windows/system32/wcmd.exe' to `/home/zer0d/.cedega/.winex_ver/winex-5.1/winex/bin/wcmd': No such file or directory
ln: creating symbolic link `/home/zer0d/.cedega/Warcraft 3 ROC/TFT/c_drive/windows/system32/wcmd.exe.so' to `/home/zer0d/.cedega/.winex_ver/winex-5.1/winex/bin/wcmd.so': No such file or directory
ln: creating symbolic link `/home/zer0d/.cedega/Warcraft 3 ROC/TFT/c_drive/windows/system32/winebrowserlink' to `/home/zer0d/.cedega/.winex_ver/winex-5.1/winex/bin/winebrowserlink': No such file or directory
ln: creating symbolic link `/home/zer0d/.cedega/Warcraft 3 ROC/TFT/c_drive/windows/system32/winebrowserlink.so' to `/home/zer0d/.cedega/.winex_ver/winex-5.1/winex/bin/winebrowserlink.so': No such file or directory
cat: /home/zer0d/.transgaming_global/Fonts/tg_font_version: No such file or directory
/home/zer0d/.cedega/.winex_ver/winex-5.1/bin/winex3: line 176: [: -lt: unary operator expected
Update complete
Invalid path 'c:\windows' for windows directory: does not exist
Perhaps you have not properly edited or created your Wine configuration file.
This is (supposed to be) '/home/zer0d/.cedega/Warcraft 3 ROC/TFT/config'
Invalid path 'c:\windows' for windows directory: does not exist
Perhaps you have not properly edited or created your Wine configuration file.
This is (supposed to be) '/home/zer0d/.cedega/Warcraft 3 ROC/TFT/config'
```

---

### Post by delsdog on 2006-04-07
Is this resolved? 
I'm running Dapper and was thinking of getting Cedega to run CivIV, but if it doesn't work then I won't bother.

---

### Post by Zer0d on 2006-04-07
It's all working now :) Without preformance problems in some games ;)

---

### Post by matko on 2006-07-13
hello. 
easiest way is to install xlibs. here is one 
> [http://www.inverseflux.com/index.php?/archives/42-Cedega-and-Ubuntu-Dapper-Drake-xlibs-Issuerepost.html](http://www.inverseflux.com/index.php?/archives/42-Cedega-and-Ubuntu-Dapper-Drake-xlibs-Issuerepost.html)

that is **not** in conflict with other packages.
enjoy

---

### Post by InverseFlux on 2006-08-13
I ran into the same issue, found the xlibs on another blog and reposted them.  Worked for me.  :o

---

