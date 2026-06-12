---
title: "What's wrong with my Ubuntu?"
date: 2009-08-12
forum: General Help
---

### Post by Lockheed on 2009-08-12
Every time I install or uninstall packages using Synaptic or console command, it also does something with kernel. I have no idea why or what for.

Here is an example when I install codecs:
```
sudo apt-get install build-essential checkinstall gpac libgpac-dev git-core yasm
[sudo] password for juha: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
checkinstall is already the newest version.
The following packages were automatically installed and are no longer required:
  libopenal1 libjinglep2p0.3-0 libmime-types-perl libnet-ssleay-perl
  linux-backports-modules-2.6.28-12-generic python-xmmsclient nspluginwrapper
  gstreamer0.10-plugins-farsight python-openssl libsvga1 libossp-uuid-perl
  libqt4-test libboost-date-time1.34.1 libgstfarsight0.10-0 libmime-tools-perl
  libjinglexmllite0.3-0 libfcgi-perl python-msn libnet-google-perl
  python-soappy blt python-tk libsoap-lite-perl python-fpconst libggi2 libgii1
  libboost-thread1.34.1 libjinglebase0.3-0 libgii1-target-x libwww-search-perl
  libemail-date-format-perl libuser-perl libjcode-pm-perl libggi-target-x
  libnet-libidn-perl libnice0 gstreamer0.10-nice libconvert-binhex-perl
  libio-socket-ssl-perl libossp-uuid15 libmime-lite-perl python-crypto
  libjinglexmpp0.3-0 python-numeric
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  freeglut3 libdigest-sha1-perl liberror-perl libgpac0.4.4 libwxbase2.6-0
  libwxgtk2.6-0
Suggested packages:
  git-doc git-arch git-cvs git-svn git-email git-daemon-run git-gui gitk
  gitweb
The following NEW packages will be installed
  freeglut3 git-core gpac libdigest-sha1-perl liberror-perl libgpac-dev
  libgpac0.4.4 libwxbase2.6-0 libwxgtk2.6-0 yasm
0 upgraded, 10 newly installed, 0 to remove and 49 not upgraded.
1 not fully installed or removed.
Need to get 12.5MB of archives.
After this operation, 33.7MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get: 1 http://gb.archive.ubuntu.com jaunty/main freeglut3 2.4.0-6.1ubuntu1 [98.9kB]
Get: 2 http://gb.archive.ubuntu.com jaunty/main liberror-perl 0.17-1 [23.8kB]
Get: 3 http://gb.archive.ubuntu.com jaunty/main libdigest-sha1-perl 2.11-2build2 [26.4kB]
Get: 4 http://gb.archive.ubuntu.com jaunty/main git-core 1:1.6.0.4-1ubuntu2 [4733kB]
Get: 5 http://gb.archive.ubuntu.com jaunty/multiverse libgpac0.4.4 0.4.4-0.3ubuntu4 [1140kB]
Get: 6 http://gb.archive.ubuntu.com jaunty/universe libwxbase2.6-0 2.6.3.2.2-3ubuntu4 [546kB]
Get: 7 http://gb.archive.ubuntu.com jaunty/universe libwxgtk2.6-0 2.6.3.2.2-3ubuntu4 [2840kB]
Get: 8 http://gb.archive.ubuntu.com jaunty/multiverse gpac 0.4.4-0.3ubuntu4 [739kB]
Get: 9 http://gb.archive.ubuntu.com jaunty/multiverse libgpac-dev 0.4.4-0.3ubuntu4 [1710kB]
Get: 10 http://gb.archive.ubuntu.com jaunty/universe yasm 0.7.1-0ubuntu2 [599kB]
Fetched 12.5MB in 1s (6302kB/s)
Selecting previously deselected package freeglut3.
(Reading database ... 
[COLOR="#ff0000"]dpkg: serious warning: files list file for package `linux-image-2.6.30-candela' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `linux-image-2.6.30-red' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `linux-headers-2.6.30-candela' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `linux-headers-2.6.30-red' missing, assuming package has no files currently installed.
244542 files and directories currently installed.)[/COLOR]
Unpacking freeglut3 (from .../freeglut3_2.4.0-6.1ubuntu1_amd64.deb) ...
Selecting previously deselected package liberror-perl.
Unpacking liberror-perl (from .../liberror-perl_0.17-1_all.deb) ...
Selecting previously deselected package libdigest-sha1-perl.
Unpacking libdigest-sha1-perl (from .../libdigest-sha1-perl_2.11-2build2_amd64.deb) ...
Selecting previously deselected package git-core.
Unpacking git-core (from .../git-core_1%3a1.6.0.4-1ubuntu2_amd64.deb) ...
Selecting previously deselected package libgpac0.4.4.
Unpacking libgpac0.4.4 (from .../libgpac0.4.4_0.4.4-0.3ubuntu4_amd64.deb) ...
Selecting previously deselected package libwxbase2.6-0.
Unpacking libwxbase2.6-0 (from .../libwxbase2.6-0_2.6.3.2.2-3ubuntu4_amd64.deb) ...
Selecting previously deselected package libwxgtk2.6-0.
Unpacking libwxgtk2.6-0 (from .../libwxgtk2.6-0_2.6.3.2.2-3ubuntu4_amd64.deb) ...
Selecting previously deselected package gpac.
Unpacking gpac (from .../gpac_0.4.4-0.3ubuntu4_amd64.deb) ...
Selecting previously deselected package libgpac-dev.
Unpacking libgpac-dev (from .../libgpac-dev_0.4.4-0.3ubuntu4_amd64.deb) ...
Selecting previously deselected package yasm.
Unpacking yasm (from .../yasm_0.7.1-0ubuntu2_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for menu ...
[COLOR="#ff0000"]Setting up linux-image-2.6.30.1-azure (386) ...
Running depmod.
Finding valid ramdisk creators.
Using mkinitramfs-kpkg to build the ramdisk.
initrd.img(/boot/initrd.img-2.6.30.1-azure
) points to /boot/initrd.img-2.6.30.1-azure
 (/boot/initrd.img-2.6.30.1-azure) -- doing nothing at /var/lib/dpkg/info/linux-image-2.6.30.1-azure.postinst line 588.
vmlinuz(/boot/vmlinuz-2.6.30.1-azure
) points to /boot/vmlinuz-2.6.30.1-azure
 (/boot/vmlinuz-2.6.30.1-azure) -- doing nothing at /var/lib/dpkg/info/linux-image-2.6.30.1-azure.postinst line 588.
Running postinst hook script update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.30.1-azure
Found kernel: /boot/vmlinuz-2.6.30.1
Found kernel: /boot/vmlinuz-2.6.30-0814
Found kernel: /boot/vmlinuz-2.6.30
Found kernel: /boot/vmlinuz-2.6.28-12-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
run-parts: executing /etc/kernel/postinst.d/nvidia-common
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 20
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.30.1-azure.postinst line 1186.
dpkg: error processing linux-image-2.6.30.1-azure (--configure):
 subprocess post-installation script returned error exit status 2[/COLOR]
Setting up freeglut3 (2.4.0-6.1ubuntu1) ...

Setting up liberror-perl (0.17-1) ...
Setting up libdigest-sha1-perl (2.11-2build2) ...
Setting up git-core (1:1.6.0.4-1ubuntu2) ...
Setting up yasm (0.7.1-0ubuntu2) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Processing triggers for menu ...
[COLOR="Red"]Errors were encountered while processing:
 linux-image-2.6.30.1-azure
E: Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR]

