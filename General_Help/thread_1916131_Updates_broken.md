---
title: "Updates broken"
date: 2012-01-27
forum: General Help
---

### Post by kooldino on 2012-01-27
I went to do an update via the GUI recently.  It hung at around 60%, so I killed it.

When I try to do it via the command line, it fails.

When I try to do a dpkg-reconfigure, THAT fails as well:

```
$ sudo dpkg-reconfigure
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.12.4 /usr/local/share/perl/5.12.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.12 /usr/share/perl/5.12 /usr/local/lib/site_perl .) at /usr/sbin/dpkg-reconfigure line 8.
BEGIN failed--compilation aborted at /usr/sbin/dpkg-reconfigure line 8.


```

What now?

---

### Post by raja.genupula on 2012-01-27
```
sudo apt-get update
sudo apt-get upgrade

```

give that info here.:D

---

### Post by kooldino on 2012-01-30
> **raja.genupula said:**
> ```
sudo apt-get update
sudo apt-get upgrade

```

give that info here.:D

Update works fine.

```

$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 kdm : Depends: libkworkspace4 (= 4:4.7.3a-0ubuntu0.1) but 4:4.7.4-0ubuntu0.1 is installed
       Depends: kde-workspace-kgreet-plugins (= 4:4.7.3a-0ubuntu0.1) but 4:4.7.4-0ubuntu0.1 is installed
 xorg : Depends: xserver-xorg (>= 1:7.6+7ubuntu7.1) but 1:7.6+7ubuntu7 is installed
E: Unmet dependencies. Try using -f.

```

```

$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  kdm linux-image-3.0.0-15-generic okular okular-extra-backends xserver-xorg
Suggested packages:
  fdutils linux-doc-3.0.0 linux-source-3.0.0 linux-tools jovie okular-odp-backend poppler-data texlive-binaries unrar
The following packages will be upgraded:
  kdm linux-image-3.0.0-15-generic okular okular-extra-backends xserver-xorg
5 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
240 not fully installed or removed.
Need to get 0 B/38.5 MB of archives.
After this operation, 117 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
debconf: Perl may be unconfigured (Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.12.4 /usr/local/share/perl/5.12.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.12 /usr/share/perl/5.12 /usr/local/lib/site_perl .) at (eval 1) line 2.
BEGIN failed--compilation aborted at (eval 1) line 2.
) -- aborting
(Reading database ... 
dpkg: warning: files list file for package `linux-image-3.0.0-15-generic' missing, assuming package has no files currently installed.
(Reading database ... 176936 files and directories currently installed.)
Preparing to replace linux-image-3.0.0-15-generic 3.0.0-15.26 (using .../linux-image-3.0.0-15-generic_3.0.0-15.26_i386.deb) ...
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.12.4 /usr/local/share/perl/5.12.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.12 /usr/share/perl/5.12 /usr/local/lib/site_perl .) at /usr/share/perl5/Debconf/Client/ConfModule.pm line 42.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Client/ConfModule.pm line 42.
Compilation failed in require at /var/lib/dpkg/tmp.ci/preinst line 20.
BEGIN failed--compilation aborted at /var/lib/dpkg/tmp.ci/preinst line 20.
dpkg: error processing /var/cache/apt/archives/linux-image-3.0.0-15-generic_3.0.0-15.26_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 2
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.12.4 /usr/local/share/perl/5.12.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.12 /usr/share/perl/5.12 /usr/local/lib/site_perl .) at /usr/lib/perl/5.12/Cwd.pm line 3.
BEGIN failed--compilation aborted at /usr/lib/perl/5.12/Cwd.pm line 3.
Compilation failed in require at /var/lib/dpkg/tmp.ci/postrm line 21.
BEGIN failed--compilation aborted at /var/lib/dpkg/tmp.ci/postrm line 21.
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 2
Preparing to replace kdm 4:4.7.3a-0ubuntu0.1 (using .../kdm_4%3a4.7.4-0ubuntu0.1_i386.deb) ...
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.12.4 /usr/local/share/perl/5.12.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.12 /usr/share/perl/5.12 /usr/local/lib/site_perl .) at /usr/share/debconf/frontend line 5.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 5.
dpkg: warning: subprocess old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.12.4 /usr/local/share/perl/5.12.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.12 /usr/share/perl/5.12 /usr/local/lib/site_perl .) at /usr/share/debconf/frontend line 5.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 5.
dpkg: error processing /var/cache/apt/archives/kdm_4%3a4.7.4-0ubuntu0.1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 2
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.12.4 /usr/local/share/perl/5.12.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.12 /usr/share/perl/5.12 /usr/local/lib/site_perl .) at /usr/share/debconf/frontend line 5.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 5.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Preparing to replace xserver-xorg 1:7.6+7ubuntu7 (using .../xserver-xorg_1%3a7.6+7ubuntu7.1_i386.deb) ...
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.12.4 /usr/local/share/perl/5.12.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.12 /usr/share/perl/5.12 /usr/local/lib/site_perl .) at /usr/share/debconf/frontend line 5.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 5.
dpkg: warning: subprocess old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.12.4 /usr/local/share/perl/5.12.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.12 /usr/share/perl/5.12 /usr/local/lib/site_perl .) at /usr/share/debconf/frontend line 5.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 5.
dpkg: error processing /var/cache/apt/archives/xserver-xorg_1%3a7.6+7ubuntu7.1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 2
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.12.4 /usr/local/share/perl/5.12.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.12 /usr/share/perl/5.12 /usr/local/lib/site_perl .) at /usr/share/debconf/frontend line 5.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 5.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Preparing to replace okular 4:4.7.3-0ubuntu0.1 (using .../okular_4%3a4.7.4-0ubuntu0.1_i386.deb) ...
Unpacking replacement okular ...
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.12.4 /usr/local/share/perl/5.12.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.12 /usr/share/perl/5.12 /usr/local/lib/site_perl .) at /usr/lib/perl/5.12/File/Glob.pm line 3.
BEGIN failed--compilation aborted at /usr/lib/perl/5.12/File/Glob.pm line 3.
Compilation failed in require at /usr/sbin/update-mime line 64.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 64.
dpkg: warning: subprocess old post-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.12.4 /usr/local/share/perl/5.12.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.12 /usr/share/perl/5.12 /usr/local/lib/site_perl .) at /usr/lib/perl/5.12/File/Glob.pm line 3.
BEGIN failed--compilation aborted at /usr/lib/perl/5.12/File/Glob.pm line 3.
Compilation failed in require at /usr/sbin/update-mime line 64.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 64.
dpkg: error processing /var/cache/apt/archives/okular_4%3a4.7.4-0ubuntu0.1_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.12.4 /usr/local/share/perl/5.12.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.12 /usr/share/perl/5.12 /usr/local/lib/site_perl .) at /usr/lib/perl/5.12/File/Glob.pm line 3.
BEGIN failed--compilation aborted at /usr/lib/perl/5.12/File/Glob.pm line 3.
Compilation failed in require at /usr/sbin/update-mime line 64.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 64.
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 2
Preparing to replace okular-extra-backends 4:4.7.3-0ubuntu0.1 (using .../okular-extra-backends_4%3a4.7.4-0ubuntu0.1_i386.deb) ...
Unpacking replacement okular-extra-backends ...
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.12.4 /usr/local/share/perl/5.12.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.12 /usr/share/perl/5.12 /usr/local/lib/site_perl .) at /usr/lib/perl/5.12/File/Glob.pm line 3.
BEGIN failed--compilation aborted at /usr/lib/perl/5.12/File/Glob.pm line 3.
Compilation failed in require at /usr/sbin/update-mime line 64.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 64.
dpkg: warning: subprocess old post-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.12.4 /usr/local/share/perl/5.12.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.12 /usr/share/perl/5.12 /usr/local/lib/site_perl .) at /usr/lib/perl/5.12/File/Glob.pm line 3.
BEGIN failed--compilation aborted at /usr/lib/perl/5.12/File/Glob.pm line 3.
Compilation failed in require at /usr/sbin/update-mime line 64.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 64.
dpkg: error processing /var/cache/apt/archives/okular-extra-backends_4%3a4.7.4-0ubuntu0.1_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.12.4 /usr/local/share/perl/5.12.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.12 /usr/share/perl/5.12 /usr/local/lib/site_perl .) at /usr/lib/perl/5.12/File/Glob.pm line 3.
BEGIN failed--compilation aborted at /usr/lib/perl/5.12/File/Glob.pm line 3.
Compilation failed in require at /usr/sbin/update-mime line 64.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 64.
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 2
Processing triggers for hicolor-icon-theme ...
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.0.0-15-generic_3.0.0-15.26_i386.deb
 /var/cache/apt/archives/kdm_4%3a4.7.4-0ubuntu0.1_i386.deb
 /var/cache/apt/archives/xserver-xorg_1%3a7.6+7ubuntu7.1_i386.deb
 /var/cache/apt/archives/okular_4%3a4.7.4-0ubuntu0.1_i386.deb
 /var/cache/apt/archives/okular-extra-backends_4%3a4.7.4-0ubuntu0.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by kooldino on 2012-01-31
