---
title: "Ubuntu 10.10 maverick startupmanager not launching?"
date: 2010-12-12
forum: General Help
---

### Post by gb210461 on 2010-12-12
Hi all

I have installed Ubuntu 10.10 Maverick Meerkat onto a USB stick. Booting up is fun but it does come up with a load of text and a blue menu screen that hangs around for 5 seconds and then loads up ok.

My challenge is to somehow customise the boot up process. For one I'd like to customise the options that are presented on the initial blue menu boot up screen and possibly to not show the back ground text that presents during the start up process.

I've googles about a bit and am aware that I need to be using startupmanager as the GUI customisation tool of choice. The trouble is that after installation startupmanager doesn't launch.

This is what I've done so far:

1. gone to [http://packages.ubunut.com/maverick/utils/startupmanager](http://packages.ubunut.com/maverick/utils/startupmanager) and downloaded the startupmanager (1.9.13-5) version of the package.

2. gone to [http://packages.ubunut.com/maverick/menu](http://packages.ubunut.com/maverick/menu) and downloaded the menu 2.1.44ubuntu1 as looking at the the pre-requisites for startupmanager this was the only one not already installed.

3. from a terminal window executed sudo dpkg -i <the previously downloaded startupmanager package>

4. from a terminal window executed sudo dpkg -i <the previously downloaded menu package>

5. Tried to launch it from the system\administration menu. Nothing obvious happened.

6. Created a shortcut of the startupmanager shortcut on the desktop and viewed the properties.

7. opened up a terminal windows and launch command su-to-root -X -c /usr/sbin/startupmanager which was originall shown within the startupmanager properties of the shortcut.

From this last terminal command I get the output as follows:

ubuntu@ubuntu:~$ su-to-root -X -c /usr/sbin/startupmanager
Grub2 detected
Usplash not detected
Splashy not detected
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).File /boot/grub/grub.cfg does not exist.
ubuntu@ubuntu:~$ 

The output from both the startmanager and menu installations were as follows:

ubuntu@ubuntu:~$  sudo dpkg -i menu_2.1.44ubuntu1_i386.deb
Selecting previously deselected package menu.
(Reading database ... 126640 files and directories currently installed.)
Unpacking menu (from menu_2.1.44ubuntu1_i386.deb) ...
Setting up menu (2.1.44ubuntu1) ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Processing triggers for doc-base ...
Processing 1 added doc-base file(s)...
Registering documents with scrollkeeper...
Processing triggers for menu ...
ubuntu@ubuntu:~$ sudo dpkg -i startupmanager_1.9.13-5_all.deb
Selecting previously deselected package startupmanager.
(Reading database ... 126821 files and directories currently installed.)
Unpacking startupmanager (from startupmanager_1.9.13-5_all.deb) ...
Setting up startupmanager (1.9.13-5) ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for man-db ...
Processing triggers for menu ...
Processing triggers for python-support ...

So the installations looked good.

Any ideas what's gone wrong?

Regards, Gary

---

### Post by ajgreeny on 2010-12-12
My goodness, you do things the hard way, don't you?

You can install startup-manager with synaptic (or software-center), and it will pull in all missing dependencies. 
Startup-manager does not do a great deal at the moment, but can be used to make a few configuration changes to the startup activities.

The blue menu is probably grub, though I don't remember it being blue by default in maverick.  The text you then see would normally not be shown; it should be the ubuntu purple screen with the word "ubuntu" and five animated dots beneath, which is plymouth.  Some systems have problems displaying this, but without knowing what your computer hardware is, it is difficult to say more.

What hardware do you have, particularly the graphics card?

---

### Post by gb210461 on 2010-12-12
Hi ... and thanks for the response.
 
What's the best way to provide the information that you require?
 
I see when I boot into a Windows OS that the graphics adaptor suggests 'Mobile Intel(R) 965 Express chipset family' if that helps.
 
Regards, Gary

---

### Post by gb210461 on 2010-12-12
... I know I'm relying to myself here but I've had a look around and am becoming a bit more familiar with the process and terms.

However mention was made by a respondent about what the boot up screens should look like. That got me thinking and I came across the following:
[FONT=monospace]
"[/FONT]Booting off the USB stick still drops me into Busybox. The boot menu still has the original five items".

This is what I maybe seeing as my system boots and not the screens that others are seeing who are using installations that are obviously working correctly.

1. Should I see this small blue menu with a few number of items on? The options range from booting into my unbuntu install, installing ubuntu, advanced options, booting from first hard drive and help.

2. How do I get ride of it for the correct bootup screen?

Any help would be much appreciated ....

Thanks, Gary

---

### Post by ajgreeny on 2010-12-12
That menu you describe only shows when running from a live CD or USB as far as I'm aware, and not from an installed version of Ubuntu.  I think, therefore that you have not installed but simply "burned" the iso file of ubuntu onto the USB, and are running a live system from that, not an installed version.

Can you give us more detail of what happens when you boot up the machine; do you always get that menu appear?

Also did you actually run the "Install ubuntu" from that menu, and if so where did you, or where do you think you installed the OS?

---

### Post by gb210461 on 2010-12-13
Hi ... and again thanks for the rsponse. I'm certainly getting there...
 
I see now that what I have isn't an install and that would explain the startup manager issue I was experiencing.
 
So my next question is how do I install ubuntu 10.10 onto a 4Gb USB stick with some available persistent memory? Is it possible?
 
I do recollect usinh the option 2 download from the ubuntu site and using the 'Create a USB drive'. From there I used unetbooting (or something sounding similar) to provide some persistent USB memory. All slightly wrong I'm now guessing?
 
Regards, Gary

---

### Post by ajgreeny on 2010-12-13
Yes, what you have at the moment is definitely a live USB version of Ubuntu.  You will need another USB drive to install to as a proper install, as I do not think it is possible to both run from, and install to the same USB drive, though if it were a larger drive it might perhaps be possible if you had a second large enough partition available;  4GB will not be big enough for that, however.

When you have another USB drive, just pick that as the drive to install to, using the whole drive with default settings, apart from using the Advanced button to make sure grub goes onto the USB install drive.  **Don't put grub on a partition** but choose **/dev/sdc** or **dev/sdb**, whichever is the drive you install to, rather than the one you are installing from, if you see what I mean.

---

