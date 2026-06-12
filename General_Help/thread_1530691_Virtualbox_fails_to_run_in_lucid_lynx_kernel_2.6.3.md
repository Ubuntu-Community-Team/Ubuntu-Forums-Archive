---
title: "Virtualbox fails to run in lucid lynx kernel 2.6.32.24"
date: 2010-07-14
forum: General Help
---

### Post by kentechy on 2010-07-14
I am running Lucid Lynx kernel 2.6.32.24.  Soon after the latest kernel update I noticed that Virtualbox would not launch when I clicked on the icon.  I have searched the Internet for days, tried numerous possible fixes, over hours of effort, but can't get it working at all.  Ubuntu Lucid runs great!!  There are no errors just a few blinks of the hard drive indicator and nothing.  Is there anyone out there that has seen this same issue?  Thanks very much...  :neutral:

---

### Post by CharlesA on 2010-07-14
How did you install VirtualBox?

---

### Post by kentechy on 2010-07-14
I tried 2 ways, manually in Terminal, and with Synaptic.  I tried an older version as well.  So, I tried Sun 3.1 and now Oracle 3.2 versions.  Prior to this it worked great and XP ran fine inside VB.

---

### Post by CharlesA on 2010-07-14
Running the open source version then?

---

### Post by kentechy on 2010-07-14
> **CharlesA said:**
> Running the open source version then?

I tried the OS but now I am running Oracle 3.2.6-63112 VM Virtualbox.  I tried all kinds of things.  Removing all and re-installing, etc...

---

### Post by CharlesA on 2010-07-14
Is it spitting out any errors if you run it from a terminal?

---

### Post by kentechy on 2010-07-14
> **CharlesA said:**
> Is it spitting out any errors if you run it from a terminal?

Please remind me of the command to start Virtualbox.  I am not very swift in the command line stuff... Thanks

---

### Post by CharlesA on 2010-07-14
It should be this:

```
VirtualBox
```

---

### Post by kentechy on 2010-07-14
> **CharlesA said:**
> It should be this:

```
VirtualBox
```

That's what I thought I tried with and without caps and I get this response:

No command 'Virtualbox' found, did you mean:
 Command 'virtualbox' from package 'virtualbox-ose-qt' (universe)
Virtualbox: command not found
ken@kenslaptop:~$ virtualbox
The program 'virtualbox' is currently not installed.  You can install it by typing:
sudo apt-get install virtualbox-ose-qt

---

### Post by JustinR on 2010-07-14
The Command is

```

Virtual**B**ox

```

---

### Post by kentechy on 2010-07-14
> **JustinR said:**
> The Command is

```

Virtual**B**ox

```

OK, I got this:

ken@kenslaptop:~$ VirtualBox
VirtualBox: supR3HardenedMainGetTrustedMain: dlopen("/usr/lib/virtualbox/VirtualBox.so",) failed: libfusion-1.0.so.0: cannot open shared object file: No such file or directory

But it is showing it to be installed in Synaptic.

---

### Post by CharlesA on 2010-07-14
Hrm. try puring it with apt-get.

```
sudo apt-get purge virtualbox-3.2
```

---

### Post by kentechy on 2010-07-14
> **CharlesA said:**
> It's case sensitive. The V and B are capiolized.


Yes, I got this:

ken@kenslaptop:~$ VirtualBox
VirtualBox: supR3HardenedMainGetTrustedMain: dlopen("/usr/lib/virtualbox/VirtualBox.so",) failed: libfusion-1.0.so.0: cannot open shared object file: No such file or directory

---

### Post by CharlesA on 2010-07-14
Only thing I can think of doing is purging it and reinstalling VirtualBox.

---

### Post by JustinR on 2010-07-14
> **kentechy said:**
> Yes, I got this:

ken@kenslaptop:~$ VirtualBox
VirtualBox: supR3HardenedMainGetTrustedMain: dlopen("/usr/lib/virtualbox/VirtualBox.so",) failed: libfusion-1.0.so.0: cannot open shared object file: No such file or directory

Type this into a terminal:

```

locate libfusion

```

and post the results.

---

### Post by kentechy on 2010-07-14
> **CharlesA said:**
> Only thing I can think of doing is purging it and reinstalling VirtualBox.

I saw some things about purging but never found them again.  Is that going to destroy my XP installation I had in VirtualBox?  Not that I use it much but it would be nice to not have to install it again.

---

### Post by CharlesA on 2010-07-14
I don't think it removes the hard drive images, just the config files.

---

### Post by kentechy on 2010-07-14
> **JustinR said:**
> Type this into a terminal:

```

locate libfusion

```and post the results.

Got this:

ken@kenslaptop:~$ locate libfusion
/home/ken/google-earth/libfusioncommon.so
/usr/lib/libfusion-1.2.so.0
/usr/lib/libfusion-1.2.so.0.8.0
/usr/lib/libfusion.a
/usr/lib/libfusion.so
ken@kenslaptop:~$

---

