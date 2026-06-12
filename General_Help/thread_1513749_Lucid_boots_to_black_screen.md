---
title: "Lucid boots to black screen"
date: 2010-06-20
forum: General Help
---

### Post by jxtreme on 2010-06-20
So I've been using Ubuntu for about a month now. Everything is great and all but today when I booted into Ubuntu everything was going well--the splash screen appeared and the dots were doing their thing and all--but then there was just a blank screen. Some people have had this problem after a fresh install of Lucid, but its been working for a while so I don't get why it isn't working... I didn't do anything to the system except run some updates before I turned off the computer. Anyone have any ideas?

---

### Post by wilee-nilee on 2010-06-20
Could be any number of problems but the first suspect is the graphic chip/card drivers. When you boot the computer hit the e key for edit then with the arrow keys get to the end of the kernel and put in nomodset and remove the splash, then hold down the ctrl key and hit x to boot from there.

This will only get you in and you will have to look at your updates in synaptic history and the drivers for the card. If you get in run this to identify the graphic chip/card.
```
lspci | grep VGA
```

---

### Post by jxtreme on 2010-06-20
> **wilee-nilee said:**
> Could be any number of problems but the first suspect is the graphic chip/card drivers. When you boot the computer hit the e key for edit then with the arrow keys get to the end of the kernel and put in nomodset and remove the splash, then hold down the ctrl key and hit x to boot from there.

This will only get you in and you will have to look at your updates in synaptic history and the drivers for the card. If you get in run this to identify the graphic chip/card.
```
lspci | grep VGA
```
That didn't work. I think I rember something having to do with fglrfx (I'm using the ATI proprietary driver) was updated. Could I boot into recocvery mode and run some commands in the terminal to uninstall the driver?

---

### Post by Drumber on 2010-06-20
> **jxtreme said:**
> So I've been using Ubuntu for about a month now. Everything is great and all but today when I booted into Ubuntu everything was going well--the splash screen appeared and the dots were doing their thing and all--but then there was just a blank screen. Some people have had this problem after a fresh install of Lucid, but its been working for a while so I don't get why it isn't working... I didn't do anything to the system except run some updates before I turned off the computer. Anyone have any ideas?

I'm having this exact problem, I updated my system and after a few minutes everything went black. Now when I boot into ubuntu I see exactly what you described. I am also using an ATI card.

---