Bump

---

### Post by raja.genupula on 2012-01-31
hi man 

sudo apt-get clean
sudo apt-get install -f

execute them one by one .

---

### Post by kooldino on 2012-02-09
> **raja.genupula said:**
> hi man 

sudo apt-get clean
sudo apt-get install -f

execute them one by one .

The clean worked fine.  OTOH...

```
$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  kdm linux-image-3.0.0-15-generic okular okular-extra-backends xserver-xorg
Suggested packages:
  fdutils linux-doc-3.0.0 linux-source-3.0.0 linux-tools jovie okular-odp-backend poppler-data texlive-binaries unrar
The following packages will be upgraded:
  kdm linux-image-3.0.0-15-generic okular okular-extra-backends xserver-xorg
5 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.
246 not fully installed or removed.
Need to get 38.5 MB of archives.
After this operation, 117 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://us.archive.ubuntu.com/ubuntu/ oneiric-updates/main linux-image-3.0.0-15-generic i386 3.0.0-15.26 [36.5 MB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ oneiric-updates/main kdm i386 4:4.7.4-0ubuntu0.1 [879 kB]                                                                
Get:3 http://us.archive.ubuntu.com/ubuntu/ oneiric-updates/main xserver-xorg i386 1:7.6+7ubuntu7.1 [78.9 kB]                                                        
Get:4 http://us.archive.ubuntu.com/ubuntu/ oneiric-updates/main okular i386 4:4.7.4-0ubuntu0.1 [998 kB]                                                             
Get:5 http://us.archive.ubuntu.com/ubuntu/ oneiric-updates/main okular-extra-backends i386 4:4.7.4-0ubuntu0.1 [51.9 kB]                                             
Fetched 38.5 MB in 6min 36s (97.2 kB/s)                                                                                                                             
debconf: Perl may be unconfigured (Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.12.4 /usr/local/share/perl/5.12.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.12 /usr/share/perl/5.12 /usr/local/lib/site_perl .) at (eval 1) line 2.
BEGIN failed--compilation aborted at (eval 1) line 2.
) -- aborting
(Reading database ... 
dpkg: warning: files list file for package `linux-image-3.0.0-15-generic' missing, assuming package has no files currently installed.
(Reading database ... 176936 files and directories currently installed.)
Preparing to replace linux-image-3.0.0-15-generic 3.0.0-15.26 (using .../linux-image-3.0.0-15-generic_3.0.0-15.26_i386.deb) ...
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.12.4 /usr/local/share/perl/5.12.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.12 /usr/share/perl/5.12 /usr/local/lib/site_perl .) at /usr/share/perl5/Debconf/Client/ConfModule.pm line 42.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Client/ConfModule.pm line 42.
Compilation failed in require at /var/lib/dpkg/tmp.ci/preinst line 20.
BEGIN failed--compilation aborted at /var/lib/dpkg/tmp.ci/preinst line 20.
dpkg: error processing /var/cache/apt/archives/linux-image-3.0.0-15-generic_3.0.0-15.26_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 2
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.12.4 /usr/local/share/perl/5.12.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.12 /usr/share/perl/5.12 /usr/local/lib/site_perl .) at /usr/lib/perl/5.12/Cwd.pm line 3.
BEGIN failed--compilation aborted at /usr/lib/perl/5.12/Cwd.pm line 3.
Compilation failed in require at /var/lib/dpkg/tmp.ci/postrm line 21.
BEGIN failed--compilation aborted at /var/lib/dpkg/tmp.ci/postrm line 21.
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 2
Preparing to replace kdm 4:4.7.3a-0ubuntu0.1 (using .../kdm_4%3a4.7.4-0ubuntu0.1_i386.deb) ...
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.12.4 /usr/local/share/perl/5.12.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.12 /usr/share/perl/5.12 /usr/local/lib/site_perl .) at /usr/share/debconf/frontend line 5.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 5.
dpkg: warning: subprocess old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.12.4 /usr/local/share/perl/5.12.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.12 /usr/share/perl/5.12 /usr/local/lib/site_perl .) at /usr/share/debconf/frontend line 5.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 5.
dpkg: error processing /var/cache/apt/archives/kdm_4%3a4.7.4-0ubuntu0.1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 2
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.12.4 /usr/local/share/perl/5.12.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.12 /usr/share/perl/5.12 /usr/local/lib/site_perl .) at /usr/share/debconf/frontend line 5.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 5.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Preparing to replace xserver-xorg 1:7.6+7ubuntu7 (using .../xserver-xorg_1%3a7.6+7ubuntu7.1_i386.deb) ...
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.12.4 /usr/local/share/perl/5.12.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.12 /usr/share/perl/5.12 /usr/local/lib/site_perl .) at /usr/share/debconf/frontend line 5.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 5.
dpkg: warning: subprocess old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.12.4 /usr/local/share/perl/5.12.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.12 /usr/share/perl/5.12 /usr/local/lib/site_perl .) at /usr/share/debconf/frontend line 5.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 5.
dpkg: error processing /var/cache/apt/archives/xserver-xorg_1%3a7.6+7ubuntu7.1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 2
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.12.4 /usr/local/share/perl/5.12.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.12 /usr/share/perl/5.12 /usr/local/lib/site_perl .) at /usr/share/debconf/frontend line 5.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 5.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Preparing to replace okular 4:4.7.3-0ubuntu0.1 (using .../okular_4%3a4.7.4-0ubuntu0.1_i386.deb) ...
Unpacking replacement okular ...
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.12.4 /usr/local/share/perl/5.12.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.12 /usr/share/perl/5.12 /usr/local/lib/site_perl .) at /usr/lib/perl/5.12/File/Glob.pm line 3.
BEGIN failed--compilation aborted at /usr/lib/perl/5.12/File/Glob.pm line 3.
Compilation failed in require at /usr/sbin/update-mime line 64.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 64.
dpkg: warning: subprocess old post-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.12.4 /usr/local/share/perl/5.12.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.12 /usr/share/perl/5.12 /usr/local/lib/site_perl .) at /usr/lib/perl/5.12/File/Glob.pm line 3.
BEGIN failed--compilation aborted at /usr/lib/perl/5.12/File/Glob.pm line 3.
Compilation failed in require at /usr/sbin/update-mime line 64.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 64.
dpkg: error processing /var/cache/apt/archives/okular_4%3a4.7.4-0ubuntu0.1_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.12.4 /usr/local/share/perl/5.12.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.12 /usr/share/perl/5.12 /usr/local/lib/site_perl .) at /usr/lib/perl/5.12/File/Glob.pm line 3.
BEGIN failed--compilation aborted at /usr/lib/perl/5.12/File/Glob.pm line 3.
Compilation failed in require at /usr/sbin/update-mime line 64.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 64.
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 2
Preparing to replace okular-extra-backends 4:4.7.3-0ubuntu0.1 (using .../okular-extra-backends_4%3a4.7.4-0ubuntu0.1_i386.deb) ...
Unpacking replacement okular-extra-backends ...
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.12.4 /usr/local/share/perl/5.12.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.12 /usr/share/perl/5.12 /usr/local/lib/site_perl .) at /usr/lib/perl/5.12/File/Glob.pm line 3.
BEGIN failed--compilation aborted at /usr/lib/perl/5.12/File/Glob.pm line 3.
Compilation failed in require at /usr/sbin/update-mime line 64.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 64.
dpkg: warning: subprocess old post-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.12.4 /usr/local/share/perl/5.12.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.12 /usr/share/perl/5.12 /usr/local/lib/site_perl .) at /usr/lib/perl/5.12/File/Glob.pm line 3.
BEGIN failed--compilation aborted at /usr/lib/perl/5.12/File/Glob.pm line 3.
Compilation failed in require at /usr/sbin/update-mime line 64.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 64.
dpkg: error processing /var/cache/apt/archives/okular-extra-backends_4%3a4.7.4-0ubuntu0.1_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.12.4 /usr/local/share/perl/5.12.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.12 /usr/share/perl/5.12 /usr/local/lib/site_perl .) at /usr/lib/perl/5.12/File/Glob.pm line 3.
BEGIN failed--compilation aborted at /usr/lib/perl/5.12/File/Glob.pm line 3.
Compilation failed in require at /usr/sbin/update-mime line 64.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 64.
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 2
Processing triggers for hicolor-icon-theme ...
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.0.0-15-generic_3.0.0-15.26_i386.deb
 /var/cache/apt/archives/kdm_4%3a4.7.4-0ubuntu0.1_i386.deb
 /var/cache/apt/archives/xserver-xorg_1%3a7.6+7ubuntu7.1_i386.deb
 /var/cache/apt/archives/okular_4%3a4.7.4-0ubuntu0.1_i386.deb
 /var/cache/apt/archives/okular-extra-backends_4%3a4.7.4-0ubuntu0.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by raja.genupula on 2012-02-09
