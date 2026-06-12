---
title: "Live instance of 12.04 hangs at install screen: &quot;b43/ucode5.fw&quot; not found"
date: 2012-04-27
forum: General Help
---

### Post by MorrisseyJ on 2012-04-27
Hi, 

I am having a problem trying to run live sessions of 12.04 (32 bit) and its different flavours (Lubuntu) on an asus A6RP with ATI Radeon Express 200M graphics.

When i boot to the live session (USB) i get to the screen with the distro logo and dots which change colour. At some point these dots stop changing colour and the machine hangs. If i set nomodeset i get the following error when the dots freeze.

> [    48.753669] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[    48.753687] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[    48.753698] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this site.This is the wireless driver which i have always installed using a wired connection once i've booted to the install. I am not sure why this is proving a problem while trying to run a live session (even when i am connected through a wired connection), nor what i am meant to do about it. Previously i have run a number of different distributions on the machine (currently Lubuntu 11.10 is installed and working) and have tested the USB on another machine and it works. 

From the website mentioned in the error message i am not sure what to do with the instructions 'toggle line numbers', as i am not sure of the file in which i am meant to be toggling them. I am also guessing, if its the case that I need to add a line saying: > sudo apt-get install firmware-b43-installer that i need to be connected to the internet on a wired connection while i try and boot to the live USB?

If anyone has any ideas about what i should try i'd love to hear them. Also if someone can tell me whether this is a bug, i'll file it as such.

Thanks,

---

### Post by MorrisseyJ on 2012-04-27
This looks like the problem:

[http://lists.infradead.org/pipermail/b43-dev/2012-March/002460.html](http://lists.infradead.org/pipermail/b43-dev/2012-March/002460.html)

But i am not sure what to do with it.

---

### Post by MorrisseyJ on 2012-04-27
Ah, found the bug report.

[https://bugs.launchpad.net/ubuntu/+source/b43-fwcutter/+bug/909871](https://bugs.launchpad.net/ubuntu/+source/b43-fwcutter/+bug/909871)

---

### Post by MorrisseyJ on 2012-04-27
Sorry, i actually can't work out how to follow the instructions in the bug report.

How do i blacklist b43 on the live session? All the instructions i can find describe doing so for an installed system, using the live session.

Thanks

---

### Post by Hubu on 2012-04-28
Hello.
Just solved that problem in very brutal way... 

You need your previous installation/backup with working wifi.
- You need to boot *ubuntu with b43.blacklist=yes parameter
- mount your backup or partition with previous installation
- simply copy firmware files to new system
sudo cp -r [old installation]/lib/firmware/b43 /lib/firmware/

Reboot and enjoy :)

---

### Post by MorrisseyJ on 2012-04-28
Thanks Hubu, 

I didn't have a backup so haven't tried your solution.

I did however get this working another way. So here is another detailed solution. It should work but you will need a wired internet connection.

First you need to blacklist b43 so that you can get into the live session.

1. Boot to the live CD/USB
2. When the screen comes up showing the accessibility icon (little stick man and keyboard at the bottom of the screen), press any key
3. Pick your language, press enter
4. Press F6, this will launch a dialogue
5. Press esc to get rid of the dialogue
6. You should now have a cursor from which you can enter commands below the boot options: Type > b43.blacklist=yes making sure there is a space before and after the text you enter.
7. Press enter to either 'Try Ubuntu without installing' or 'Install Ubuntu'

In the case of the former, above, your instance of the live session should now work.

Now you should be able to install Ubuntu but you will still need to install b43 onto your system so that you can boot normally and use your wireless. To do this you have to boot to your system to do the install, but before that will work you once again have to blacklist b43 in the boot process. Here are the instructions.

1. Boot to the grub screen. If grub doesn't load automatically press, and hold, the Shift key after the BIOS screen (the screen mentioning your machine's manufacturer) disappears.
2. At the grub screen (the purple screen which lets you choose the instance of the kernel you want) press 'e', this will bring up a screen of text.
3. Using the arrow keys, navigate to the line which ends with "vt.handoff" or something similar. At the end of that line enter > b43.blacklist=yes again making sure to leave spaces before and after.
4. Press F10

This should boot you to your install, but your wireless won't be working. To fix this we have to install b43 - this is where you'll need your wired internet connection.