### Post by kentechy on 2010-07-14
> **CharlesA said:**
> I don't think it removes the hard drive images, just the config files.

Can you give me the information on how to step through the "purge" and I will check this tomorrow.  Got to hit the hay as I am teaching a class tomorrow...Thanks.

---

### Post by JustinR on 2010-07-14
> **kentechy said:**
> Got this:

ken@kenslaptop:~$ locate libfusion
/home/ken/google-earth/libfusioncommon.so
/usr/lib/libfusion-1.2.so.0
/usr/lib/libfusion-1.2.so.0.8.0
/usr/lib/libfusion.a
/usr/lib/libfusion.so
ken@kenslaptop:~$

Okay, you could try what this person did: [http://ubuntuforums.org/showthread.php?t=1479950](http://ubuntuforums.org/showthread.php?t=1479950)

Basically, he did this:

Go into a terminal type:
```

gksudo nautilus /usr/lib

```

Find the file "libfusion-1.2.so.0". Click and drag it while holding the ALT key, (like moving a file except holding ALT) make sure the file is still in the same folder. Let go of the mouse button and a menu will pop up and press "Link Here". It will create a link to this file in the /usr/lib folder. Now rename the new file to "libfusion-1.0.so.0". Restart VirtualBox and see if it works.

---

### Post by kentechy on 2010-07-14
> **JustinR said:**
> Okay, you could try what this person did: [http://ubuntuforums.org/showthread.php?t=1479950](http://ubuntuforums.org/showthread.php?t=1479950)

Basically, he did this:

Go into a terminal type:
```

gksudo nautilus /usr/lib

```Find the file "libfusion-1.2.so.0". Click and drag it while holding the ALT key and press "Link Here". It will create a link to this file. Now rename the new file to "libfusion-1.0.so.0".


Thanks you guys!!  Off to catch some zzzzzzzzzz so I can think tomorrow.  I will check back tomorrow and give your ideas a shot.  Take care...  Ubuntu is cool!!

---

### Post by Bradleypit on 2010-07-14
Hi Mate

 Acoording to my view Virtualbox will not run with the kernel update As i faced this issue and changed the settings of virtual box

---

### Post by kentechy on 2010-07-14
> **Bradleypit said:**
> Hi Mate

 Acoording to my view Virtualbox will not run with the kernel update As i faced this issue and changed the settings of virtual box

I saw some information about exactly what you are saying.  I will be back tomorrow and try some things, thanks.

---

### Post by sinteq on 2010-07-14
I have seen this thread and I'll ask something there although I haven't got same problem. I use Oracle VirtualBox 3.2 on Lucid Lynx. Yesterday I have updated kernel to version 2.6.32.24 and now VirtualBox won't run anymore. 
When I open it and try to start a virtual machine it says:
> WARNING: The vboxdrv kernel module is not loaded. Either there is no module
         available for the current kernel (2.6.32-24-generic) or it failed to
         load. Please recompile the kernel module and install it by

           sudo /etc/init.d/vboxdrv setup

         You will not be able to start VMs until this problem is fixed.

Then I run that command, but it executes with an error: * > Stopping VirtualBox kernel module                                             *  done.
 * Recompiling VirtualBox kernel module                                         
 * Look at /var/log/vbox-install.log to find out what went wrong

And this is content of log file:
> Attempting to install using DKMS
  removing old DKMS module vboxdrv version  3.2.6
dkms.conf: Error! No 'DEST_MODULE_LOCATION' directive specified.
dkms.conf: Error! No 'PACKAGE_NAME' directive specified.
dkms.conf: Error! No 'PACKAGE_VERSION' directive specified.
dkms.conf: Error! No 'DEST_MODULE_LOCATION' directive specified.
dkms.conf: Error! No 'PACKAGE_NAME' directive specified.
dkms.conf: Error! No 'PACKAGE_VERSION' directive specified.

------------------------------
Deleting module version: 3.2.6
completely from the DKMS tree.
------------------------------
Done.
  removing old DKMS module vboxdrv version  3.2.4
dkms.conf: Error! No 'DEST_MODULE_LOCATION' directive specified.
dkms.conf: Error! No 'PACKAGE_NAME' directive specified.
dkms.conf: Error! No 'PACKAGE_VERSION' directive specified.

Error! Bad conf file.
File: /var/lib/dkms/vboxdrv/3.2.4/source/dkms.conf does not represent
a valid dkms.conf file.
  removing old DKMS module vboxdrv version  3.2.4
dkms.conf: Error! No 'DEST_MODULE_LOCATION' directive specified.
dkms.conf: Error! No 'PACKAGE_NAME' directive specified.
dkms.conf: Error! No 'PACKAGE_VERSION' directive specified.

Error! Bad conf file.
File: /var/lib/dkms/vboxdrv/3.2.4/source/dkms.conf does not represent
a valid dkms.conf file.

Creating symlink /var/lib/dkms/vboxdrv/3.2.6/source ->
                 /usr/src/vboxdrv-3.2.6

DKMS: add Completed.

Error! Your kernel headers for kernel 2.6.32-24-generic cannot be found at
/lib/modules/2.6.32-24-generic/build or /lib/modules/2.6.32-24-generic/source.
You can use the --kernelsourcedir option to tell DKMS where it's located, or you could install the linux-headers-2.6.32-24-generic package.
Failed to install using DKMS, attempting to install without
Makefile:159: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.


Help much appreciated.

Edit: 
I don't know, why it would compile /var/lib/dkms/vboxdrv/3.2.4/ if I use version 3.2.6

---

### Post by kentechy on 2010-07-14
> **Bradleypit said:**
> Hi Mate

 Acoording to my view Virtualbox will not run with the kernel update As i faced this issue and changed the settings of virtual box

If VirtualBox not running is a Kernel issue, when will there be a fix?

---

### Post by JustinR on 2010-07-15
If its still not working for you then its not a kernel issue but a VirtualBox issue with the new kernel.

---

### Post by kentechy on 2010-07-15
> **JustinR said:**
> If its still not working for you then its not a kernel issue but a VirtualBox issue with the new kernel.

I tried some things like the Sun version then the Oracle version.  I did a purge, removal, and re-install.  I get no errors from trying to launch it from the icon or Terminal.  Everything else works perfect in my Lucid install.  Strange.  I guess I will wait a few weeks and try it again.  I think I have had more problems with Lucid than any previous versions, over the last couple of years but it also has some great things.  After using XP at work all day it is refreshing to come home and kick on Ubuntu....Thanks for trying.

---

### Post by Operan on 2010-07-15
> **sinteq said:**
> I have seen this thread and I'll ask something there although I haven't got same problem. I use Oracle VirtualBox 3.2 on Lucid Lynx. Yesterday I have updated kernel to version 2.6.32.24 and now VirtualBox won't run anymore. 
When I open it and try to start a virtual machine it says:

Then I run that command, but it executes with an error: * 

And this is content of log file:


Help much appreciated.

Edit: 
I don't know, why it would compile /var/lib/dkms/vboxdrv/3.2.4/ if I use version 3.2.6

I got the same issue. I also tried VMware Player. When first run, VP ask me to locate kernel header (It said that kernel headers 2.6.32-24 not found though I installed it.) I tried /usr/src/linux-headers-2.6.32-24-generic, /usr/src/linux-headers-2.6.32-24-generic/kernel, /usr/src/linux-headers-2.6.32-24, /usr/src/linux-headers-2.6.32-24/kernel but nothing worked. Something wrong with new kernel?

---

### Post by Irony on 2010-07-15
I assume you have the virtualbox dkms thing installed in synaptic otherwise virtualbox won't recompile on a kernel update.

Note uninstalling and reinstalling virtualbox won't affect your windows install - you can go to your .vdi file and make a copy of it to an external drive just to be sure (you should do this anyway).

---

### Post by slooksterpsv on 2010-07-23
Ok, so I just updated to the latest kernel and Virtualbox works fine for me. It boots vms and everything. I used the installation deb off of [http://virtualbox.org/](http://virtualbox.org/) instead of synaptic.

---

### Post by CharlesA on 2010-07-24
Just upgraded to 2.6.32-24-server kernel and the only thing I had to do was run this:

```
sudo /etc/init.d/vboxdrv setup
```

To recompile the VBox kernel modules, after that Virtualbox worked fine.

I am using the deb from virtualbox.org, not the OSE.

---

### Post by kat_ams on 2010-07-31
I opened a bug report here:

[https://bugs.launchpad.net/ubuntu/+source/dkms/+bug/600517](https://bugs.launchpad.net/ubuntu/+source/dkms/+bug/600517)

With a workaround in it.

Please add an affects you if you are experiencing the same issue.

do a 

dkms status

and look for error messages in the vboxdrv

---

### Post by kentechy on 2010-08-05
I finally found a fix for my Virtualbox not starting properly.  See link and follow JBB instructions:

The problem is that the release was compiled using a set of libraries  which have been replaced on Ubuntu 10.04 (latest updates).  To fix, su  to root and issue the following commands:

cd /usr/lib
ln -s libdirectfb-1.2.so.0 libdirectfb-1.0.so.0
ln -s libfusion-1.2.so.0.8.0 libfusion-1.0.so.0
ln -s libdirect.so libdirect-1.0.so.0

These commands will create symbolic links for the missing libraries.

Hope this helps.



JBB  :p

---

### Post by FrankyG on 2010-09-07
Thanks kentecky, this worked it around for me as well. 

Symlinks for lines #1 and #3 were already present on my system (lucid with kernel 2.6.32-24-generic #42-Ubuntu SMP), so I only had to issue the second line like so:

```
$cd /usr/lib
$sudo ln -s libfusion-1.2.so.0.8.0 libfusion-1.0.so.0
```My VirtualBox ( 3.1.6_OSE r59338 ) is up and running again! \\:D/

---

