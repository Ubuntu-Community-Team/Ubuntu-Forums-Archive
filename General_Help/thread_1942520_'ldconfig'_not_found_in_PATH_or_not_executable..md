---
title: "'ldconfig' not found in PATH or not executable."
date: 2012-03-17
forum: General Help
---

### Post by jeremymiles on 2012-03-17
Hello,

I've just installed Ubuntu as a dual boot, and done nothing except tried to download and install Chrome (which failed).

I get an error warning that there are unmet dependencies, so I run:

sudo apt-get -f install

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libc-bin libc6
Suggested packages:
  glibc-doc
The following NEW packages will be installed:
  libc-bin
The following packages will be upgraded:
  libc6
1 upgraded, 1 newly installed, 0 to remove and 367 not upgraded.
2 not fully installed or removed.
Need to get 0 B/5,143 kB of archives.
After this operation, 3,432 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Can't exec "locale": No such file or directory at /usr/share/perl5/Debconf/Encoding.pm line 16.
Use of uninitialized value $Debconf::Encoding::charmap in scalar chomp at /usr/share/perl5/Debconf/Encoding.pm line 17.
Preconfiguring packages ...
dpkg: warning: 'ldconfig' not found in PATH or not executable.
dpkg: error: 1 expected program not found in PATH or not executable.
Note: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.
E: Sub-process /usr/bin/dpkg returned an error code (2)
jeremy@ubuntu:/etc$ ^C
jeremy@ubuntu:/etc$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libc-bin libc6
Suggested packages:
  glibc-doc
The following NEW packages will be installed:
  libc-bin
The following packages will be upgraded:
  libc6
1 upgraded, 1 newly installed, 0 to remove and 367 not upgraded.
2 not fully installed or removed.
Need to get 0 B/5,143 kB of archives.
After this operation, 3,432 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Can't exec "locale": No such file or directory at /usr/share/perl5/Debconf/Encoding.pm line 16.
Use of uninitialized value $Debconf::Encoding::charmap in scalar chomp at /usr/share/perl5/Debconf/Encoding.pm line 17.
Preconfiguring packages ...
**dpkg: warning: 'ldconfig' not found in PATH or not executable.**
dpkg: error: 1 expected program not found in PATH or not executable.
Note: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.
E: Sub-process /usr/bin/dpkg returned an error code (2)

Googling around a bit, I try to change the root path, 

So I run:

sudo visudo

But this contains:

Defaults        env_reset

Defaults        secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"

Which is what it should contain.  

Any ideas how to fix this?

Can I just delete Ubuntu and try again?  (As I haven't actually done anything).

Thanks!

Jeremy

---

### Post by matt_symes on 2012-03-17
Hi

This is the third time someone has posted this problem this week that i have seen.

Is this really a problem with the path ?

Open a terminal and type

```
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin sudo apt-get -f install
```What does that return ?

Kind regards

---

### Post by albertz on 2012-07-21
I have the same think here on a Debian after a dist-upgrade.

Your command without the env throws the error - with the env, it outputs nothing, i.e. it seems to work. It seems ldconfig is in /sbin and this is not in my PATH by default for some reason.

Edit: Further stuff still failed, e.g.:
```
az@albert:~$ sudo dpkg --configure -a 
Setting up initramfs-tools (0.107) ...
/var/lib/dpkg/info/initramfs-tools.postinst: 12: /var/lib/dpkg/info/initramfs-tools.postinst: update-initramfs: not found
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 127
Setting up printer-driver-gutenprint (5.2.9-1) ...
/var/lib/dpkg/info/printer-driver-gutenprint.postinst: 30: /var/lib/dpkg/info/printer-driver-gutenprint.postinst: cups-genppdupdate: not found
dpkg: error processing printer-driver-gutenprint (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 initramfs-tools
 printer-driver-gutenprint

```

It turns out that also /usr/sbin was missing in PATH. After adding that, this worked now.

Edit: I am still getting errors on apt-get upgrade with fontconfig:
```
az@albert:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  cpp g++ gcc libblas3gf liblapack3gf libsdl1.2-dev libsdl1.2debian nmap
The following packages will be upgraded:
  fontconfig
1 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
Need to get 0 B/347 kB of archives.
After this operation, 82.9 kB of additional disk space will be used.
Do you want to continue [Y/n]? 
(Reading database ... 68208 files and directories currently installed.)
Preparing to replace fontconfig 2.6.0-3 (using .../fontconfig_2.9.0-6_i386.deb) ...
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
dpkg: error processing /var/cache/apt/archives/fontconfig_2.9.0-6_i386.deb (--unpack):
 there is no script in the new version of the package - giving up
Errors were encountered while processing:
 /var/cache/apt/archives/fontconfig_2.9.0-6_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I was trying to reinstall fontconfig but getting errors. Even just removing fontconfig:
```


az@albert:~$ sudo apt-get remove fontconfig  -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  hicolor-icon-theme libatk1.0-0 libatk1.0-data libfontenc1 libgconf2-4
  libgtk2.0-common libnss3-1d libstartup-notification0 libthai-data libthai0
  libxaw7 libxcomposite1 libxcursor1 libxft2 libxinerama1 libxmu6 libxrandr2
  libxss1 libxv1 libxxf86dga1 x11-utils x11-xserver-utils xdg-utils
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  fontconfig
0 upgraded, 0 newly installed, 1 to remove and 8 not upgraded.
After this operation, 393 kB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 68026 files and directories currently installed.)
Removing fontconfig ...
dpkg: error processing fontconfig (--remove):
 subprocess installed pre-removal script returned error exit status 1
Errors were encountered while processing:
 fontconfig
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Still problems while removing fontconfig:
```


az@albert:~$ sudo dpkg -D2 --force-all -r fontconfig 
(Reading database ... 68026 files and directories currently installed.)
Removing fontconfig ...
D000002: fork/exec /var/lib/dpkg/info/fontconfig.prerm ( remove )
dpkg: error processing fontconfig (--remove):
 subprocess installed pre-removal script returned error exit status 1
D000002: fork/exec /var/lib/dpkg/info/fontconfig.postinst ( abort-remove )
Errors were encountered while processing:
 fontconfig

```

In /var/lib/dpkg/info/fontconfig.prerm (which is quite small/easy), there is:
```

case "$1" in
        upgrade)
                test -x /usr/bin/defoma-app && \
                        /usr/bin/defoma-app clean fontconfig
                ;;
        remove)
                test -x /usr/bin/defoma-app && \
                       /usr/bin/defoma-app purge fontconfig
                ;;
esac

```

I don't have /usr/bin/defoma-app. Not sure why and why I need that. However, that seems to be the reason why it fails. I just commented that stuff out. Now the removing of fontconfig finally did work.

Everything seems to work now so far.

---

### Post by fwolf on 2012-08-05
Check below 2 lines in /etc/sudoers :

```

Defaults    env_reset
Defaults    secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"

```

This should fix your 'apt' problem.

---

### Post by zenolijo on 2013-02-16
For me, using su instead of sudo fixed the problem :)

This happened for me when updating from Debian Squeezy to Sid

---