```
sudo dpkg --configure -a
```
then ty again 

if this not sort things then 
```
sudo rm -rf /var/cache/apt/*
sudo apt-get update
```

let us know what you got 
all the best man

---

### Post by kooldino on 2012-02-09
> **raja.genupula said:**
> ```
sudo dpkg --configure -a
```
then ty again 

The dpkg command failed.

[QUOTE]if this not sort things then 
```
sudo rm -rf /var/cache/apt/*
sudo apt-get update
```

That worked, but I still get an error when I try to do anything else.

---

### Post by drmrgd on 2012-02-09
A bit of a new problem for me.  The first thing that jumps out at me is that something is hosed with your Perl installation.  Strict.pm should be easily found in the paths where it's looking.  Not sure why that's hanging it, though. A super quick a dirty thing to try is a simple reboot to make sure nothings gumming up the process from the failed upgrade previously. 

Then I would (just for kicks) run:

```
sudo updatedb
``` 

and when it completes run:

```
locate strict.pm
```

For me it's located here:  /usr/share/perl/5.12.4/strict.pm (I noticed that /usr/share/perl/5.12/ is a symbolic link to /usr/share/perl/5.12.4/). You can verify the path by:

```
env -i perl -V
``` 

and at the end you should see a list of paths in the @INC variable.  

Until someone with a little more dpkg knowledge comes along, that might be a good place to start.  I think Perl is unable to process the packages due to it having a hard time with the environment variable path.

---

### Post by raja.genupula on 2012-02-09
> **kooldino said:**
> The dpkg command failed.

[QUOTE]if this not sort things then 
```
sudo rm -rf /var/cache/apt/*
sudo apt-get update
```

That worked, but I still get an error when I try to do anything else.

```
sudo dpkg --configure -a
sudo apt-get install -f

```

if things are fine ok else do this 

```
sudo apt-get remove -f
```

please post the output of terminal , that can help us.

---

### Post by kooldino on 2012-02-10
```
locate strict.pm
```


```
kubby:/usr/share/perl$ ls -alh
total 8.0K
drwxr-xr-x   2 root root 4.0K 2011-10-12 11:08 .
drwxr-xr-x 188 root root 4.0K 2012-01-26 15:08 ..
lrwxrwxrwx   1 root root    6 2011-12-09 16:38 5.12 -> 5.12.4
kubby:/usr/share/perl$ cd 5.12
bash: cd: 5.12: No such file or directory

```

Ruh Roh.

```
env -i perl -V
``` 

and at the end you should see a list of paths in the @INC variable.  

Until someone with a little more dpkg knowledge comes along, that might be a good place to start.  I think Perl is unable to process the packages due to it having a hard time with the environment variable path.[/QUOTE]

[QUOTE]kubby:/usr/share/perl$ env -i perl -V
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.12.4 /usr/local/share/perl/5.12.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.12 /usr/share/perl/5.12 /usr/local/lib/site_perl .) at /usr/lib/perl/5.12/Config.pm line 9.
BEGIN failed--compilation aborted at /usr/lib/perl/5.12/Config.pm line 9.
Compilation failed in require.
BEGIN failed--compilation aborted.

---

### Post by kooldino on 2012-02-10
> **raja.genupula said:**
> [QUOTE=kooldino;11676343]The dpkg command failed.



```
sudo dpkg --configure -a
sudo apt-get install -f

```

if things are fine ok else do this 

```
sudo apt-get remove -f
```

please post the output of terminal , that can help us.


sudo dpkg --configure -a fails every time.

---

### Post by raja.genupula on 2012-02-10
hi please man , for next steps i need output of terminal , it fails or success ,i need terminal output .


cheers

raja

---

### Post by drmrgd on 2012-02-10
> **kooldino said:**
> ```
locate strict.pm
```


