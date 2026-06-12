---
title: "Ubuntu 9.10 will not turn on for me please help!"
date: 2010-02-28
forum: General Help
---

### Post by georgep1993 on 2010-02-28
ok so this is my second post because i had no replys on the other one, i installed ubuntu from my Win7 Desktop. then when i got onto Ubuntu i installed the graphics card drivers, and the update manager came up, however i clicked restart (for the graphics) before update manager had finished, and when it came back on, a load of code came up on my screen and basically wouldnt go on to ubuntu, please help!

---

### Post by Arkitekt on 2010-02-28
sounds to me that something is definitely broken from restarting during an update.

any possibility you could post the code that you referring to?

---

### Post by georgep1993 on 2010-02-28
init: udevtrigger main process (452) terminated with status 1
init: udevtrigger post - stop process (453) terminated with status 1
init: udevmonitor main process (451) killed by TERM signal
fsck from util - linux - ng 2.16
/dev/loop0: clean, 131510/10731521 files, 795521/4286464 blocks
init: networking main process (485) terminated with status 1

---

### Post by georgep1993 on 2010-02-28
know it ? =/

---

### Post by rahilm on 2010-02-28
is this a Wubii install??

---

### Post by georgep1993 on 2010-02-28
yea, if you mean by i clicked wubi and it started the install

---

### Post by rahilm on 2010-02-28
i read somewhere that grub2 bootloader has been having problems with wubii. That's why they removed mint4win from linux mint. Perhaps you should try a regular install.

---

### Post by georgep1993 on 2010-02-28
Thats what im trying now, but 1. i cannot find how to uninstall it, and 2. i dont know how to do regular install, this is my first time installing a new OS. =/

---

### Post by 3rdalbum on 2010-02-28
If you are left with a command prompt, you might be able to resume the upgrade process assuming that it was stopped while it was installing the new packages.

Put the following into the command line:

```
sudo dpkg --configure -a
```

It may ask for your password - type it in and hit Enter, it won't display anything while you're typing.

Once the updating process has finished (if it works) type:

```
sudo reboot
```

---

### Post by georgep1993 on 2010-02-28
ive got a command prompt on Win7 if thats what you mean, however it wont even let me onto Ubuntu.

---

### Post by 3rdalbum on 2010-02-28
> **georgep1993 said:**
> Thats what im trying now, but 1. i cannot find how to uninstall it, and 2. i dont know how to do regular install, this is my first time installing a new OS. =/

1. You remove it through the Add/Remove Programs function in the Control Panel in Windows.

2. If you want to install Ubuntu as a real dual-boot system, then it's as easy as falling off a log. First, back up your Windows data. Second, boot from the Ubuntu CD (you might need to change the settings in your BIOS so it checks the CD drive before the hard disk) and follow the prompts. Third, at the screen that asks if you want to "install side by side", just drag the little handle in the bottom bar graph to the left to show how much space you want for Ubuntu.

---

### Post by 3rdalbum on 2010-02-28
> **georgep1993 said:**
> ive got a command prompt on Win7 if thats what you mean, however it wont even let me onto Ubuntu.

I meant the Ubuntu command-line.

Underneath the Ubuntu GUI is a command-line. When the GUI isn't running, the command-line still is. After you get those error messages, you may end off with something like this on the screen:

```
george@my-desktop:~$
```

You can type commands into this.

If you don't have this on the screen, you can try pressing Control-Alt-F2 to switch to a new virtual terminal. You can log in here using your username and password, and get a command prompt.

---

### Post by georgep1993 on 2010-02-28
Yea but i looked in the add remove program and for some reason its not there? nothing sayign ubuntu or anything. and For the install, i dont have a CD for it, should i just paste the downloaded files onto a cd? thanks :)

---

### Post by 3rdalbum on 2010-02-28
> **georgep1993 said:**
> Yea but i looked in the add remove program and for some reason its not there? nothing sayign ubuntu or anything. and For the install, i dont have a CD for it, should i just paste the downloaded files onto a cd? thanks :)

If you don't have a CD, then you have a "disc image" somewhere on your computer. This is a file that contains the exact contents of the Ubuntu CD, and of course you can burn this to CD. It should be called something like "ubuntu-9.10-desktop-i386.iso".

You must burn it in a specific way - don't just drag it to a CD. You must use the "Burn image to disc" or "Burn ISO Image" function of your CD burning software. Any other functions (like "Data Disc" or "Create Bootable CD") will NOT make the CD correctly.

---

### Post by georgep1993 on 2010-02-28
Yuup, i burnt the ISO to a file a while back and when i went onto the CD it say there was nothing on it =/

---

### Post by georgep1993 on 2010-02-28
come to think about it , i did it differently, i unextracted the files, then with winRAR did "add to archive" and saved it as ISO. and put it on the cd. i cant find this iso file, will it be within the ubuntu folder? stilll cant find it =/=/

---

### Post by 3rdalbum on 2010-02-28
> **georgep1993 said:**
> come to think about it , i did it differently, i unextracted the files, then with winRAR did "add to archive" and saved it as ISO. and put it on the cd. i cant find this iso file, will it be within the ubuntu folder? stilll cant find it =/=/

I'm not sure I can exactly follow what you've done, but you need the **original ISO file** that you downloaded. If you "extract the files" then you'll lose the special sauce that makes the CD able to boot.

The original ISO will be wherever you downloaded it to originally. If you got Wubi to download it for you, then I can't help you find this - I don't know where it gets placed and I can't try it out (don't have Windows).

---

### Post by georgep1993 on 2010-02-28
Ok, im sorry because this is probably really quite annoying for you, but ill redownload the file , and i have a blank CD, if you could tell me what to do from the stage of the file is downloaded and how to get it onto the CD that would be all i need, ill work out how to uninstall the one i have myself.

---

### Post by rahilm on 2010-02-28
> **georgep1993 said:**
> Ok, im sorry because this is probably really quite annoying for you, but ill redownload the file , and i have a blank CD, if you could tell me what to do from the stage of the file is downloaded and how to get it onto the CD that would be all i need, ill work out how to uninstall the one i have myself.

[B]If you want to uninstall the wubii install, i remember that there was an uninstall program in the folder where it is installed (It doesn't show in add/remove).

As far as installing goes, download the iso,
[/B]Well burn it to a CD (If you have win7, there is an option when you right-click on it)
Put the CD in the tray and reboot.
Boot from the CD (If it doesn't, then check the BIOS settings)
Start Ubuntu (the first option)
Start Install
When it comes to select partition, drag the sidebar to the left to give the space you want to ubuntu
**(VERRY IMPORTANT: Make sure that you select the first option in partitioning, DO NOT select USE ENTIRE DISK this will format the entire disk)**

---

