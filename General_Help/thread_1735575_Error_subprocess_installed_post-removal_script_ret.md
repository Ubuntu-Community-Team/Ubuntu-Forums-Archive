---
title: "Error: subprocess installed post-removal script returned error exit status 1"
date: 2011-04-21
forum: General Help
---

### Post by vuetrip on 2011-04-21
I can't get any updates for my system and keep getting the errors shown below, and suggestions peeps?


E: linux-image-2.6.28-11-generic: subprocess installed post-removal script returned error exit status 1
E: linux-image-2.6.28-13-generic: subprocess installed post-removal script returned error exit status 1
E: linux-image-2.6.28-14-generic: subprocess installed post-removal script returned error exit status 1
E: linux-image-2.6.28-15-generic: subprocess installed post-removal script returned error exit status 1
E: linux-image-2.6.28-19-generic: subprocess installed post-removal script returned error exit status 1

---

### Post by vuetrip on 2011-04-21
Tried this in Update Manager, Synaptic, and Terminal - all give similar replies and the same error code?

---

### Post by vuetrip on 2011-04-21
full output of the terminal is:

```
craig@washington:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  linux-image-2.6.28-11-generic linux-image-2.6.28-13-generic
  linux-image-2.6.28-14-generic linux-image-2.6.28-15-generic
  linux-image-2.6.28-19-generic linux-image-2.6.31-23-generic
  linux-image-2.6.32-30-generic
The following packages will be upgraded:
  firefox firefox-branding firefox-gnome-support language-pack-en
  language-pack-en-base libtiff4 ubufox xul-ext-ubufox
8 upgraded, 0 newly installed, 7 to remove and 0 not upgraded.
7 not fully installed or removed.
Need to get 0B/15.9MB of archives.
After this operation, 670MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 170506 files and directories currently installed.)
Removing linux-image-2.6.28-11-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.28-11-generic /boot/vmlinuz-2.6.28-11-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.28-11-generic /boot/vmlinuz-2.6.28-11-generic
/etc/default/grub: 9: splash: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-2.6.28-11-generic.postrm line 320.
dpkg: error processing linux-image-2.6.28-11-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-2.6.28-13-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.28-13-generic /boot/vmlinuz-2.6.28-13-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.28-13-generic /boot/vmlinuz-2.6.28-13-generic
/etc/default/grub: 9: splash: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-2.6.28-13-generic.postrm line 320.
dpkg: error processing linux-image-2.6.28-13-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-2.6.28-14-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.28-14-generic /boot/vmlinuz-2.6.28-14-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.28-14-generic /boot/vmlinuz-2.6.28-14-generic
/etc/default/grub: 9: splash: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-2.6.28-14-generic.postrm line 320.
dpkg: error processing linux-image-2.6.28-14-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-2.6.28-15-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.28-15-generic /boot/vmlinuz-2.6.28-15-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.28-15-generic /boot/vmlinuz-2.6.28-15-generic
/etc/default/grub: 9: splash: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-2.6.28-15-generic.postrm line 320.
dpkg: error processing linux-image-2.6.28-15-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports has already been reached
                                                                    Removing linux-image-2.6.28-19-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.28-19-generic /boot/vmlinuz-2.6.28-19-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.28-19-generic /boot/vmlinuz-2.6.28-19-generic
/etc/default/grub: 9: splash: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-2.6.28-19-generic.postrm line 320.
dpkg: error processing linux-image-2.6.28-19-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports has already been reached
                                                                    Removing linux-image-2.6.31-23-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.31-23-generic /boot/vmlinuz-2.6.31-23-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.31-23-generic /boot/vmlinuz-2.6.31-23-generic
/etc/default/grub: 9: splash: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-2.6.31-23-generic.postrm line 320.
dpkg: error processing linux-image-2.6.31-23-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports has already been reached
                                                                    Removing linux-image-2.6.32-30-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.32-30-generic /boot/vmlinuz-2.6.32-30-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.32-30-generic /boot/vmlinuz-2.6.32-30-generic
/etc/default/grub: 9: splash: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-2.6.32-30-generic.postrm line 321.
dpkg: error processing linux-image-2.6.32-30-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports has already been reached
                                                                    Errors were encountered while processing:
 linux-image-2.6.28-11-generic
 linux-image-2.6.28-13-generic
 linux-image-2.6.28-14-generic
 linux-image-2.6.28-15-generic
 linux-image-2.6.28-19-generic
 linux-image-2.6.31-23-generic
 linux-image-2.6.32-30-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

if no-one knows how to fix this can anyone tell me how to unmark the old kernels for removal?

---

### Post by vuetrip on 2011-04-21
I've been trying to fix this for over two hours now, does anyone know how to sort it out?

---

### Post by vuetrip on 2011-04-21
hi I'm having a problem with my system atm, could anyone help? my first post is: [here]("http://ubuntuforums.org/showthread.php?t=1735575"), kind of makes sense to keep it in one place :):D

---

### Post by howefield on 2011-04-21
Duplicate threads merged.

Please keep to one thread per issue and feel free to bump it once per 24(ish) hours if no reply.

---

### Post by Dutch70 on 2011-04-21
First, give this a quick read...
[[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=1422475[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1422475")

To remove old kernels, either use synaptic & search for "linux-image-2", mark the old ones for removal and click apply, or use Ubuntu Tweak which will remove them for you. 

As for the problem you posted about. Try running these commands...
```
sudo dpkg --configure -a
```
or...
```
sudo apt-get install -f
```

---

### Post by vuetrip on 2011-04-21
Hi, thanks for the reply, I tried your suggestions and have included the output from the terminal at the end of this post.

How I got in this trouble:
I was trying out themes for grub with [http://ubuntuguide.net/decorate-grub-2-boot-loader-with-burg-manager-gui-for-burg]("http://ubuntuguide.net/decorate-grub-2-boot-loader-with-burg-manager-gui-for-burg") that software and there was an option to clear old kernels, that's how I got to where I am now.


From here all I want to do is get these packages either removed so my updates work again, or unmarked for removal so it doesn't try to remove them before running updates, any further assistance would be greatly appreciated :D

```
craig@washington:/var/www$ sudo dpkg --configure -a
craig@washington:/var/www$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  linux-image-2.6.28-11-generic linux-image-2.6.28-13-generic
  linux-image-2.6.28-14-generic linux-image-2.6.28-15-generic
  linux-image-2.6.28-19-generic linux-image-2.6.31-23-generic
  linux-image-2.6.32-30-generic
