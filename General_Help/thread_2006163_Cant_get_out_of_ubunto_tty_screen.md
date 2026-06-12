---
title: "Cant get out of ubunto tty screen"
date: 2012-06-18
forum: General Help
---

### Post by ubuntoneedhelp303 on 2012-06-18
I am new to Ubuntu and I am stuck in tty mode.I heard that i can try Ctrl +alt+f7 to get out but it doesnt work, I am wondering what to do, i heard Ubuntu is a great os and i would like to try it. ALSO i heard it might be a driver problem? Im not sure.I have vied many topics with problems like this but yet to find an solution.:confused::confused::confused:

---

### Post by Kakers on 2012-06-18
Welcome to Ubuntu! You can use Alt + the function keys to cycle through the different Xsessions. F7 I believe is typically the one that runs the GUI.

What happens when you type 'startx'? You may need to elevate your permissions using the sudo command, so this would be 'sudo startx'.

---

### Post by sudodus on 2012-06-18
Are you testing Ubuntu booted from a CD or USB drive? Or have you installed Ubuntu?

Have you ever had a graphical desktop environment (screen)? Or does your screen only reach to a text mode?

Sometimes there are problems with the graphics card or chip, and you need a boot option, for example ***nomodeset***. Please look at this link:
[[COLOR="Red"]_https://help.ubuntu.com/community/BootOptions_[/COLOR]]("https://help.ubuntu.com/community/BootOptions")

It would make it easier for us to help, if you specify your computer's CPU, RAM and graphics card or chip.

---

### Post by wheeze on 2012-06-18
Try Ctrl-Alt-F8 or F9, too. The display manager can run in the last three virtual terminals.

If you're booting to a console though you probably have something else going on as the handoff to the display manager should automatic.

Do you an nVidia graphics card and did you install the proprietary driver? If so you may need to run **sudo nvidia-xconfig** then reboot your machine. Sometimes the driver installer fails to run the configuration step.

---

### Post by ubuntoneedhelp303 on 2012-06-18
@Kakers I install startx and when i do and use crtl + alt + f7 thiers a mouse/cursor with a white screen at the top left.


@sudodus I installed ubuntu. And it reaches the startup loading ubuntu 12.04 screen then switches me to the tty screen.


@wheeze crtl 8 and crtl 9 dont work for me. And i dont have an nvidia graphics card. :cry::cry:

---

### Post by Kakers on 2012-06-18
Do you have ubuntu-desktop installed?

I actually missed it myself, when I skipped past it during the alternative install.

---

### Post by ubuntoneedhelp303 on 2012-06-18
Yes yes i do i clicked it during install i was actually wondering which one to click and i chose Ubuntu desktop.

---

### Post by ubuntoneedhelp303 on 2012-06-18
Bump.

---

### Post by ubuntoneedhelp303 on 2012-06-18
Aah :cry: 132 views and still no solution to my problem ill see if anyone reply's tomorrow. Wish me luck :KS:KS:KS.

---

### Post by sudodus on 2012-06-19
Did you try to run Ubuntu live 'test Ubuntu' from the CD drive before installing it? If you did not, please do it now, because it will give us valuable information without tampering with your hard drive.

Or is your system too small to allow a live session from a standard install CD or USB drive? If you have less than 512 MB or 1 GB of RAM it might be a good idea to get some very small system, for example a 'rescue CD' and make a swap partition. And then it will work better to run a live session and to install a full [KLX]ubuntu system.

And test if some boot option will help. See my link in post #3.

---

### Post by ubuntoneedhelp303 on 2012-06-19
I'm trying to install Ubuntu on a net book but I have 1 GB ram on it.

---

### Post by sudodus on 2012-06-19
It should work with Ubuntu but I would suggest that you try the light-weight flavours of Ubuntu: Lubuntu and Xubuntu.

How did you try to install Ubuntu? Did you use a standard Ubuntu iso file and make a USB boot drive? If this is the case, did you ***test*** Ubuntu live (booted from the USB drive)? If not, I recommend that.

Or did you use an alternate iso file?

You might have problems with hardware recognition, and then it is worth trying some of the boot options.

---

### Post by ubuntoneedhelp303 on 2012-06-19
This is what my installer looks like. Found a picture of it on the internet. And ill try some of the boot options right now and if they don't work which OS do you recommend is better Lubuntu or Xubuntu mostly for lightweight gaming.

[IMG]http://4.bp.blogspot.com/-ZyttcHnUwhc/T6FHIbkfOJI/AAAAAAAAI0o/v2hW9o6-Lyc/s1600/ubuntu12.04-mini_2.png[/IMG]

---

### Post by sudodus on 2012-06-19
> **ubuntoneedhelp303 said:**
> This is what my installer looks like. Found a picture of it on the internet. And ill try some of the boot options right now and if they don't work which OS do you recommend is better Lubuntu or Xubuntu mostly for lightweight gaming.

This text interface looks like the alternate installer (or maybe the mini-iso), I'm not sure. But it is not the standard installer, and I think you don't have the option to run a live system from this boot drive.

If you find a suitable boot option, you might succeed in a few minutes.

Otherwise I suggest that you download both iso files and test them live. Lubuntu with LXDE is ultra-light and Xubuntu with XFCE is 'only' light, but has more features and eye-candy. For gaming and playing high definition video I would go for Lubuntu.

---

### Post by ubuntoneedhelp303 on 2012-06-19
Alright im going to go look for the standard installation and if it doesn't work ill get Lubuntu takes for all your help. :p:D:p

---

### Post by xp15 on 2012-06-19
I glad to catch this thread (:
It seems you've download an net-installer, what's  mean the disc or DOK are having only the basic of the system and the rest things-also a GUI-it's dowloading from the internet. So if havn't connected your laptop to the internat while installing-it couldn't install any GUI ;).

so let do it in level-level (an hebrew expression-in english it means-step after step).

do you have a DOK of more than 4GB?

---

### Post by sudodus on 2012-06-19
When you have a live session running, please post the output of
```
sudo fdisk -lu
```
It helps finding out how to create drive space for [LX]Ubuntu.

---

### Post by ubuntoneedhelp303 on 2012-06-19
@ xp15 Do you mean a USB? i have one that's 4GB's

---

### Post by GreatDanton on 2012-06-19
I would recommend you this link:[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu). It's link for downloading Lubuntu. Choose 32-bit version (I assume you have 32-bit computer), burn a cd (burn it at minimum speed) and then install it.

If you don't have any files on your Ubuntu 12.04 it's better to start from scratch.

Hope this helps.

---

### Post by ubuntoneedhelp303 on 2012-06-19
> **GreatDanton said:**
> I would recommend you this link:[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu). It's link for downloading Lubuntu. Choose 32-bit version (I assume you have 32-bit computer), burn a cd (burn it at minimum speed) and then install it.

If you don't have any files on your Ubuntu 12.04 it's better to start from scratch.

Hope this helps.

I already started the Lubuntu (torrent download cause its faster) thanks anyway  :biggrin:

---

### Post by xp15 on 2012-06-19
> **ubuntoneedhelp303 said:**
> @ xp15 Do you mean a USB? i have one that's 4GB's

great! now I assume you want to install (before installing-try the system) Ubuntu.
Here is the download page, choose 32/64 bit by your laptop: [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

you can find the guide here: [http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)

but step 3 is missing some important information.

[LIST]
[*]put attention that you are _**choosing the right drive-enter to "my computer" and check it!**_ which is your DOK!
[/LIST]

[LIST]
[*]also it's very important to create a **persistent file** of 1.5GB-which are 1**536mb! **(1024+512).
[/LIST]


[LIST]
[*]the last thing is that it will work better if you'll format your drive-so first backup important data if you need-_all data on the DOK  will be lost!_
[/LIST]
so, are you ready? ;)

---