```

---

### Post by P4man on 2009-08-12
Try running:
```
sudo dpkg --configure -a
```

---

### Post by Lockheed on 2009-08-12
That did not help.

---

### Post by zkriesse on 2009-08-12
It looks like you might be running the sudo command a little wrong. What did you try to install exactly?

---

### Post by Lockheed on 2009-08-12
It happens when I install or uninstall anything. Whatever involves Synaptic.

---

### Post by zkriesse on 2009-08-12
Synaptic Package manager you mean??? That shouldn't be a problem....

---

### Post by Lockheed on 2009-08-12
Well, I know it shouldn't. But it is.

---

### Post by jocko on 2009-08-12
> **Lockheed said:**
> ```
[COLOR=#ff0000]dpkg: serious warning: files list file for package `[COLOR=Blue]linux-image-2.6.30-candela'[/COLOR] missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `[COLOR=Blue]linux-image-2.6.30-red[/COLOR]' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `[COLOR=Blue]linux-headers-2.6.30-candela[/COLOR]' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `[COLOR=Blue]linux-headers-2.6.30-red[/COLOR]' missing, assuming package has no files currently installed.
244542 files and directories currently installed.)[/COLOR]
...
[COLOR=#ff0000]Setting up linux-image-2.6.30.1-azure (386) ...
Running depmod.
Finding valid ramdisk creators.
Using mkinitramfs-kpkg to build the ramdisk.
initrd.img(/boot/initrd.img-2.6.30.1-azure
) points to /boot/initrd.img-2.6.30.1-azure
 (/boot/initrd.img-2.6.30.1-azure) -- doing nothing at [COLOR=Blue]/var/lib/dpkg/info/linux-image-2.6.30.1-azure.postinst[/COLOR] line 588.
vmlinuz(/boot/vmlinuz-2.6.30.1-azure
) points to /boot/vmlinuz-2.6.30.1-azure
 (/boot/vmlinuz-2.6.30.1-azure) -- doing nothing at [COLOR=Blue]/var/lib/dpkg/info/linux-image-2.6.30.1-azure.postinst[/COLOR] line 588.
Running postinst hook script update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.30.1-azure
Found kernel: /boot/vmlinuz-2.6.30.1
Found kernel: /boot/vmlinuz-2.6.30-0814
Found kernel: /boot/vmlinuz-2.6.30
Found kernel: /boot/vmlinuz-2.6.28-12-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
run-parts: executing /etc/kernel/postinst.d/nvidia-common
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 20
Failed to process /etc/kernel/postinst.d at [COLOR=Blue]/var/lib/dpkg/info/linux-image-2.6.30.1-azure.postinst[/COLOR] line 1186.
dpkg: error processing linux-image-2.6.30.1-azure (--configure):
 subprocess post-installation script returned error exit status 2[/COLOR]
...
[COLOR=Red]Errors were encountered while processing:
 linux-image-2.6.30.1-azure
E: Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR]