0 upgraded, 0 newly installed, 7 to remove and 8 not upgraded.
7 not fully installed or removed.
After this operation, 669MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 170506 files and directories currently installed.)
Removing linux-image-2.6.28-11-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.28-11-generic /boot/vmlinuz-2.6.28-11-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.28-11-generic /boot/vmlinuz-2.6.28-11-generic
/etc/default/grub: 9: splash: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-2.6.28-11-generic.postrm line 320.
dpkg: error processing linux-image-2.6.28-11-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports has already been reached
                                                                    Removing linux-image-2.6.28-13-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.28-13-generic /boot/vmlinuz-2.6.28-13-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.28-13-generic /boot/vmlinuz-2.6.28-13-generic
/etc/default/grub: 9: splash: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-2.6.28-13-generic.postrm line 320.
dpkg: error processing linux-image-2.6.28-13-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports has already been reached
                                                                    Removing linux-image-2.6.28-14-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.28-14-generic /boot/vmlinuz-2.6.28-14-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.28-14-generic /boot/vmlinuz-2.6.28-14-generic
/etc/default/grub: 9: splash: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-2.6.28-14-generic.postrm line 320.
dpkg: error processing linux-image-2.6.28-14-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports has already been reached
                                                                    Removing linux-image-2.6.28-15-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.28-15-generic /boot/vmlinuz-2.6.28-15-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.28-15-generic /boot/vmlinuz-2.6.28-15-generic
/etc/default/grub: 9: splash: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-2.6.28-15-generic.postrm line 320.
dpkg: error processing linux-image-2.6.28-15-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports has already been reached
                                                                    Removing linux-image-2.6.28-19-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.28-19-generic /boot/vmlinuz-2.6.28-19-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.28-19-generic /boot/vmlinuz-2.6.28-19-generic
/etc/default/grub: 9: splash: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-2.6.28-19-generic.postrm line 320.
dpkg: error processing linux-image-2.6.28-19-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports has already been reached
                                                                    Removing linux-image-2.6.31-23-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.31-23-generic /boot/vmlinuz-2.6.31-23-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.31-23-generic /boot/vmlinuz-2.6.31-23-generic
/etc/default/grub: 9: splash: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-2.6.31-23-generic.postrm line 320.
dpkg: error processing linux-image-2.6.31-23-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports has already been reached
                                                                    Removing linux-image-2.6.32-30-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.32-30-generic /boot/vmlinuz-2.6.32-30-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.32-30-generic /boot/vmlinuz-2.6.32-30-generic
/etc/default/grub: 9: splash: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-2.6.32-30-generic.postrm line 321.
dpkg: error processing linux-image-2.6.32-30-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports has already been reached
                                                                    Errors were encountered while processing:
 linux-image-2.6.28-11-generic
 linux-image-2.6.28-13-generic
 linux-image-2.6.28-14-generic
 linux-image-2.6.28-15-generic
 linux-image-2.6.28-19-generic
 linux-image-2.6.31-23-generic
 linux-image-2.6.32-30-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
craig@washington:/var/www$ 