1. Open a terminal (ctrl+alt+t or hit the 'super-key' (the one with the windows logo on it) and type 'terminal' and press enter).
2. Enter > sudo apt-get install firmware-b43-installer3. Enter your password (note your keystrokes won't register) and hit enter

Now b43 should install, your wireless should work and you should be able to boot without any problems. 

Thanks to different people who helped me sort this out. Also, here is a blog detailing much of what needs to be done and which helped me get this sorted: [http://linux-software-news-tutorials.blogspot.co.uk/2012/04/installing-ubuntu-1204-crashes-because.html](http://linux-software-news-tutorials.blogspot.co.uk/2012/04/installing-ubuntu-1204-crashes-because.html)

---

### Post by eodrobot on 2012-04-30
sudo apt-get install firmware-b43-installer" worked for me. I didn't see that b43 error. 

My (via Ubuntu update Mgr) upgrade from 11.10 to 12.04 was hanging on the boot screen - I'd tried everything else and followed the rather annoying Apport bug reporting procedure over and over - it seemed to be in a loop.

This, fyi, was on a Panasonic Toughbook. I have 12.04LTS on a USB hard drive (works faster than PC Windows hard drive) and was naturally upgrading from 12.04 beta, by which I mean I didn't do a fresh install, just update / upgrade from Update Manager. No hiccups with this one - the difference being maybe the PC is on ethernet cable - the laptop on WiFi

---

### Post by eodrobot on 2012-05-02
Thought I'd fixed it but the problem came back.

Inadequate work round was Ctrl Alt F2 - log in / password - Terminal command = sudo shutdown -r now

Select Recovery mode /fix broken packages/ - resume normal boot - 
may see partial desktop - terminal sudo apt-get update 

Then Apport messages

Answer anything to send bug report - Details  package "zenity" problem  - also saw Ubuntu 11.10 instead of 12.04

Get or open Synaptic - type in zenity - see Zenity and Zenity Common - mark for reinstallation / Apply

so far so good.

---

### Post by Flame_Phoenix on 2012-05-03
One thing you guys might find useful: After step 1 (after installation) don't press ANY OTHER KEY BUT 'e'. I was miss fortuned enough to actually click one of the arrows by mistake. Thus when I pressed 'e' i was taken to a completely different text menu, one without the 'vt.handoff' line ... Kinda screwed up xD

Other than that, awesome tutorial! Thanks!

---

### Post by FoZFoRiC on 2012-05-03
> **MorrisseyJ said:**
> Thanks Hubu, 

I didn't have a backup so haven't tried your solution.

I did however get this working another way. So here is another detailed solution. It should work but you will need a wired internet connection.

First you need to blacklist b43 so that you can get into the live session.

1. Boot to the live CD/USB
2. When the screen comes up showing the accessibility icon (little stick man and keyboard at the bottom of the screen), press any key
3. Pick your language, press enter
4. Press F6, this will launch a dialogue
5. Press esc to get rid of the dialogue
6. You should now have a cursor from which you can enter commands below the boot options: Type  making sure there is a space before and after the text you enter.
7. Press enter to either 'Try Ubuntu without installing' or 'Install Ubuntu'

In the case of the former, above, your instance of the live session should now work.

Now you should be able to install Ubuntu but you will still need to install b43 onto your system so that you can boot normally and use your wireless. To do this you have to boot to your system to do the install, but before that will work you once again have to blacklist b43 in the boot process. Here are the instructions.

1. Boot to the grub screen. If grub doesn't load automatically press, and hold, the Shift key after the BIOS screen (the screen mentioning your machine's manufacturer) disappears.
2. At the grub screen (the purple screen which lets you choose the instance of the kernel you want) press 'e', this will bring up a screen of text.
3. Using the arrow keys, navigate to the line which ends with "vt.handoff" or something similar. At the end of that line enter  again making sure to leave spaces before and after.
4. Press F10

This should boot you to your install, but your wireless won't be working. To fix this we have to install b43

1. Open a terminal (ctrl+alt+t or hit the 'super-key' (the one with the windows logo on it) and type 'terminal' and press enter).
2. Enter 3. Enter your password (note your keystrokes won't register) and hit enter

Now b43 should install, your wireless should work and you should be able to boot without any problems. 

Thanks to different people who helped me sort this out. Also, here is a blog detailing much of what needs to be done and which helped me get this sorted: [http://linux-software-news-tutorials.blogspot.co.uk/2012/04/installing-ubuntu-1204-crashes-because.html](http://linux-software-news-tutorials.blogspot.co.uk/2012/04/installing-ubuntu-1204-crashes-because.html)


[SIZE=4]Apparently the Win wubi or network install wubi doesn't  have the same feature in "accessibility" because all I get is visibility  options and F6 does nothing. [SIZE=2][Whole description of my problem]("http://ubuntuforums.org/showthread.php?t=1972356")[/SIZE][/SIZE]

---

### Post by DemonSharkKisame on 2012-05-03
Quick question: would the blacklist for GRUB be permanent or does it only take effect for the session that it's entered? I want to know because I'm unsure whether blacklisting my wireless chip would keep me from manually installing my Broadcom drivers (I have an Ethernet connection, but I don't feel like dragging my desktop all the way to my living room just to install a driver).

---

### Post by MorrisseyJ on 2012-05-04
FoZFoRiC: Sorry, i don't know much about Wubi, i only used it very briefly and a long time ago. Perhaps you would do well to drop this into a Wubi thread. Sorry i can't be of more help.

DemonSharkKisame: I am pretty sure its just for the session. If you want to check just boot with the blacklist then reboot and see if the error comes up or the machine freezes. If it does, the blacklist has persisted, if it hasn't, then it hasn't.

---

### Post by leilton on 2012-05-19
> **MorrisseyJ said:**
> Thanks Hubu, 

I didn't have a backup so haven't tried your solution.

I did however get this working another way. So here is another detailed solution. It should work but you will need a wired internet connection.

First you need to blacklist b43 so that you can get into the live session.

1. Boot to the live CD/USB
2. When the screen comes up showing the accessibility icon (little stick man and keyboard at the bottom of the screen), press any key
3. Pick your language, press enter
4. Press F6, this will launch a dialogue
5. Press esc to get rid of the dialogue
6. You should now have a cursor from which you can enter commands below the boot options: Type  making sure there is a space before and after the text you enter.
7. Press enter to either 'Try Ubuntu without installing' or 'Install Ubuntu'

In the case of the former, above, your instance of the live session should now work.

Now you should be able to install Ubuntu but you will still need to install b43 onto your system so that you can boot normally and use your wireless. To do this you have to boot to your system to do the install, but before that will work you once again have to blacklist b43 in the boot process. Here are the instructions.

1. Boot to the grub screen. If grub doesn't load automatically press, and hold, the Shift key after the BIOS screen (the screen mentioning your machine's manufacturer) disappears.
2. At the grub screen (the purple screen which lets you choose the instance of the kernel you want) press 'e', this will bring up a screen of text.
3. Using the arrow keys, navigate to the line which ends with "vt.handoff" or something similar. At the end of that line enter  again making sure to leave spaces before and after.
4. Press F10

This should boot you to your install, but your wireless won't be working. To fix this we have to install b43 - this is where you'll need your wired internet connection.

1. Open a terminal (ctrl+alt+t or hit the 'super-key' (the one with the windows logo on it) and type 'terminal' and press enter).
2. Enter 3. Enter your password (note your keystrokes won't register) and hit enter

Now b43 should install, your wireless should work and you should be able to boot without any problems. 

Thanks to different people who helped me sort this out. Also, here is a blog detailing much of what needs to be done and which helped me get this sorted: [http://linux-software-news-tutorials.blogspot.co.uk/2012/04/installing-ubuntu-1204-crashes-because.html](http://linux-software-news-tutorials.blogspot.co.uk/2012/04/installing-ubuntu-1204-crashes-because.html)


And all of this to get an updated version of Ubuntu, which has taken them 6 months, so that you need to do all the above just to get back to basically where you were before they messed about.

I left Windows because they would not leave well alone.

Still waiting to be told why, when I cannot load (only get cursor), 12.04 I have no problem installing, but don't want. downloaded and burnt to disc, L, M and X Ubuntu.

Going to try and find another version (if that’s the word), of Linux, Ubuntu can then play around as much as they like, but without me.

---

### Post by jbart0312 on 2012-08-22
> **MorrisseyJ said:**
> Thanks Hubu, 

I didn't have a backup so haven't tried your solution.

I did however get this working another way. So here is another detailed solution. It should work but you will need a wired internet connection.

First you need to blacklist b43 so that you can get into the live session.

1. Boot to the live CD/USB
2. When the screen comes up showing the accessibility icon (little stick man and keyboard at the bottom of the screen), press any key
3. Pick your language, press enter
4. Press F6, this will launch a dialogue
5. Press esc to get rid of the dialogue
6. You should now have a cursor from which you can enter commands below the boot options: Type  making sure there is a space before and after the text you enter.
7. Press enter to either 'Try Ubuntu without installing' or 'Install Ubuntu'

In the case of the former, above, your instance of the live session should now work.

Now you should be able to install Ubuntu but you will still need to install b43 onto your system so that you can boot normally and use your wireless. To do this you have to boot to your system to do the install, but before that will work you once again have to blacklist b43 in the boot process. Here are the instructions.

1. Boot to the grub screen. If grub doesn't load automatically press, and hold, the Shift key after the BIOS screen (the screen mentioning your machine's manufacturer) disappears.
2. At the grub screen (the purple screen which lets you choose the instance of the kernel you want) press 'e', this will bring up a screen of text.
3. Using the arrow keys, navigate to the line which ends with "vt.handoff" or something similar. At the end of that line enter  again making sure to leave spaces before and after.
4. Press F10

This should boot you to your install, but your wireless won't be working. To fix this we have to install b43 - this is where you'll need your wired internet connection.

1. Open a terminal (ctrl+alt+t or hit the 'super-key' (the one with the windows logo on it) and type 'terminal' and press enter).
2. Enter 3. Enter your password (note your keystrokes won't register) and hit enter

Now b43 should install, your wireless should work and you should be able to boot without any problems. 

Thanks to different people who helped me sort this out. Also, here is a blog detailing much of what needs to be done and which helped me get this sorted: [http://linux-software-news-tutorials.blogspot.co.uk/2012/04/installing-ubuntu-1204-crashes-because.html](http://linux-software-news-tutorials.blogspot.co.uk/2012/04/installing-ubuntu-1204-crashes-because.html)

Hey. Jbart0312 here, new to the forum. Ubuntu user for close to a year. ..

About four weeks ago my Dell Inspirion 6000 (my laptop with a nice giant screen that I can't live without) crashed. I was running 10.10  Pangolin, just recently upgraded from 10.04. 

By the way it was a You tube video that initially started the whole problem. And the fix required a LiveUSB along with some line commands that were all Latin to me....

I ordered a vendor release of 12.04 off Amazon for 8 bucks. Ubuntu Studio 12.04.

I love Ubuntu. I hate Windows. I dislike Bill Gates too. Why? Because he thinks taxes are useful. 

However, A problem cropped up immediately during install...  b43/ucode5.fw :: please visit so and so and download driver :: . 

Well, I am very happy to say that after tethering my laptop to my Nexus S, finding this thread and following the solution basically word for word, I finally ironed the whole problem out. 

So, this is my official Thx to MorrisseyJ for the post and the solution. I am completely new to GRUB and other Linux stuff but I'm rather adept at catching on to new sh**, but I couldn't have done it without this post. Or, at least, this was the first documented solution that I found and it worked.

Yes, I was without a PC for a month but I had my smart phone. Still, this experience has strengthened my commitment to the platform because... #1; Ubuntu is not a corporate experience... I think I can stop there.

---

### Post by MorrisseyJ on 2012-08-22
Hey jbart0312,

Welcome to the forums. 

Glad to hear that you got your machine working again, that the post was useful and that you are enjoying Ubuntu.

Good luck with the rest of it.

j

---

### Post by bbhaag on 2012-11-16
I just signed up to say thanks to MorrisseyJ.  I was given an older Acer Aspire 3002LCi laptop and when I tried installing Peppermint 3 I was getting the same error codes when trying to install.  Then the installation would halt.
A google search led me here and when I tried your instructions on the first page(post #6) it worked perfectly.
Thanks!

---

### Post by MorrisseyJ on 2012-11-17
Hey bbhaag, 

No problem at all. Glad you got it working. 

j

---