```
Those kernels (-azure, -candela and -red) it complains about does not look like they come from the ubuntu repositories, have you compiled them yourself or are they from some third party repo? There's probably something wrong with the packages you installed those kernels from, which makes dpkg try and fail to run those postinst scripts every time. I've got the same with a self-compiled kernel, and I haven't figured out how to fix it properly.
The "dpkg: serious warning: files list file for package" errors lets me suspect the packages are not even proper debian packages. Maybe they are just checkinstall packages? In that case it's not very surprising. Checkinstall does not generate fully functional debian packages.


An ugly fix for one of the errors (the postist scripts that fail):
```
sudo rm [COLOR=Blue]/var/lib/dpkg/info/linux-image-2.6.30.1-azure.postinst[/COLOR]
```That removes the script that fails, which will prevent those errors from showing up.
But the "dpkg: serious warning: files list file for package" errors I have no clue how to fix, other than uninstalling the packages...

---

### Post by zkriesse on 2009-08-12
Ohhhkkkk...hmmm. Do you or are you using a different system to post on here? Because if you are then maybe you could use a live cd and try the repair/recover option.

---

### Post by Lockheed on 2009-08-12
No, I am using this system and it is working fine. Why would I need to use LiveCD to fix it?

And yes, I compiled my own kernel I am using now (azure) which is the newest official kernel downloaded from official kernel site. 

I followed the Master Kernel guide so don't know how is it a problem.

---

### Post by jocko on 2009-08-12
> **Lockheed said:**
> I followed the Master Kernel guide so don't know how is it a problem.
That's the guide I used to compile mine that gives the postinst errors as well (but I don't get those other errors about missing file lists). Mine is a 2.6.28 kernel (from the source in the jaunty repos), just patched it to be able to undervolt the cpu to keep it cool and I also removed some modules I know I don't need.
So perhaps there's something in the Master Kernel thread needs to be changed...

Edit: it looks like this is a known problem: [http://ubuntuforums.org/showthread.php?t=311158&highlight=Master+Kernel&page=127](http://ubuntuforums.org/showthread.php?t=311158&highlight=Master+Kernel&page=127). Apparently it's something in the nvidia-common package that causes the scripts to fail, so uninstalling nvidia-common will allow the scripts to finish, and then it should be ok to install nvidia-common again...

---

### Post by Lockheed on 2009-08-12
Is this nvidia-common needed for anything? Can I just premanently remove it?
Removing it temporarily just to install/uninstall something makes no sense.

---

### Post by jocko on 2009-08-12
> **Lockheed said:**
> Is this nvidia-common needed for anything? Can I just premanently remove it?
Removing it temporarily just to install/uninstall something makes no sense.
If I understand it correctly, it pretty much just provides the information the restricted driver manager needs to know which nvidia driver support your graphics card. If you don't have an nvidia graphichs card you don't need it, and I don't even think you need it after the nvidia driver has been installed. So try leaving it uninstalled.

---

### Post by Lockheed on 2009-08-20
I can no confirm uninstalling nvidia-common made no difference.
Help!

---

### Post by Lockheed on 2009-08-21
Maybe this will shed some light on the subject:
```
$ sudo dpkg-reconfigure linux-image-$(uname -r)
/usr/sbin/dpkg-reconfigure: linux-image-2.6.30.1-azure is broken or not fully installed.