### Post by t1nm@n on 2010-06-20
[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

there was a sticky started for lucid in the forums... use this link to get it done..

~t1nm@n:p

---

### Post by jxtreme on 2010-06-20
> **t1nm@n said:**
> [http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

there was a sticky started for lucid in the forums... use this link to get it done..

~t1nm@n:p
I did that awhile back when I first installed Lucid. My splash screen is fine, I'm having problems with a black screen after that.
> I'm having this exact problem, I updated my system and after a few  minutes everything went black. Now when I boot into ubuntu I see exactly  what you described. I am also using an ATI card.That pretty much confirms for me that it was the updates. Were you using the proprietary driver? I now see that ATI has released a new version, 10.6. I was previously using 10.5. You can't even download 10.5 anymore.

EDIT:Booted in graphics failsafe mode, output of lspci | grep VGA is
```
01:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]
```Nothing I didn't already know.

EDIT 2:
Okay, seems I accidentally uninstalled ubuntu-desktop and update-notifier the day before I updated, so that can't be good. Reinstalled. Here's what was updated:
```
Commit Log for Sat Jun 19 12:04:27 2010


Upgraded the following packages:
evolution (2.28.3-0ubuntu9) to 2.28.3-0ubuntu10
evolution-common (2.28.3-0ubuntu9) to 2.28.3-0ubuntu10
evolution-data-server (2.28.3.1-0ubuntu2) to 2.28.3.1-0ubuntu3
evolution-data-server-common (2.28.3.1-0ubuntu2) to 2.28.3.1-0ubuntu3
evolution-plugins (2.28.3-0ubuntu9) to 2.28.3-0ubuntu10
**fglrx-modaliases (2:8.723.1-0ubuntu3) to 2:8.723.1-0ubuntu4**
gstreamer0.10-plugins-good (0.10.21-1ubuntu2) to 0.10.21-1ubuntu3
gstreamer0.10-plugins-ugly-multiverse (0.10.14-0ubuntu1) to 0.10.14-0ubuntu2
gstreamer0.10-pulseaudio (0.10.21-1ubuntu2) to 0.10.21-1ubuntu3
libcamel1.2-14 (2.28.3.1-0ubuntu2) to 2.28.3.1-0ubuntu3
libebackend1.2-0 (2.28.3.1-0ubuntu2) to 2.28.3.1-0ubuntu3
libebook1.2-9 (2.28.3.1-0ubuntu2) to 2.28.3.1-0ubuntu3
libecal1.2-7 (2.28.3.1-0ubuntu2) to 2.28.3.1-0ubuntu3
libedata-book1.2-2 (2.28.3.1-0ubuntu2) to 2.28.3.1-0ubuntu3
libedata-cal1.2-6 (2.28.3.1-0ubuntu2) to 2.28.3.1-0ubuntu3
libedataserver1.2-11 (2.28.3.1-0ubuntu2) to 2.28.3.1-0ubuntu3
libedataserverui1.2-8 (2.28.3.1-0ubuntu2) to 2.28.3.1-0ubuntu3
libegroupwise1.2-13 (2.28.3.1-0ubuntu2) to 2.28.3.1-0ubuntu3
libexchange-storage1.2-3 (2.28.3.1-0ubuntu2) to 2.28.3.1-0ubuntu3
libgdata-google1.2-1 (2.28.3.1-0ubuntu2) to 2.28.3.1-0ubuntu3
libgdata1.2-1 (2.28.3.1-0ubuntu2) to 2.28.3.1-0ubuntu3
libgnomekbd-common (2.30.0-0ubuntu2) to 2.30.1-0ubuntu1
libgnomekbd4 (2.30.0-0ubuntu2) to 2.30.1-0ubuntu1
libgssapi-krb5-2 (1.8.1+dfsg-2) to 1.8.1+dfsg-2ubuntu0.1
libido-0.1-0 (0.1.5-0ubuntu1) to 0.1.6-0ubuntu1
libk5crypto3 (1.8.1+dfsg-2) to 1.8.1+dfsg-2ubuntu0.1
libkrb5-3 (1.8.1+dfsg-2) to 1.8.1+dfsg-2ubuntu0.1
libkrb5support0 (1.8.1+dfsg-2) to 1.8.1+dfsg-2ubuntu0.1
libpoppler-glib4 (0.12.4-0ubuntu4) to 0.12.4-0ubuntu5
libpoppler5 (0.12.4-0ubuntu4) to 0.12.4-0ubuntu5
libsdl1.2debian (1.2.14-4ubuntu1) to 1.2.14-4ubuntu1.1
libsdl1.2debian-pulseaudio (1.2.14-4ubuntu1) to 1.2.14-4ubuntu1.1
**nvidia-current-modaliases (195.36.15-0ubuntu3) to 195.36.24-0ubuntu1~10.04**
poppler-utils (0.12.4-0ubuntu4) to 0.12.4-0ubuntu5
software-center (2.0.4) to 2.0.5
telepathy-butterfly (0.5.9-0ubuntu1) to 0.5.11-0ubuntu1
udisks (1.0.1-1build1) to 1.0.1-1ubuntu1
[B]xserver-common (2:1.7.6-2ubuntu7) to 2:1.7.6-2ubuntu7.1
xserver-xephyr (2:1.7.6-2ubuntu7) to 2:1.7.6-2ubuntu7.1
xserver-xorg-core (2:1.7.6-2ubuntu7) to 2:1.7.6-2ubuntu7.1[/B]
```Notice the bold text. But I don't have a nvidia card!? Whatever.

---

### Post by Drumber on 2010-06-20
> **jxtreme said:**
> I did that awhile back when I first installed Lucid. My splash screen is fine, I'm having problems with a black screen after that.
That pretty much confirms for me that it was the updates. Were you using the proprietary driver? I now see that ATI has released a new version, 10.6. I was previously using 10.5. You can't even download 10.5 anymore.

EDIT:Booted in graphics failsafe mode, output of lspci | grep VGA is
```
01:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]
```Nothing I didn't already know.

I am using the driver from the ATI website. I get the same output of  lspci | grep (but 3650, not 4500). Doesn't really help me much.

---

### Post by jxtreme on 2010-06-20
> **Drumber said:**
> I am using the driver from the ATI website. I get the same output of  lspci | grep (but 3650, not 4500). Doesn't really help me much.
Look at your Synaptic update history. What was updated?

---

### Post by t1nm@n on 2010-06-20
i wanted you to completely read the post in softpedia... see the user opinions...
they already said stuff about ATi card drivers.. heres one

Comment  #4 by: **bg76x** on 01 May 2010, 18:52 GMT[IMG]http://news.softpedia.com/_img/generic/message_16.gif[/IMG] [reply to this comment]("http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml#add_review_form")If you follow alt 2, you will NOT be able to use suspend  if you are using the ATI drivers!
it states that in the ubuntu launch pad. 
[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/553854](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/553854)

see this ..it ain't much... post back if you find anything.... the update was including the xvideo-driver...you know the openGl driver (i think)... post back if you have success.

i also found this
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by Drumber on 2010-06-20
> **jxtreme said:**
> Look at your Synaptic update history. What was updated?

Ok, how do I do that?

---

### Post by jxtreme on 2010-06-20
I'm in! Uninstalled the driver from failsafe graphics mode, will try to reinstall and see how it goes. To uninstall:
```
cd /usr/share/ati
sudo sh ./fglrx-uninstall.sh
```EDIT: Probably doesn't matter now, but to view your history, go to System>Administration>Synaptic Package Manager. You will be asked for your default keyring password. In Synaptic, go to File>History.

---

### Post by ep1centre on 2010-06-20
I too am having the same sort of problem, the computer was working fine last night, when i woke up this morning (i leave it on) it was making strange noises through the speakers and i had a blank screen, restarted a few times had some page full of code and wouldnt move on from there, i went out came back started it up and it did everything normally exept instead of a desktop i had a black screen, however strangely enough when i press the power button on the PC a shut down menu comes up, and the mouse works and i can select from the options.

I am on an Nvidia ION tho...

how do i boot into a safe mode as such? as at the moment i'm using a ubuntu live CD to read the forums!

---

### Post by Drumber on 2010-06-20
> **jxtreme said:**
> I'm in! Uninstalled the driver from failsafe graphics mode, will try to reinstall and see how it goes. To uninstall:
```
cd /usr/share/ati
sudo sh ./fglrx-uninstall.sh
```EDIT: Probably doesn't matter now, but to view your history, go to System>Administration>Synaptic Package Manager. You will be asked for your default keyring password. In Synaptic, go to File>History.

I could only get to the command line, and not into the GUI. But I tried recovery mode from GRUB, and then failsafe graphics mode. I got the message:

```
You screen, graphic card, and input device settings could not be detected correctly. You will need to configure these yourself.
```So I select the option to reconfigure, and choose default configuration and then run ubuntu. So I managed to get into my ubuntu now. Synaptic history is:

```
Commit Log for Sun Jun 20 12:34:02 2010


Upgraded the following packages:
evolution (2.28.3-0ubuntu9) to 2.28.3-0ubuntu10
evolution-common (2.28.3-0ubuntu9) to 2.28.3-0ubuntu10
evolution-data-server (2.28.3.1-0ubuntu2) to 2.28.3.1-0ubuntu3
evolution-data-server-common (2.28.3.1-0ubuntu2) to 2.28.3.1-0ubuntu3
evolution-plugins (2.28.3-0ubuntu9) to 2.28.3-0ubuntu10
fglrx-modaliases (2:8.723.1-0ubuntu3) to 2:8.723.1-0ubuntu4
gstreamer0.10-plugins-good (0.10.21-1ubuntu2) to 0.10.21-1ubuntu3
gstreamer0.10-plugins-ugly-multiverse (0.10.14-0ubuntu1) to 0.10.14-0ubuntu2
gstreamer0.10-pulseaudio (0.10.21-1ubuntu2) to 0.10.21-1ubuntu3
kdepimlibs-data (4:4.4.2-0ubuntu2) to 4:4.4.2-0ubuntu2.1
kdepimlibs5 (4:4.4.2-0ubuntu2) to 4:4.4.2-0ubuntu2.1
kpackagekit (0.5.4-0ubuntu4) to 0.5.4-0ubuntu4.1
libcamel1.2-14 (2.28.3.1-0ubuntu2) to 2.28.3.1-0ubuntu3
libebackend1.2-0 (2.28.3.1-0ubuntu2) to 2.28.3.1-0ubuntu3
libebook1.2-9 (2.28.3.1-0ubuntu2) to 2.28.3.1-0ubuntu3
libecal1.2-7 (2.28.3.1-0ubuntu2) to 2.28.3.1-0ubuntu3
libedata-book1.2-2 (2.28.3.1-0ubuntu2) to 2.28.3.1-0ubuntu3
libedata-cal1.2-6 (2.28.3.1-0ubuntu2) to 2.28.3.1-0ubuntu3
libedataserver1.2-11 (2.28.3.1-0ubuntu2) to 2.28.3.1-0ubuntu3
libedataserverui1.2-8 (2.28.3.1-0ubuntu2) to 2.28.3.1-0ubuntu3
libegroupwise1.2-13 (2.28.3.1-0ubuntu2) to 2.28.3.1-0ubuntu3
libexchange-storage1.2-3 (2.28.3.1-0ubuntu2) to 2.28.3.1-0ubuntu3
libgdata-google1.2-1 (2.28.3.1-0ubuntu2) to 2.28.3.1-0ubuntu3
libgdata1.2-1 (2.28.3.1-0ubuntu2) to 2.28.3.1-0ubuntu3
libgnomekbd-common (2.30.0-0ubuntu2) to 2.30.1-0ubuntu1
libgnomekbd4 (2.30.0-0ubuntu2) to 2.30.1-0ubuntu1
libgssapi-krb5-2 (1.8.1+dfsg-2) to 1.8.1+dfsg-2ubuntu0.1
libido-0.1-0 (0.1.5-0ubuntu1) to 0.1.6-0ubuntu1
libk5crypto3 (1.8.1+dfsg-2) to 1.8.1+dfsg-2ubuntu0.1
libkrb5-3 (1.8.1+dfsg-2) to 1.8.1+dfsg-2ubuntu0.1
libkrb5support0 (1.8.1+dfsg-2) to 1.8.1+dfsg-2ubuntu0.1
libpoppler-glib4 (0.12.4-0ubuntu4) to 0.12.4-0ubuntu5
libpoppler5 (0.12.4-0ubuntu4) to 0.12.4-0ubuntu5
libsdl1.2debian (1.2.14-4ubuntu1) to 1.2.14-4ubuntu1.1
libsdl1.2debian-pulseaudio (1.2.14-4ubuntu1) to 1.2.14-4ubuntu1.1
nvidia-185-modaliases (195.36.15-0ubuntu3) to 195.36.24-0ubuntu1~10.04
nvidia-current-modaliases (195.36.15-0ubuntu3) to 195.36.24-0ubuntu1~10.04
poppler-utils (0.12.4-0ubuntu4) to 0.12.4-0ubuntu5
software-center (2.0.4) to 2.0.5
telepathy-butterfly (0.5.9-0ubuntu1) to 0.5.11-0ubuntu1
udisks (1.0.1-1build1) to 1.0.1-1ubuntu1
xserver-common (2:1.7.6-2ubuntu7) to 2:1.7.6-2ubuntu7.1
xserver-xorg-core (2:1.7.6-2ubuntu7) to 2:1.7.6-2ubuntu7.1

```I'll try what you suggested and report back.

EDIT: Woo-hoo! So that worked and now I'm back in my ubuntu, but without fancy graphics. Next question is how do I install ATI drivers without messing it up again...

---

### Post by jxtreme on 2010-06-20
> **ep1centre said:**
> I too am having the same sort of problem, the computer was working fine last night, when i woke up this morning (i leave it on) it was making strange noises through the speakers and i had a blank screen, restarted a few times had some page full of code and wouldnt move on from there, i went out came back started it up and it did everything normally exept instead of a desktop i had a black screen, however strangely enough when i press the power button on the PC a shut down menu comes up, and the mouse works and i can select from the options.

I am on an Nvidia ION tho...

how do i boot into a safe mode as such? as at the moment i'm using a ubuntu live CD to read the forums!
On the GRUB menu, seclect "Ubuntu (recovery mode)" (not exact wording). You'll get scrolling boot messages until you get to a screen with a grey box and some options. Use the arrow keys to select "x failsafe graphics mode" or something of the like. Press enter and you'll probably get a message that your card can't be detected or something. Press okay and continue. Your screen will be messed up, but you'll be in.

It probably isn't the same problem, as you don't have an ATI card and can see a shutdown menu, but good Luck!

---

### Post by ep1centre on 2010-06-20
How do you bring up the GRUB menu? My PC isnt dual booted so i never see any menus at all, i thought all i had to do was press F8 during boot up?

---

### Post by jxtreme on 2010-06-20
> **ep1centre said:**
> How do you bring up the GRUB menu? My PC isnt dual booted so i never see any menus at all, i thought all i had to do was press F8 during boot up?
No, F8 is Windows. Hold down shift when booting to see the menu.

EDIT: Downloaded & Installed the 10.6 driver and everything is working fine. Unminimizing apps works much faster with this driver :D. However, /usr/bin/aticonfig --initial results in 
```
Found fglrx primary device section
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-2
/usr/bin/aticonfig: Writing to '/etc/X11/xorg.conf' failed. Bad file descriptor.

``` However, this doesn't seem to affect anything. Problem solved. :cool:

---

