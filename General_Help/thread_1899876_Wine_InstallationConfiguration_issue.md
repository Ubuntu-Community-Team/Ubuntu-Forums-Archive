---
title: "Wine Installation/Configuration issue"
date: 2011-12-24
forum: General Help
---

### Post by cuberts on 2011-12-24
I do use windows some of the time, and I often used Notepad ++ for web designing on windows, like a lot of people. For other software, I always found an Installation for Linux, or  I just found an alternative. However, I am not all that familiar with Emacs or VIM at the moment, so I just decided to go ahead and install Wine, easy solution. However, during the installation/configuration, I have come upon some issues. 

```
 * Starting the Winbind daemon winbind                                   [ OK ] 
dpkg: dependency problems prevent configuration of wine:
 wine depends on wine1.2; however:
  Package wine1.2 is not configured yet.
dpkg: error processing wine (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 python2.7-minimal
 python2.7
 libpython2.7
 libasound2
 wine1.2
 wine
E: Sub-process /usr/bin/dpkg returned an error code (1)
taiga@taiga-desktop:~$ ^C
taiga@taiga-desktop:~$ All done, no errors.
All: command not found
taiga@taiga-desktop:~$ verdan32.exe: OK
verdan32.exe:: command not found
taiga@taiga-desktop:~$ Extracting cabinet: verdan32.exe
Extracting: command not found
taiga@taiga-desktop:~$   extracting fontinst.exe
extracting: command not found
taiga@taiga-desktop:~$   extracting fontinst.inf
extracting: command not found
taiga@taiga-desktop:~$   extracting Verdanab.TTF
extracting: command not found
taiga@taiga-desktop:~$   extracting Verdanai.TTF
extracting: command not found
taiga@taiga-desktop:~$   extracting Verdanaz.TTF
extracting: command not found
taiga@taiga-desktop:~$   extracting Verdana.TTF
extracting: command not found
taiga@taiga-desktop:~$ 
taiga@taiga-desktop:~$ All done, no errors.
All: command not found
taiga@taiga-desktop:~$ webdin32.exe: OK
webdin32.exe:: command not found
taiga@taiga-desktop:~$ Extracting cabinet: webdin32.exe
Extracting: command not found
taiga@taiga-desktop:~$   extracting fontinst.exe
extracting: command not found
taiga@taiga-desktop:~$   extracting Webdings.TTF
extracting: command not found
taiga@taiga-desktop:~$   extracting fontinst.inf
extracting: command not found
taiga@taiga-desktop:~$   extracting Licen.TXT
extracting: command not found
taiga@taiga-desktop:~$ 
taiga@taiga-desktop:~$ All done, no errors.
All: command not found
taiga@taiga-desktop:~$ All fonts downloaded and installed.
All: command not found
taiga@taiga-desktop:~$ W: libwmf0.2-7 is already removed. It is recommended to run defoma-app purge libwmf0.2-7.
W:: command not found
taiga@taiga-desktop:~$ W: gs is already removed. It is recommended to run defoma-app purge gs.
W:: command not found
taiga@taiga-desktop:~$ Updating fontconfig cache for /usr/share/fonts/truetype/msttcorefonts
Updating: command not found
taiga@taiga-desktop:~$ Setting up ttf-umefont (422-1) ...
bash: syntax error near unexpected token `('
taiga@taiga-desktop:~$ Setting up unrar (1:4.0.3-1) ...
bash: syntax error near unexpected token `('
taiga@taiga-desktop:~$ update-alternatives: using /usr/bin/unrar-nonfree to provide /usr/bin/unrar (unrar) in auto mode.
bash: syntax error near unexpected token `('
taiga@taiga-desktop:~$ Setting up winbind (2:3.5.8~dfsg-1ubuntu2.3) ...
bash: syntax error near unexpected token `('
taiga@taiga-desktop:~$  * Starting the Winbind daemon winbind                                   [ OK ] 
Desktop: command not found
taiga@taiga-desktop:~$ dpkg: dependency problems prevent configuration of wine:
No command 'dpkg:' found, did you mean:
 Command 'dpkg' from package 'dpkg' (main)
dpkg:: command not found
taiga@taiga-desktop:~$  wine depends on wine1.2; however:
wine: created the configuration directory '/home/taiga/.wine'
fixme:system:SetProcessDPIAware stub!
fixme:dwmapi:DwmIsCompositionEnabled 0x33d04c
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:advapi:SetNamedSecurityInfoW L"C:\\windows\\system32\\gecko\\1.0.0\\wine_gecko\\components\\xpti.dat" 1 536870916 (nil) (nil) 0x21ff5c (nil)
fixme:iphlpapi:NotifyAddrChange (Handle 0xa73e8d8, overlapped 0xa73e8e0): stub
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:advapi:SetNamedSecurityInfoW L"C:\\windows\\system32\\gecko\\1.0.0\\wine_gecko\\components\\compreg.dat" 1 536870916 (nil) (nil) 0x1e1debc (nil)
wine: configuration in '/home/taiga/.wine' has been updated.
wine: cannot find L"C:\\windows\\system32\\depends.exe"
however:: command not found
taiga@taiga-desktop:~$   Package wine1.2 is not configured yet.
No command 'Package' found, did you mean:
 Command 'package' from package 'mailagent' (universe)
Package: command not found
taiga@taiga-desktop:~$ dpkg: error processing wine (--configure):
bash: syntax error near unexpected token `('
taiga@taiga-desktop:~$  dependency problems - leaving unconfigured
dependency: command not found
taiga@taiga-desktop:~$ No apport report written because MaxReports is reached already
No: command not found
taiga@taiga-desktop:~$                                                               Processing triggers for libc-bin ...
Processing: command not found
taiga@taiga-desktop:~$ ldconfig deferred processing now taking place
/sbin/ldconfig.real: relative path `deferred' used to build cache
taiga@taiga-desktop:~$ Errors were encountered while processing:
Errors: command not found
taiga@taiga-desktop:~$  python2.7-minimal
python2.7-minimal: command not found
taiga@taiga-desktop:~$  python2.7
Python 2.7.1+ (r271:86832, Apr 11 2011, 18:05:24) 
[GCC 4.5.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>>  libpython2.7
  File "<stdin>", line 1
    libpython2.7
    ^
IndentationError: unexpected indent
>>>  libasound2
  File "<stdin>", line 1
    libasound2
    ^
IndentationError: unexpected indent
>>>  wine1.2
  File "<stdin>", line 1
    wine1.2
    ^
IndentationError: unexpected indent
>>>  wine
  File "<stdin>", line 1
    wine
    ^
IndentationError: unexpected indent
>>> 

```

I really have no idea what the issue is, I'm assuming that Wine has remained un-configured. Please help.

---

### Post by Karlchen on 2011-12-24
Hello, cuberts.

Which Ubuntu version are you using exactly?
Which software did you use to download and install Wine?

The screen output that you posted might suggest you downloaded some Wine package, put it in your desktop folder and tried to install it from your normal user account.

On Ubuntu 10.04 Desktop 32-bit as well as on Ubuntu 11.10 Desktop 32-bit I have used Synaptic. I requires privilege elevation, i.e. it runs as root and asks for _your_ password, not root's password.
Inside Synaptic I have selected the **Wine 1.2** package for installation, confirmed to select any dependent packages as well and selected to apply my selection(s).
On Ubuntu 10.04 Desktop 32-bit as well as on Ubuntu 11.10 Desktop 32-bit Synaptic has installed and configured Wine 1.2.3 without any problems.

Kind regards,
Karl

---