```

---

### Post by Lockheed on 2009-08-28
bump...

---

### Post by SPr on 2009-08-28
```

dpkg-reconfigure linux-image-2.6.30.1-azure

```
and reboot. What errors does that give?

---

### Post by Lockheed on 2009-08-28
> **SPr said:**
> ```

dpkg-reconfigure linux-image-2.6.30.1-azure

```
and reboot. What errors does that give?

```
$ sudo dpkg-reconfigure linux-image-2.6.30.1-azure
/usr/sbin/dpkg-reconfigure: linux-image-2.6.30.1-azure is broken or not fully installed

```

---

### Post by SPr on 2009-08-28
LOL. I should have read the full thread.

Have you tried to re-compile the kernel?

---

### Post by Lockheed on 2009-08-28
> **SPr said:**
> LOL. I should have read the full thread.

Have you tried to re-compile the kernel?

Oh no, no, no. I am not touching that anytime soon. It took me too much time and nerves to make it usable the last time.

But I am not sure that would fix it anyway, cause in the previous kernel (also self-compiled) there was the same problem.

---

### Post by Lockheed on 2009-08-31
Ok, I have another example of this behaviour. This time I was purging pidgin.
```
$ sudo apt-get purge pidgin*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting pidgin-privacy-please for regex 'pidgin*'
Note, selecting pidgin-libnotify for regex 'pidgin*'
The following packages will be REMOVED:
  libpurple0* pidgin-data*
0 upgraded, 0 newly installed, 2 to remove and 34 not upgraded.
1 not fully installed or removed.
After this operation, 27.4MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 156131 files and directories currently installed.)
Removing libpurple0 ...
Purging configuration files for libpurple0 ...
Removing pidgin-data ...
Purging configuration files for pidgin-data ...
Processing triggers for man-db ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Setting up linux-image-2.6.30.1-azure (386) ...
Running depmod.
Finding valid ramdisk creators.
Using mkinitramfs-kpkg to build the ramdisk.
initrd.img(/boot/initrd.img-2.6.30.1-azure
) points to /boot/initrd.img-2.6.30.1-azure
 (/boot/initrd.img-2.6.30.1-azure) -- doing nothing at /var/lib/dpkg/info/linux-image-2.6.30.1-azure.postinst line 588.