```

---

### Post by Dutch70 on 2011-04-21
Have you removed Burg? I'm really not sure, but if it's settings. Try running these...
```
sudo apt-get autoclean 
```
```
sudo apt-get autoremove
```
```
sudo apt-get clean
```

---

### Post by vuetrip on 2011-04-22
Hi, tried those again, and it still comes up with the same output in the terminal.

also went into Synaptic Package manager and tried in there, whilst there I noticed that there are no linux-header-x-x-x for these linux-image packages and right clicking on the packages and selecting Properties -> Installed Files shows an empty box whereas with my other installed kernels it provides a very long list, think maybe these packages are gone already and the problem is that it can't find the files to remove?

and burg is still on the system, it won't let me install, upgrade or remove anything :S

where is the file that lists all the installed packages? and has it been in the same place since 8.04ish as that's when i first installed ubuntu on this machine

---

### Post by drs305 on 2011-04-22
The problem appears to be in the post installation script of grub: */etc/kernel/postrm.d/zz-update-grub* 

I don't have the problem but I've done what follows. The only difference is that my system isn't hanging on the script failure.

Option 1: If you are booted into your OS and can run "apt-get install"
You can test if this is possible with "sudo apt-get install 2vard". It's a really small package. If it installs ok:
a. Purge grub-common. The command will uninstall grub-common and grub-pc
```
sudo apt-get purge grub-common
```
This will remove the zz-update-grub script.
You will be warned you are removing your bootloader. Tab to OK and ENTER.
b. Install grub-pc. It will install grub-common and grub-pc.
```
sudo apt-get install grub-pc
```
Tab to OK, and use the spacebar to select ONLY the Ubuntu drive, not the partition.
This will restore the zz-update-grub file. If the problem was with the grub file, this should fix it.
c. Try to update your system again.

Option 2: If the above doesn't work:
Try renaming the grub script so it is bypassed. It isn't a long term solution but you may be able to run your updates.
```
sudo mv /etc/kernel/postrm.d/zz-update-grub /etc/kernel/postrm.d/zz-update-grub.bad
```

---

### Post by vuetrip on 2011-04-22
Thank you drs305 it now works fine update/upgrade and the old linux-image packages are gone. I'm going to restart the comp to make sure nothing breaks on restart then I'll mark this thread as solved.

:D :D :D

---

### Post by drs305 on 2011-04-22
> **vuetrip said:**
> Thank you drs305 it now works fine update/upgrade and the old linux-image packages are gone. I'm going to restart the comp to make sure nothing breaks on restart then I'll mark this thread as solved.

:D :D :D

Glad to hear it. Did the purge/reinstall do it or did you just rename the script?

---

### Post by vuetrip on 2011-04-22
> **drs305 said:**
> Glad to hear it. Did the purge/reinstall do it or did you just rename the script?

purge/install failed with the same errors.

I renamed the script and got rid of the linux-image packages, renamed the script back to it's original name, then purged and reinstalled grub.

---

### Post by craniumonempty on 2011-07-13
had the same problem... had knoppix livecd and went trigger happy and it  tried to install a linux-image. Then it didn't want to uninstall even  though the original was still there. I figured it was something to do  with grub because of the line, but all is hunky-dorry now...

basically:

```
sudo mv /etc/kernel/postrm.d/zz-update-grub /etc/kernel/postrm.d/zz-update-grub.bad

sudo apt-get install -f

sudo mv /etc/kernel/postrm.d/zz-update-grub.bad /etc/kernel/postrm.d/zz-update-grub
```Then it all worked fine. Thanks.

---

### Post by nldquy on 2013-04-17
> **drs305 said:**
> The problem appears to be in the post installation script of grub: */etc/kernel/postrm.d/zz-update-grub* 

I don't have the problem but I've done what follows. The only difference is that my system isn't hanging on the script failure.

Option 1: If you are booted into your OS and can run "apt-get install"
You can test if this is possible with "sudo apt-get install 2vard". It's a really small package. If it installs ok:
a. Purge grub-common. The command will uninstall grub-common and grub-pc
```
sudo apt-get purge grub-common
```
This will remove the zz-update-grub script.
You will be warned you are removing your bootloader. Tab to OK and ENTER.
b. Install grub-pc. It will install grub-common and grub-pc.
```
sudo apt-get install grub-pc
```
Tab to OK, and use the spacebar to select ONLY the Ubuntu drive, not the partition.
This will restore the zz-update-grub file. If the problem was with the grub file, this should fix it.
c. Try to update your system again.

Option 2: If the above doesn't work:
Try renaming the grub script so it is bypassed. It isn't a long term solution but you may be able to run your updates.
```
sudo mv /etc/kernel/postrm.d/zz-update-grub /etc/kernel/postrm.d/zz-update-grub.bad
```

Excellent. You saved my life drs305. Thank you.

---

### Post by oldos2er on 2013-04-17
Old thread closed.

---