```
kubby:/usr/share/perl$ ls -alh
total 8.0K
drwxr-xr-x   2 root root 4.0K 2011-10-12 11:08 .
drwxr-xr-x 188 root root 4.0K 2012-01-26 15:08 ..
lrwxrwxrwx   1 root root    6 2011-12-09 16:38 5.12 -> 5.12.4
kubby:/usr/share/perl$ cd 5.12
bash: cd: 5.12: No such file or directory

```

Ruh Roh.

```
env -i perl -V
``` 

and at the end you should see a list of paths in the @INC variable.  

Until someone with a little more dpkg knowledge comes along, that might be a good place to start.  I think Perl is unable to process the packages due to it having a hard time with the environment variable path.

> kubby:/usr/share/perl$ env -i perl -V
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.12.4 /usr/local/share/perl/5.12.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.12 /usr/share/perl/5.12 /usr/local/lib/site_perl .) at /usr/lib/perl/5.12/Config.pm line 9.
BEGIN failed--compilation aborted at /usr/lib/perl/5.12/Config.pm line 9.
Compilation failed in require.
BEGIN failed--compilation aborted.

Your output at the end got a little messy and I got a little lost.  It looks like the symbolic link to 5.12.4 is hosed, though (or at least you can't seem to be able to use it).  Is the link colored red to indicate it's broken?  Also, can you manually get into the 5.12.4 directory?  I'm going to assume it's a not to that question, since (at least for me), the 5.12.4 directory is in the same place as the symbolic link from 5.12.  

Also, I just want to confirm, the result of locate strict.pm resulted in no hits, right?  And, you did either reboot or run:

```
sudo updatedb
```

If all of the above are true, I would say your Perl installation is hosed for one reason or another, and you'd have to reinstall.  I'm guessing since the dpkg scripts are running from Perl that you'll have to manually download and compile it.  I'd like someone else with a little more knowledge to confirm that before you spend the time and effort, though.

Oh, and I also forgot to say, if you can find the 5.12.4 package, and strict.pm is still located on the system, then I think it's just a matter of fixing the symbolic link to once again point to that target.

---

### Post by kooldino on 2012-02-10
> **drmrgd said:**
> Your output at the end got a little messy and I got a little lost.  It looks like the symbolic link to 5.12.4 is hosed, though (or at least you can't seem to be able to use it).  Is the link colored red to indicate it's broken?  

Yes, it's red, and I can't use it.

> Also, can you manually get into the 5.12.4 directory?  

Nope, that's why I did an ls -al to show you that it's not even listed there.

> 
Also, I just want to confirm, the result of locate strict.pm resulted in no hits, right?  And, you did either reboot or run:

Correct, no results.

> If all of the above are true, I would say your Perl installation is hosed for one reason or another, and you'd have to reinstall.  

It would be **** poor if I was forced to reinstall. There's gotta be a way to fix this.

> I'm guessing since the dpkg scripts are running from Perl that you'll have to manually download and compile it.  I'd like someone else with a little more knowledge to confirm that before you spend the time and effort, though.

That sounds reasonable.

> Oh, and I also forgot to say, if you can find the 5.12.4 package, and strict.pm is still located on the system, then I think it's just a matter of fixing the symbolic link to once again point to that target.

I did a locate on 5.12.4 and found it in "/usr/share/perl/5.12.4", so I pointed the symbolic link to it.

Still didn't fix the issue, though.

---

### Post by kooldino on 2012-02-10
> **raja.genupula said:**
> hi please man , for next steps i need output of terminal , it fails or success ,i need terminal output .


```
kubby:~$ sudo dpkg --configure -a
Setting up man-db (2.6.0.2-2) ...
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.12.4 /usr/local/share/perl/5.12.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.12 /usr/share/perl/5.12 /usr/local/lib/site_perl .) at /usr/share/debconf/frontend line 5.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 5.
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of xorg:
 xorg depends on xserver-xorg (>= 1:7.6+7ubuntu7.1); however:
  Version of xserver-xorg on system is 1:7.6+7ubuntu7.
dpkg: error processing xorg (--configure):
 dependency problems - leaving unconfigured
dpkg: error processing xserver-xorg (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Setting up x11-common (1:7.6+7ubuntu7) ...
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.12.4 /usr/local/share/perl/5.12.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.12 /usr/share/perl/5.12 /usr/local/lib/site_perl .) at /usr/share/debconf/frontend line 5.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 5.
dpkg: error processing x11-common (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.0.0-15-generic; however:
  Package linux-image-3.0.0-15-generic is not installed.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdm:
 kdm depends on libkworkspace4 (= 4:4.7.3a-0ubuntu0.1); however:
  Version of libkworkspace4 on system is 4:4.7.4-0ubuntu0.1.
 kdm depends on kde-workspace-kgreet-plugins (= 4:4.7.3a-0ubuntu0.1); however:
  Version of kde-workspace-kgreet-plugins on system is 4:4.7.4-0ubuntu0.1.
dpkg: error processing kdm (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.0.0.15.17); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up udev (173-0ubuntu4.1) ...
udev start/running, process 20095
update-initramfs: deferring update (trigger activated)
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.12.4 /usr/local/share/perl/5.12.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.12 /usr/share/perl/5.12 /usr/local/lib/site_perl .) at /usr/sbin/update-rc.d line 6.
BEGIN failed--compilation aborted at /usr/sbin/update-rc.d line 6.
dpkg: error processing udev (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libsolid4:
 libsolid4 depends on udev; however:
  Package udev is not configured yet.
dpkg: error processing libsolid4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkio5:
 libkio5 depends on libsolid4 (= 4:4.7.4-0ubuntu0.1); however:
  Package libsolid4 is not configured yet.
dpkg: error processing libkio5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of plasma-dataengines-workspace:
 plasma-dataengines-workspace depends on libkio5 (>= 4:4.6.80); however:
  Package libkio5 is not configured yet.
 plasma-dataengines-workspace depends on libsolid4 (>= 4:4.6.80); however:
  Package libsolid4 is not configured yet.
dpkg: error processing plasma-dataengines-workspace (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kaddressbook:
 kaddressbook depends on libkio5 (>= 4:4.6); however:
  Package libkio5 is not configured yet.
dpkg: error processing kaddressbook (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libknewstuff2-4:
 libknewstuff2-4 depends on libkio5 (= 4:4.7.4-0ubuntu0.1); however:
  Package libkio5 is not configured yet.
dpkg: error processing libknewstuff2-4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkunitconversion4:
 libkunitconversion4 depends on libsolid4 (= 4:4.7.4-0ubuntu0.1); however:
  Package libsolid4 is not configured yet.
dpkg: error processing libkunitconversion4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkateinterfaces4:
 libkateinterfaces4 depends on libkio5 (>= 4:4.6); however:
  Package libkio5 is not configured yet.
dpkg: error processing libkateinterfaces4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of plasma-desktop:
 plasma-desktop depends on libkio5 (>= 4:4.6.80); however:
  Package libkio5 is not configured yet.
 plasma-desktop depends on libsolid4 (>= 4:4.6.80); however:
  Package libsolid4 is not configured yet.
dpkg: error processing plasma-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkleo4:
 libkleo4 depends on libkio5 (>= 4:4.6); however:
  Package libkio5 is not configured yet.
dpkg: error processing libkleo4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ksystemlog:
 ksystemlog depends on libkio5 (>= 4:4.3.4); however:
  Package libkio5 is not configured yet.
dpkg: error processing ksystemlog (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libakonadi-kde4:
 libakonadi-kde4 depends on libkio5 (>= 4:4.6); however:
  Package libkio5 is not configured yet.
 libakonadi-kde4 depends on libsolid4 (>= 4:4.6); however:
  Package libsolid4 is not configured yet.
dpkg: error processing libakonadi-kde4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libmessagecomposer4:
 libmessagecomposer4 depends on libakonadi-kde4 (>= 4:4.6); however:
  Package libakonadi-kde4 is not configured yet.
 libmessagecomposer4 depends on libkio5 (>= 4:4.6); however:
  Package libkio5 is not configured yet.
 libmessagecomposer4 depends on libkleo4 (= 4:4.7.4+git111222-0ubuntu0.1); however:
  Package libkleo4 is not configured yet.
dpkg: error processing libmessagecomposer4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libknotifyconfig4:
 libknotifyconfig4 depends on libkio5 (= 4:4.7.4-0ubuntu0.1); however:
  Package libkio5 is not configured yet.
dpkg: error processing libknotifyconfig4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kinfocenter:
 kinfocenter depends on libkio5 (>= 4:4.6.80); however:
  Package libkio5 is not configured yet.
 kinfocenter depends on libsolid4 (>= 4:4.6.80); however:
  Package libsolid4 is not configured yet.
dpkg: error processing kinfocenter (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdepim-wizards:
 kdepim-wizards depends on libkio5 (>= 4:4.6); however:
  Package libkio5 is not configured yet.
dpkg: error processing kdepim-wizards (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libincidenceeditorsng4:
 libincidenceeditorsng4 depends on libakonadi-kde4 (>= 4:4.6); however:
  Package libakonadi-kde4 is not configured yet.
 libincidenceeditorsng4 depends on libkio5 (>= 4:4.6); however:
  Package libkio5 is not configured yet.
dpkg: error processing libincidenceeditorsng4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdelibs-bin:
 kdelibs-bin depends on libkio5 (= 4:4.7.4-0ubuntu0.1); however:
  Package libkio5 is not configured yet.
dpkg: error processing kdelibs-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libplasmaclock4abi2:
 libplasmaclock4abi2 depends on libkio5 (>= 4:4.6.80); however:
  Package libkio5 is not configured yet.
dpkg: error processing libplasmaclock4abi2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libknewstuff3-4:
 libknewstuff3-4 depends on libkio5 (= 4:4.7.4-0ubuntu0.1); however:
  Package libkio5 is not configured yet.
dpkg: error processing libknewstuff3-4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkparts4:
 libkparts4 depends on libkio5 (= 4:4.7.4-0ubuntu0.1); however:
  Package libkio5 is not configured yet.
dpkg: error processing libkparts4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdoctools:
 kdoctools depends on libkio5 (= 4:4.7.4-0ubuntu0.1); however:
  Package libkio5 is not configured yet.
dpkg: error processing kdoctools (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of plasma-widget-folderview:
 plasma-widget-folderview depends on libkio5 (>= 4:4.6.90); however:
  Package libkio5 is not configured yet.
 plasma-widget-folderview depends on libsolid4 (>= 4:4.6.90); however:
  Package libsolid4 is not configured yet.
dpkg: error processing plasma-widget-folderview (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ark:
 ark depends on libkio5 (>= 4:4.6); however:
  Package libkio5 is not configured yet.
 ark depends on libkparts4 (>= 4:4.6); however:
  Package libkparts4 is not configured yet.
dpkg: error processing ark (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kmail:
 kmail depends on libakonadi-kde4 (>= 4:4.7.0); however:
  Package libakonadi-kde4 is not configured yet.
 kmail depends on libkio5 (>= 4:4.6); however:
  Package libkio5 is not configured yet.
 kmail depends on libkleo4 (= 4:4.7.4+git111222-0ubuntu0.1); however:
  Package libkleo4 is not configured yet.
 kmail depends on libknotifyconfig4 (>= 4:4.6); however:
  Package libknotifyconfig4 is not configured yet.
 kmail depends on libkparts4 (>= 4:4.6); however:
  Package libkparts4 is not configured yet.
 kmail depends on libmessagecomposer4 (= 4:4.7.4+git111222-0ubuntu0.1); however:
  Package libmessagecomposer4 is not configured yet.
 kmail depends on libsolid4 (>= 4:4.6); however:
  Package libsolid4 is not configured yet.
dpkg: error processing kmail (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libmessagecore4:
 libmessagecore4 depends on libakonadi-kde4 (>= 4:4.6); however:
  Package libakonadi-kde4 is not configured yet.
 libmessagecore4 depends on libkio5 (>= 4:4.6); however:
  Package libkio5 is not configured yet.
dpkg: error processing libmessagecore4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kopete:
 kopete depends on libkio5 (>= 4:4.6.90); however:
  Package libkio5 is not configured yet.
 kopete depends on libknewstuff2-4 (>= 4:4.6.90); however:
  Package libknewstuff2-4 is not configured yet.
 kopete depends on libknotifyconfig4 (>= 4:4.6.90); however:
  Package libknotifyconfig4 is not configured yet.
 kopete depends on libkparts4 (>= 4:4.6.90); however:
  Package libkparts4 is not configured yet.
 kopete depends on libsolid4 (>= 4:4.6.90); however:
  Package libsolid4 is not configured yet.
dpkg: error processing kopete (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdenetwork-filesharing:
 kdenetwork-filesharing depends on libkio5 (>= 4:4.6.90); however:
  Package libkio5 is not configured yet.
dpkg: error processing kdenetwork-filesharing (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of korganizer:
 korganizer depends on libakonadi-kde4 (>= 4:4.6.80); however:
  Package libakonadi-kde4 is not configured yet.
 korganizer depends on libincidenceeditorsng4 (= 4:4.7.4+git111222-0ubuntu0.1); however:
  Package libincidenceeditorsng4 is not configured yet.
 korganizer depends on libkio5 (>= 4:4.6); however:
  Package libkio5 is not configured yet.
 korganizer depends on libknewstuff3-4 (>= 4:4.6); however:
  Package libknewstuff3-4 is not configured yet.
 korganizer depends on libkparts4 (>= 4:4.6); however:
  Package libkparts4 is not configured yet.
dpkg: error processing korganizer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kfind:
 kfind depends on libkio5 (>= 4:4.6.90); however:
  Package libkio5 is not configured yet.
dpkg: error processing kfind (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libplasma3:
 libplasma3 depends on libkio5 (= 4:4.7.4-0ubuntu0.1); however:
  Package libkio5 is not configured yet.
 libplasma3 depends on libknewstuff3-4 (= 4:4.7.4-0ubuntu0.1); however:
  Package libknewstuff3-4 is not configured yet.
 libplasma3 depends on libsolid4 (= 4:4.7.4-0ubuntu0.1); however:
  Package libsolid4 is not configured yet.
dpkg: error processing libplasma3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libktexteditor4:
 libktexteditor4 depends on libkparts4 (= 4:4.7.4-0ubuntu0.1); however:
  Package libkparts4 is not configured yet.
dpkg: error processing libktexteditor4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkhtml5:
 libkhtml5 depends on libkio5 (= 4:4.7.4-0ubuntu0.1); however:
  Package libkio5 is not configured yet.
 libkhtml5 depends on libkparts4 (= 4:4.7.4-0ubuntu0.1); however:
  Package libkparts4 is not configured yet.
 libkhtml5 depends on libktexteditor4 (= 4:4.7.4-0ubuntu0.1); however:
  Package libktexteditor4 is not configured yet.
dpkg: error processing libkhtml5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ksysguard:
 ksysguard depends on libkio5 (>= 4:4.6.80); however:
  Package libkio5 is not configured yet.
 ksysguard depends on libknewstuff3-4 (>= 4:4.6.80); however:
  Package libknewstuff3-4 is not configured yet.
dpkg: error processing ksysguard (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkdepimdbusinterfaces4:
 libkdepimdbusinterfaces4 depends on libakonadi-kde4 (>= 4:4.6); however:
  Package libakonadi-kde4 is not configured yet.
 libkdepimdbusinterfaces4 depends on libkio5 (>= 4:4.6); however:
  Package libkio5 is not configured yet.
dpkg: error processing libkdepimdbusinterfaces4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkxmlrpcclient4:
 libkxmlrpcclient4 depends on libkio5 (>= 4:4.6); however:
  Package libkio5 is not configured yet.
dpkg: error processing libkxmlrpcclient4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkpimidentities4:
 libkpimidentities4 depends on libkio5 (>= 4:4.6); however:
  Package libkio5 is not configured yet.
dpkg: error processing libkpimidentities4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kpat:
 kpat depends on libkio5 (>= 4:4.7); however:
  Package libkio5 is not configured yet.
 kpat depends on libknewstuff3-4 (>= 4:4.7); however:
  Package libknewstuff3-4 is not configured yet.
dpkg: error processing kpat (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kmix:
 kmix depends on libplasma3 (>= 4:4.6); however:
  Package libplasma3 is not configured yet.
 kmix depends on libsolid4 (>= 4:4.6); however:
  Package libsolid4 is not configured yet.
dpkg: error processing kmix (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkmanagesieve4:
 libkmanagesieve4 depends on libkio5 (>= 4:4.6); however:
  Package libkio5 is not configured yet.
dpkg: error processing libkmanagesieve4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkcalutils4:
 libkcalutils4 depends on libkio5 (>= 4:4.6); however:
  Package libkio5 is not configured yet.
dpkg: error processing libkcalutils4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libmailtransport4:
 libmailtransport4 depends on libakonadi-kde4 (= 4:4.7.4-0ubuntu0.1); however:
  Package libakonadi-kde4 is not configured yet.
 libmailtransport4 depends on libkio5 (>= 4:4.6); however:
  Package libkio5 is not configured yet.
dpkg: error processing libmailtransport4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkdepim4:
 libkdepim4 depends on libakonadi-kde4 (>= 4:4.6.80); however:
  Package libakonadi-kde4 is not configured yet.
 libkdepim4 depends on libkio5 (>= 4:4.6); however:
  Package libkio5 is not configured yet.
 libkdepim4 depends on libsolid4 (>= 4:4.6); however:
  Package libsolid4 is not configured yet.
dpkg: error processing libkdepim4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkdegames5a:
 libkdegames5a depends on libkio5 (>= 4:4.7); however:
  Package libkio5 is not configured yet.
 libkdegames5a depends on libknewstuff3-4 (>= 4:4.7); however:
  Package libknewstuff3-4 is not configured yet.
dpkg: error processing libkdegames5a (--configure):
 dependency problems - leaving unconfigured
dpkg: too many errors, stopping
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.0.0-14-generic
Errors were encountered while processing:
 man-db
 xorg
 xserver-xorg
 x11-common
 linux-image-generic
 kdm
 linux-generic
 udev
 libsolid4
 libkio5
 plasma-dataengines-workspace
 kaddressbook
 libknewstuff2-4
 libkunitconversion4
 libkateinterfaces4
 plasma-desktop
 libkleo4
 ksystemlog
 libakonadi-kde4
 libmessagecomposer4
 libknotifyconfig4
 kinfocenter
 kdepim-wizards
 libincidenceeditorsng4
 kdelibs-bin
 libplasmaclock4abi2
 libknewstuff3-4
 libkparts4
 kdoctools
 plasma-widget-folderview
 ark
 kmail
 libmessagecore4
 kopete
 kdenetwork-filesharing
 korganizer
 kfind
 libplasma3
 libktexteditor4
 libkhtml5
 ksysguard
 libkdepimdbusinterfaces4
 libkxmlrpcclient4
 libkpimidentities4
 kpat
 kmix
 libkmanagesieve4
 libkcalutils4
 libmailtransport4
 libkdepim4
 libkdegames5a
Processing was halted because there were too many errors.

```

---

### Post by drmrgd on 2012-02-10
> **kooldino said:**
> Yes, it's red, and I can't use it.



Nope, that's why I did an ls -al to show you that it's not even listed there.



Correct, no results.



It would be **** poor if I was forced to reinstall. There's gotta be a way to fix this.



That sounds reasonable.



I did a locate on 5.12.4 and found it in "/usr/share/perl/5.12.4", so I pointed the symbolic link to it.

Still didn't fix the issue, though.

You almost threw me a curve with that last comment about finding the 5.12.4 directory and making a new symbolic link to it not working.  I re-read it, though, and noticed that you used locate to find it, and I'm guessing the result you got was actually the  broken symbolic link you mentioned above (red is bad!) since the result of 'locate' and the 'ls -al' from above show the same directory.  

I'm convinced that the error you're getting is because somehow Perl got messed up and there is no longer a valid install.  Since it can't find strict.pm, I think it's crashing the dpkg script and killing the rest of the update process.  

Again, though, it might be worth confirmation from someone a little more experienced with the dpkg system.  But, at this point, I can't imagine why downloading from source and recompiling would hurt much.

---

### Post by raja.genupula on 2012-02-11
> **kooldino said:**
> ```
kubby:~$ sudo dpkg --configure -a
Setting up man-db (2.6.0.2-2) ...
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.12.4 /usr/local/share/perl/5.12.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.12 /usr/share/perl/5.12 /usr/local/lib/site_perl .) at /usr/share/debconf/frontend line 5.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 5.
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of xorg:
 xorg depends on xserver-xorg (>= 1:7.6+7ubuntu7.1); however:
  Version of xserver-xorg on system is 1:7.6+7ubuntu7.
dpkg: error processing xorg (--configure):
 dependency problems - leaving unconfigured
dpkg: error processing xserver-xorg (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Setting up x11-common (1:7.6+7ubuntu7) ...
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.12.4 /usr/local/share/perl/5.12.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.12 /usr/share/perl/5.12 /usr/local/lib/site_perl .) at /usr/share/debconf/frontend line 5.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 5.
dpkg: error processing x11-common (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.0.0-15-generic; however:
  Package linux-image-3.0.0-15-generic is not installed.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdm:
 kdm depends on libkworkspace4 (= 4:4.7.3a-0ubuntu0.1); however:
  Version of libkworkspace4 on system is 4:4.7.4-0ubuntu0.1.
 kdm depends on kde-workspace-kgreet-plugins (= 4:4.7.3a-0ubuntu0.1); however:
  Version of kde-workspace-kgreet-plugins on system is 4:4.7.4-0ubuntu0.1.
dpkg: error processing kdm (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.0.0.15.17); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up udev (173-0ubuntu4.1) ...
udev start/running, process 20095
update-initramfs: deferring update (trigger activated)
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.12.4 /usr/local/share/perl/5.12.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.12 /usr/share/perl/5.12 /usr/local/lib/site_perl .) at /usr/sbin/update-rc.d line 6.
BEGIN failed--compilation aborted at /usr/sbin/update-rc.d line 6.
dpkg: error processing udev (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libsolid4:
 libsolid4 depends on udev; however:
  Package udev is not configured yet.
dpkg: error processing libsolid4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkio5:
 libkio5 depends on libsolid4 (= 4:4.7.4-0ubuntu0.1); however:
  Package libsolid4 is not configured yet.
dpkg: error processing libkio5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of plasma-dataengines-workspace:
 plasma-dataengines-workspace depends on libkio5 (>= 4:4.6.80); however:
  Package libkio5 is not configured yet.
 plasma-dataengines-workspace depends on libsolid4 (>= 4:4.6.80); however:
  Package libsolid4 is not configured yet.
dpkg: error processing plasma-dataengines-workspace (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kaddressbook:
 kaddressbook depends on libkio5 (>= 4:4.6); however:
  Package libkio5 is not configured yet.
dpkg: error processing kaddressbook (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libknewstuff2-4:
 libknewstuff2-4 depends on libkio5 (= 4:4.7.4-0ubuntu0.1); however:
  Package libkio5 is not configured yet.
dpkg: error processing libknewstuff2-4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkunitconversion4:
 libkunitconversion4 depends on libsolid4 (= 4:4.7.4-0ubuntu0.1); however:
  Package libsolid4 is not configured yet.
dpkg: error processing libkunitconversion4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkateinterfaces4:
 libkateinterfaces4 depends on libkio5 (>= 4:4.6); however:
  Package libkio5 is not configured yet.
dpkg: error processing libkateinterfaces4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of plasma-desktop:
 plasma-desktop depends on libkio5 (>= 4:4.6.80); however:
  Package libkio5 is not configured yet.
 plasma-desktop depends on libsolid4 (>= 4:4.6.80); however:
  Package libsolid4 is not configured yet.
dpkg: error processing plasma-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkleo4:
 libkleo4 depends on libkio5 (>= 4:4.6); however:
  Package libkio5 is not configured yet.
dpkg: error processing libkleo4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ksystemlog:
 ksystemlog depends on libkio5 (>= 4:4.3.4); however:
  Package libkio5 is not configured yet.
dpkg: error processing ksystemlog (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libakonadi-kde4:
 libakonadi-kde4 depends on libkio5 (>= 4:4.6); however:
  Package libkio5 is not configured yet.
 libakonadi-kde4 depends on libsolid4 (>= 4:4.6); however:
  Package libsolid4 is not configured yet.
dpkg: error processing libakonadi-kde4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libmessagecomposer4:
 libmessagecomposer4 depends on libakonadi-kde4 (>= 4:4.6); however:
  Package libakonadi-kde4 is not configured yet.
 libmessagecomposer4 depends on libkio5 (>= 4:4.6); however:
  Package libkio5 is not configured yet.
 libmessagecomposer4 depends on libkleo4 (= 4:4.7.4+git111222-0ubuntu0.1); however:
  Package libkleo4 is not configured yet.
dpkg: error processing libmessagecomposer4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libknotifyconfig4:
 libknotifyconfig4 depends on libkio5 (= 4:4.7.4-0ubuntu0.1); however:
  Package libkio5 is not configured yet.
dpkg: error processing libknotifyconfig4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kinfocenter:
 kinfocenter depends on libkio5 (>= 4:4.6.80); however:
  Package libkio5 is not configured yet.
 kinfocenter depends on libsolid4 (>= 4:4.6.80); however:
  Package libsolid4 is not configured yet.
dpkg: error processing kinfocenter (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdepim-wizards:
 kdepim-wizards depends on libkio5 (>= 4:4.6); however:
  Package libkio5 is not configured yet.
dpkg: error processing kdepim-wizards (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libincidenceeditorsng4:
 libincidenceeditorsng4 depends on libakonadi-kde4 (>= 4:4.6); however:
  Package libakonadi-kde4 is not configured yet.
 libincidenceeditorsng4 depends on libkio5 (>= 4:4.6); however:
  Package libkio5 is not configured yet.
dpkg: error processing libincidenceeditorsng4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdelibs-bin:
 kdelibs-bin depends on libkio5 (= 4:4.7.4-0ubuntu0.1); however:
  Package libkio5 is not configured yet.
dpkg: error processing kdelibs-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libplasmaclock4abi2:
 libplasmaclock4abi2 depends on libkio5 (>= 4:4.6.80); however:
  Package libkio5 is not configured yet.
dpkg: error processing libplasmaclock4abi2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libknewstuff3-4:
 libknewstuff3-4 depends on libkio5 (= 4:4.7.4-0ubuntu0.1); however:
  Package libkio5 is not configured yet.
dpkg: error processing libknewstuff3-4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkparts4:
 libkparts4 depends on libkio5 (= 4:4.7.4-0ubuntu0.1); however:
  Package libkio5 is not configured yet.
dpkg: error processing libkparts4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdoctools:
 kdoctools depends on libkio5 (= 4:4.7.4-0ubuntu0.1); however:
  Package libkio5 is not configured yet.
dpkg: error processing kdoctools (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of plasma-widget-folderview:
 plasma-widget-folderview depends on libkio5 (>= 4:4.6.90); however:
  Package libkio5 is not configured yet.
 plasma-widget-folderview depends on libsolid4 (>= 4:4.6.90); however:
  Package libsolid4 is not configured yet.
dpkg: error processing plasma-widget-folderview (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ark:
 ark depends on libkio5 (>= 4:4.6); however:
  Package libkio5 is not configured yet.
 ark depends on libkparts4 (>= 4:4.6); however:
  Package libkparts4 is not configured yet.
dpkg: error processing ark (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kmail:
 kmail depends on libakonadi-kde4 (>= 4:4.7.0); however:
  Package libakonadi-kde4 is not configured yet.
 kmail depends on libkio5 (>= 4:4.6); however:
  Package libkio5 is not configured yet.
 kmail depends on libkleo4 (= 4:4.7.4+git111222-0ubuntu0.1); however:
  Package libkleo4 is not configured yet.
 kmail depends on libknotifyconfig4 (>= 4:4.6); however:
  Package libknotifyconfig4 is not configured yet.
 kmail depends on libkparts4 (>= 4:4.6); however:
  Package libkparts4 is not configured yet.
 kmail depends on libmessagecomposer4 (= 4:4.7.4+git111222-0ubuntu0.1); however:
  Package libmessagecomposer4 is not configured yet.
 kmail depends on libsolid4 (>= 4:4.6); however:
  Package libsolid4 is not configured yet.
dpkg: error processing kmail (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libmessagecore4:
 libmessagecore4 depends on libakonadi-kde4 (>= 4:4.6); however:
  Package libakonadi-kde4 is not configured yet.
 libmessagecore4 depends on libkio5 (>= 4:4.6); however:
  Package libkio5 is not configured yet.
dpkg: error processing libmessagecore4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kopete:
 kopete depends on libkio5 (>= 4:4.6.90); however:
  Package libkio5 is not configured yet.
 kopete depends on libknewstuff2-4 (>= 4:4.6.90); however:
  Package libknewstuff2-4 is not configured yet.
 kopete depends on libknotifyconfig4 (>= 4:4.6.90); however:
  Package libknotifyconfig4 is not configured yet.
 kopete depends on libkparts4 (>= 4:4.6.90); however:
  Package libkparts4 is not configured yet.
 kopete depends on libsolid4 (>= 4:4.6.90); however:
  Package libsolid4 is not configured yet.
dpkg: error processing kopete (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdenetwork-filesharing:
 kdenetwork-filesharing depends on libkio5 (>= 4:4.6.90); however:
  Package libkio5 is not configured yet.
dpkg: error processing kdenetwork-filesharing (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of korganizer:
 korganizer depends on libakonadi-kde4 (>= 4:4.6.80); however:
  Package libakonadi-kde4 is not configured yet.
 korganizer depends on libincidenceeditorsng4 (= 4:4.7.4+git111222-0ubuntu0.1); however:
  Package libincidenceeditorsng4 is not configured yet.
 korganizer depends on libkio5 (>= 4:4.6); however:
  Package libkio5 is not configured yet.
 korganizer depends on libknewstuff3-4 (>= 4:4.6); however:
  Package libknewstuff3-4 is not configured yet.
 korganizer depends on libkparts4 (>= 4:4.6); however:
  Package libkparts4 is not configured yet.
dpkg: error processing korganizer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kfind:
 kfind depends on libkio5 (>= 4:4.6.90); however:
  Package libkio5 is not configured yet.
dpkg: error processing kfind (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libplasma3:
 libplasma3 depends on libkio5 (= 4:4.7.4-0ubuntu0.1); however:
  Package libkio5 is not configured yet.
 libplasma3 depends on libknewstuff3-4 (= 4:4.7.4-0ubuntu0.1); however:
  Package libknewstuff3-4 is not configured yet.
 libplasma3 depends on libsolid4 (= 4:4.7.4-0ubuntu0.1); however:
  Package libsolid4 is not configured yet.
dpkg: error processing libplasma3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libktexteditor4:
 libktexteditor4 depends on libkparts4 (= 4:4.7.4-0ubuntu0.1); however:
  Package libkparts4 is not configured yet.
dpkg: error processing libktexteditor4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkhtml5:
 libkhtml5 depends on libkio5 (= 4:4.7.4-0ubuntu0.1); however:
  Package libkio5 is not configured yet.
 libkhtml5 depends on libkparts4 (= 4:4.7.4-0ubuntu0.1); however:
  Package libkparts4 is not configured yet.
 libkhtml5 depends on libktexteditor4 (= 4:4.7.4-0ubuntu0.1); however:
  Package libktexteditor4 is not configured yet.
dpkg: error processing libkhtml5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ksysguard:
 ksysguard depends on libkio5 (>= 4:4.6.80); however:
  Package libkio5 is not configured yet.
 ksysguard depends on libknewstuff3-4 (>= 4:4.6.80); however:
  Package libknewstuff3-4 is not configured yet.
dpkg: error processing ksysguard (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkdepimdbusinterfaces4:
 libkdepimdbusinterfaces4 depends on libakonadi-kde4 (>= 4:4.6); however:
  Package libakonadi-kde4 is not configured yet.
 libkdepimdbusinterfaces4 depends on libkio5 (>= 4:4.6); however:
  Package libkio5 is not configured yet.
dpkg: error processing libkdepimdbusinterfaces4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkxmlrpcclient4:
 libkxmlrpcclient4 depends on libkio5 (>= 4:4.6); however:
  Package libkio5 is not configured yet.
dpkg: error processing libkxmlrpcclient4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkpimidentities4:
 libkpimidentities4 depends on libkio5 (>= 4:4.6); however:
  Package libkio5 is not configured yet.
dpkg: error processing libkpimidentities4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kpat:
 kpat depends on libkio5 (>= 4:4.7); however:
  Package libkio5 is not configured yet.
 kpat depends on libknewstuff3-4 (>= 4:4.7); however:
  Package libknewstuff3-4 is not configured yet.
dpkg: error processing kpat (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kmix:
 kmix depends on libplasma3 (>= 4:4.6); however:
  Package libplasma3 is not configured yet.
 kmix depends on libsolid4 (>= 4:4.6); however:
  Package libsolid4 is not configured yet.
dpkg: error processing kmix (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkmanagesieve4:
 libkmanagesieve4 depends on libkio5 (>= 4:4.6); however:
  Package libkio5 is not configured yet.
dpkg: error processing libkmanagesieve4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkcalutils4:
 libkcalutils4 depends on libkio5 (>= 4:4.6); however:
  Package libkio5 is not configured yet.
dpkg: error processing libkcalutils4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libmailtransport4:
 libmailtransport4 depends on libakonadi-kde4 (= 4:4.7.4-0ubuntu0.1); however:
  Package libakonadi-kde4 is not configured yet.
 libmailtransport4 depends on libkio5 (>= 4:4.6); however:
  Package libkio5 is not configured yet.
dpkg: error processing libmailtransport4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkdepim4:
 libkdepim4 depends on libakonadi-kde4 (>= 4:4.6.80); however:
  Package libakonadi-kde4 is not configured yet.
 libkdepim4 depends on libkio5 (>= 4:4.6); however:
  Package libkio5 is not configured yet.
 libkdepim4 depends on libsolid4 (>= 4:4.6); however:
  Package libsolid4 is not configured yet.
dpkg: error processing libkdepim4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkdegames5a:
 libkdegames5a depends on libkio5 (>= 4:4.7); however:
  Package libkio5 is not configured yet.
 libkdegames5a depends on libknewstuff3-4 (>= 4:4.7); however:
  Package libknewstuff3-4 is not configured yet.
dpkg: error processing libkdegames5a (--configure):
 dependency problems - leaving unconfigured
dpkg: too many errors, stopping
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.0.0-14-generic
Errors were encountered while processing:
 man-db
 xorg
 xserver-xorg
 x11-common
 linux-image-generic
 kdm
 linux-generic
 udev
 libsolid4
 libkio5
 plasma-dataengines-workspace
 kaddressbook
 libknewstuff2-4
 libkunitconversion4
 libkateinterfaces4
 plasma-desktop
 libkleo4
 ksystemlog
 libakonadi-kde4
 libmessagecomposer4
 libknotifyconfig4
 kinfocenter
 kdepim-wizards
 libincidenceeditorsng4
 kdelibs-bin
 libplasmaclock4abi2
 libknewstuff3-4
 libkparts4
 kdoctools
 plasma-widget-folderview
 ark
 kmail
 libmessagecore4
 kopete
 kdenetwork-filesharing
 korganizer
 kfind
 libplasma3
 libktexteditor4
 libkhtml5
 ksysguard
 libkdepimdbusinterfaces4
 libkxmlrpcclient4
 libkpimidentities4
 kpat
 kmix
 libkmanagesieve4
 libkcalutils4
 libmailtransport4
 libkdepim4
 libkdegames5a
Processing was halted because there were too many errors.

```
what you did  ?  previously we have only a few errors but now a long list . any other operations you did in this time ?

---

### Post by kooldino on 2012-02-24
Just went off of some of the suggestions in this thread.

---