vmlinuz(/boot/vmlinuz-2.6.30.1-azure
) points to /boot/vmlinuz-2.6.30.1-azure
 (/boot/vmlinuz-2.6.30.1-azure) -- doing nothing at /var/lib/dpkg/info/linux-image-2.6.30.1-azure.postinst line 588.
Running postinst hook script update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.30.1-azure
Found kernel: /boot/vmlinuz-2.6.30.1
Found kernel: /boot/vmlinuz-2.6.30
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
run-parts: executing /etc/kernel/postinst.d/nvidia-common
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 20
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.30.1-azure.postinst line 1186.
dpkg: error processing linux-image-2.6.30.1-azure (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.30.1-azure
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by SPr on 2009-08-31
Have you tried reinstalling nvidia-common?

See [https://bugs.launchpad.net/ubuntu/+source/nvidia-common/+bug/303795](https://bugs.launchpad.net/ubuntu/+source/nvidia-common/+bug/303795)

---

### Post by Lockheed on 2009-08-31
> **SPr said:**
> Have you tried reinstalling nvidia-common?

See [https://bugs.launchpad.net/ubuntu/+source/nvidia-common/+bug/303795](https://bugs.launchpad.net/ubuntu/+source/nvidia-common/+bug/303795)

Yes, I tried.

---

### Post by Exodist on 2009-08-31
I belive the nVidia Common files when they where in the /etc/kernel/post~ folders prevented your custom kernel from installing correctly.

Hop back to the 2.6.28 ubu kernel right quick. 
Remove the nvidia commmon crap, even may have to remove it manualy.
use dpkg and remove your custom kernel, then install it back.

See if that helps.


EDIT:

Forgot to mention that that will help with the current kernel. But Those others need to be uninstalled. But if your like me, since they errored on install. Uninstalling a deb package that dpkg doesnt see is becoming a pain in the rear..
I have 2 custom kernels installed, sorta.. 
The one I am running was done the way I normally do things, slighty more simpler then the Master Kernel Thread list. When mine error, I thought there may have been something  *new going on, or something had changed. So I tried the MKT way and had actualy more issues. Now cant seem to remove the freaking package as dpkg has no listing of it. /sigh

---

### Post by Lockheed on 2009-08-31
> **Exodist said:**
> I belive the nVidia Common files when they where in the /etc/kernel/post~ folders prevented your custom kernel from installing correctly.

Hop back to the 2.6.28 ubu kernel right quick. 
Remove the nvidia commmon crap, even may have to remove it manualy.
use dpkg and remove your custom kernel, then install it back.

See if that helps.

That won't work cause I removed every other kernel. Can I just compile a new one with default settings of current kernel?

---

### Post by Exodist on 2009-08-31
> **Lockheed said:**
> That won't work cause I removed every other kernel. Can I just compile a new one with default settings of current kernel?

Could you,  yes. Would it resolve the issue, prob not.

I am not sure what I finally did to get that crap kernel to show up in apt. I am just glad it did and I was able to remove it.

Here is what I recomend.  
1) go back to the ubuntu kernel. 2.6.28
2) manually remove that nvidia crap from /etc/kernel/post~whatever.d, should be two of them. lazy way is to 'sudo nautilus' and if you want both those nvidia.common files are the same file. Just chunk on into you root home folder.
3) Follow the traditional way to compile your kernel I have listed below. Its the way I been doing it for 10 years and works with alot less BS then MKT has. (sorry if that offends anyone)


Build Kernel
-----------------------------------------------------------------------------------------------------------------------
**customname1 can be any name you wish. Just need a number at the end. Example: bob1, bob2, etc.. 

1 ) Install the packages needed: Most prob already installed anyway.
sudo apt-get install build-essential libncurses5 libncurses5-dev libqt3-headers kernel-package bin86 libqt3-mt-dev fakeroot

2 ) Download newest stable kernel: 2.6.30.5 (full source no patches)

3 ) copy the kernel to /usr/src:
sudo cp  linux-2.6.30.5.tar.bz2 /usr/src

4 ) cd over to /usr/src and unpack it:
sudo tar -xvjf linux-2.6.30.5.tar.bz2

5 ) Now lets change the kernel source dir name:
sudo mv linux-2.6.30.5/ linux-2.6.30.5-customname1

6 ) remove any existing linux symlinks and create one to new kernel;
sudo rm -rf linux && ln -s /usr/src/linux-2.6.30.5-customname1 linux

7 ) cd to linux

8 ) Import your current kernel config for compatability:
- get kernel full name:
uname -r
- now use that as reference and get a copy of the config file, example shows ubuntu kernel:
sudo cp /boot/config-2.6.28-15_x86-64-generic .config

9 ) Lets setup the kernel, BTW i recomend setting Timer Frequency to 1000 and change Preemtion model to Low Latency Desktop. This will shave 10+ secs off boot time and make desktop performance more spunky, make sure processor model is the x86-64 one for better compatability:
sudo make menuconfig

10 ) Now using make-kpkg we will build the kernel .deb package:
sudo make-kpkg clean
sudo make-kpkg -initrd --revision=customname1 kernel_image

11 ) cd ..

12 ) There shouldnt be any build issues and if there were none we can install the kernel:
sudo dpkg -i linux-image-2.6.30.5-customname1*.deb

13 ) Should'nt be any install errors, *should'nt*..  Reboot if there wasnt any and enjoy.

---

### Post by tormod on 2009-08-31
It is no mystery:
1. the nvidia-common package installs a file in /etc/kernel/ so it will be run if a kernel is installed.
2. since this will be part of a kernel installation process, the kernel package is not considered fully installed as long as the postinst is failing.
3. therefore it will rerun the postinst every time apt-get install is run
4. /removing/ a package does not purge configuration files and these /etc/kernel hooks are considered configuration files (under /etc)
5. therefore you need to /purge/ the nvidia-common package
```
sudo apt-get purge nvidia-common
```

If you had removed it without purging, reinstall and then purge.

If you have no nvidia GPU or you prefer to use free drivers, feel free (pun intended) to purge all the nvidia-* (closed-source) package stuff.

---

### Post by Lockheed on 2009-09-01
Exodist and thormod, thank you. 

What I did is tried to purge nvidia-common. Even though I already tried it 10 times before, this time it seemes to have helped. Maybe because I also removed everything related to other kernels using synaptic and apt-get.

---

### Post by Exodist on 2009-09-01
> **tormod said:**
> It is no mystery:
1. the nvidia-common package installs a file in /etc/kernel/ so it will be run if a kernel is installed.
2. since this will be part of a kernel installation process, the kernel package is not considered fully installed as long as the postinst is failing.
3. therefore it will rerun the postinst every time apt-get install is run
4. /removing/ a package does not purge configuration files and these /etc/kernel hooks are considered configuration files (under /etc)
5. therefore you need to /purge/ the nvidia-common package
```
sudo apt-get purge nvidia-common
```If you had removed it without purging, reinstall and then purge.

If you have no nvidia GPU or you prefer to use free drivers, feel free (pun intended) to purge all the nvidia-* (closed-source) package stuff.

Agree  you should purge it.. but it wasnt removing it for me tho.. dont know why.. So I just removed it manually and it then stopped complaining about it. /scratch head

:-)

---

### Post by Lockheed on 2009-09-01
> **tormod said:**
> If you have no nvidia GPU or you prefer to use free drivers, feel free (pun intended) to purge all the nvidia-* (closed-source) package stuff.

I have newest 190 nvidia drivers. Can I still do it? I don't know if they are free drivers. I never heard about other drivers for nvidia's GPUs.

---

### Post by jocko on 2009-09-01
> **Lockheed said:**
> I have newest 190 nvidia drivers. Can I still do it? I don't know if they are free drivers. I never heard about other drivers for nvidia's GPUs.
The open source nvidia drivers ("nv" and "nouveau")  are 2d only. If you want 3d acceleration you need the proprietary driver ("nvidia").

---

### Post by Exodist on 2009-09-01
Yes you can still remove them. Just install your own drivers from nVidias website. No need for those I dont care what anyone else says. 
Their are kernel drivers for nv to provide ok 2d video for your nvidia video card. Those common ones have no place there. Remove them, build your kernel, then boot into your kernel and then use the proprietary nvidia drivers to build the driver module to run your card.

---

### Post by indosupremacy on 2009-09-08
> **Lockheed said:**
> Every time I install or uninstall packages using Synaptic or console command, it also does something with kernel. I have no idea why or what for.

Here is an example when I install codecs:
```
sudo apt-get install build-essential checkinstall gpac libgpac-dev git-core yasm
[sudo] password for juha: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
checkinstall is already the newest version.
The following packages were automatically installed and are no longer required:
  libopenal1 libjinglep2p0.3-0 libmime-types-perl libnet-ssleay-perl
  linux-backports-modules-2.6.28-12-generic python-xmmsclient nspluginwrapper
  gstreamer0.10-plugins-farsight python-openssl libsvga1 libossp-uuid-perl
  libqt4-test libboost-date-time1.34.1 libgstfarsight0.10-0 libmime-tools-perl
  libjinglexmllite0.3-0 libfcgi-perl python-msn libnet-google-perl
  python-soappy blt python-tk libsoap-lite-perl python-fpconst libggi2 libgii1
  libboost-thread1.34.1 libjinglebase0.3-0 libgii1-target-x libwww-search-perl
  libemail-date-format-perl libuser-perl libjcode-pm-perl libggi-target-x
  libnet-libidn-perl libnice0 gstreamer0.10-nice libconvert-binhex-perl
  libio-socket-ssl-perl libossp-uuid15 libmime-lite-perl python-crypto
  libjinglexmpp0.3-0 python-numeric
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  freeglut3 libdigest-sha1-perl liberror-perl libgpac0.4.4 libwxbase2.6-0
  libwxgtk2.6-0
Suggested packages:
  git-doc git-arch git-cvs git-svn git-email git-daemon-run git-gui gitk
  gitweb
The following NEW packages will be installed
  freeglut3 git-core gpac libdigest-sha1-perl liberror-perl libgpac-dev
  libgpac0.4.4 libwxbase2.6-0 libwxgtk2.6-0 yasm
0 upgraded, 10 newly installed, 0 to remove and 49 not upgraded.
1 not fully installed or removed.
Need to get 12.5MB of archives.
After this operation, 33.7MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get: 1 http://gb.archive.ubuntu.com jaunty/main freeglut3 2.4.0-6.1ubuntu1 [98.9kB]
Get: 2 http://gb.archive.ubuntu.com jaunty/main liberror-perl 0.17-1 [23.8kB]
Get: 3 http://gb.archive.ubuntu.com jaunty/main libdigest-sha1-perl 2.11-2build2 [26.4kB]
Get: 4 http://gb.archive.ubuntu.com jaunty/main git-core 1:1.6.0.4-1ubuntu2 [4733kB]
Get: 5 http://gb.archive.ubuntu.com jaunty/multiverse libgpac0.4.4 0.4.4-0.3ubuntu4 [1140kB]
Get: 6 http://gb.archive.ubuntu.com jaunty/universe libwxbase2.6-0 2.6.3.2.2-3ubuntu4 [546kB]
Get: 7 http://gb.archive.ubuntu.com jaunty/universe libwxgtk2.6-0 2.6.3.2.2-3ubuntu4 [2840kB]
Get: 8 http://gb.archive.ubuntu.com jaunty/multiverse gpac 0.4.4-0.3ubuntu4 [739kB]
Get: 9 http://gb.archive.ubuntu.com jaunty/multiverse libgpac-dev 0.4.4-0.3ubuntu4 [1710kB]
Get: 10 http://gb.archive.ubuntu.com jaunty/universe yasm 0.7.1-0ubuntu2 [599kB]
Fetched 12.5MB in 1s (6302kB/s)
Selecting previously deselected package freeglut3.
(Reading database ... 
[COLOR="#ff0000"]dpkg: serious warning: files list file for package `linux-image-2.6.30-candela' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `linux-image-2.6.30-red' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `linux-headers-2.6.30-candela' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `linux-headers-2.6.30-red' missing, assuming package has no files currently installed.
244542 files and directories currently installed.)[/COLOR]
Unpacking freeglut3 (from .../freeglut3_2.4.0-6.1ubuntu1_amd64.deb) ...
Selecting previously deselected package liberror-perl.
Unpacking liberror-perl (from .../liberror-perl_0.17-1_all.deb) ...
Selecting previously deselected package libdigest-sha1-perl.
Unpacking libdigest-sha1-perl (from .../libdigest-sha1-perl_2.11-2build2_amd64.deb) ...
Selecting previously deselected package git-core.
Unpacking git-core (from .../git-core_1%3a1.6.0.4-1ubuntu2_amd64.deb) ...
Selecting previously deselected package libgpac0.4.4.
Unpacking libgpac0.4.4 (from .../libgpac0.4.4_0.4.4-0.3ubuntu4_amd64.deb) ...
Selecting previously deselected package libwxbase2.6-0.
Unpacking libwxbase2.6-0 (from .../libwxbase2.6-0_2.6.3.2.2-3ubuntu4_amd64.deb) ...
Selecting previously deselected package libwxgtk2.6-0.
Unpacking libwxgtk2.6-0 (from .../libwxgtk2.6-0_2.6.3.2.2-3ubuntu4_amd64.deb) ...
Selecting previously deselected package gpac.
Unpacking gpac (from .../gpac_0.4.4-0.3ubuntu4_amd64.deb) ...
Selecting previously deselected package libgpac-dev.
Unpacking libgpac-dev (from .../libgpac-dev_0.4.4-0.3ubuntu4_amd64.deb) ...
Selecting previously deselected package yasm.
Unpacking yasm (from .../yasm_0.7.1-0ubuntu2_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for menu ...
[COLOR="#ff0000"]Setting up linux-image-2.6.30.1-azure (386) ...
Running depmod.
Finding valid ramdisk creators.
Using mkinitramfs-kpkg to build the ramdisk.
initrd.img(/boot/initrd.img-2.6.30.1-azure
) points to /boot/initrd.img-2.6.30.1-azure
 (/boot/initrd.img-2.6.30.1-azure) -- doing nothing at /var/lib/dpkg/info/linux-image-2.6.30.1-azure.postinst line 588.
vmlinuz(/boot/vmlinuz-2.6.30.1-azure
) points to /boot/vmlinuz-2.6.30.1-azure
 (/boot/vmlinuz-2.6.30.1-azure) -- doing nothing at /var/lib/dpkg/info/linux-image-2.6.30.1-azure.postinst line 588.
Running postinst hook script update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.30.1-azure
Found kernel: /boot/vmlinuz-2.6.30.1
Found kernel: /boot/vmlinuz-2.6.30-0814
Found kernel: /boot/vmlinuz-2.6.30
Found kernel: /boot/vmlinuz-2.6.28-12-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
run-parts: executing /etc/kernel/postinst.d/nvidia-common
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 20
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.30.1-azure.postinst line 1186.
dpkg: error processing linux-image-2.6.30.1-azure (--configure):
 subprocess post-installation script returned error exit status 2[/COLOR]
Setting up freeglut3 (2.4.0-6.1ubuntu1) ...

Setting up liberror-perl (0.17-1) ...
Setting up libdigest-sha1-perl (2.11-2build2) ...
Setting up git-core (1:1.6.0.4-1ubuntu2) ...
Setting up yasm (0.7.1-0ubuntu2) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Processing triggers for menu ...
[COLOR="Red"]Errors were encountered while processing:
 linux-image-2.6.30.1-azure
E: Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR]

```

looks like the new kernel you have compiled doesnt done successfully , u should :
1.apt-get purge the_last_kernel_u_have_compiled
2.do " mv /etc/kernel/postinst.d/nvidia-common  /tmp   "
3.install again the .deb linux image you have made

same problem happen to me, after did that it solve all my problem

---

### Post by Lockheed on 2009-09-08
I did some random purging and cleaning of old kernels remnants and that solved my problem.

---

