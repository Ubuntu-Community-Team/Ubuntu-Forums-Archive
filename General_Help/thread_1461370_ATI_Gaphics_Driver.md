---
title: "ATI Gaphics Driver"
date: 2010-04-24
forum: General Help
---

### Post by Toastedmick on 2010-04-24
Hi All.
I'm new to Ubuntu, and so far I like what I see.
Although, I have been trying to install the graphics driver, and I feel that I so close but I'm missing something simple. I've visited lots of forums and tried lots of instructions.
The driver that I'm trying to install is called 'ati-driver-installer-9-6-x86.x86_64.run'
It is located on the desktop.
I can locate in terminal.
If I type in 'sudo chmod ugoa+x ati-driver-installer-9-6-x86.x86_64.run' I am asked for the password, but when I type, no characters appear. I type the password anyway but it is not accepted.
Another forum said to log in as root by typing 'su'. Once again it asks for a password, but no characters appear and it then says 'Authentication failure'.
Can anyone see what I'm doing wrong?
Any help would be appriciated.
Cheers,
Michael.

---

### Post by mckinnon81 on 2010-04-24
When using sudo and it asks for your password, the characters are not echoed or displayed as a '*' this is simply how it works. You just have to make sure that you are using the password that belongs to the user you are logged on as and you are typing it correctly.

Try installing the file using the command:

```
sudo sh ati-driver-installer-9-6-x86.x86_64.run
```

---

### Post by Toastedmick on 2010-04-24
Hi, and thanks for the quick reply.
I guessed that it might be the case, so I typed in the password anyway.
I've now been though it several times and I'm positive the password I'm typing is correct.
Anyway, I copied and pasted the command, and I got this response.

'Created directory fglrx-install.lHjtCW
Verifying archive integrity...Error in MD5 checksums: 0936d4717787c93f9327746586150172 is different from 62cc81468b9bd6ea298b296b2ff0eb1a'

I have gone to the correct folder, and when I type 'ls' I can see the driver.
It just doesn't seem to want to work. Also I have downloaded it from two different sites because I thought that maybe the first was corrupted or something. But that doesn't seem to be the case either.

---

### Post by Toastedmick on 2010-04-24
BTW. I'm using Ubuntu 9.1.

---

### Post by koma77 on 2010-04-24
It looks like the driver you have downloaded is damaged. Try and download it again and it should work.

---

### Post by 3rdalbum on 2010-04-24
You're actually doing it completely wrong.

Ubuntu provides a proprietary ATI driver; go to System > Administration > Hardware Drivers to download and install it. If it doesn't appear, either your hardware is not supported (anything earlier than a Radeon HD 2600 is not supported, but this is true for the file you downloaded too) or you need to reload the package list by going into Synaptic Package Manager and hitting Reload.

You should only use the **download from ATI.com** if you:

# Have problems with the version of the driver provided by Ubuntu or
# Have hardware that is too new for the Ubuntu-provided driver

If you use the driver from ATI.com you will need to reinstall it every time your kernel updates. The driver from Ubuntu will stay in sync with the kernel and not need reinstalling.

---

### Post by Toastedmick on 2010-04-24
Thanks for the replies.

I've downloaded and installed the ati and nvidia drivers from the synaptic package manager. When I go to Syestem>Administration>Hardware Drivers, it is blank and says 'No proprietary drivers are in use on this system'. So it looks like I'll need to update my graphics card or stick with windows for the moment. :(
Thanks anyway.

---

### Post by Yellow Pasque on 2010-04-24
@Michael
What video card do you have?
```
lspci
```

BTW, remove the nvidia packages if you don't have an nvidia card.

---

### Post by Toastedmick on 2010-04-24
Hey Temüjin,

Sorry about the delay.

01:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]

I know it's an older card, but this is my daughters computer. If I can get everything working on this, I'll be switching our other computers over to Ubuntu as well.

Thanks for the reply.

---

### Post by Yellow Pasque on 2010-04-24
The proprietary driver doesn't support that card anymore. See this to purge all the proprietary stuff you tried to install: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

---

### Post by Toastedmick on 2010-04-24
Thanks for that.
I've purged all the nvidia and ATI drivers.
But I still need to find a compatible driver for my card.
I am looking into ndiswrapper.
Is this a path I want to go down? Or should I skip it and keep searching.

---

### Post by 3rdalbum on 2010-04-24
> **Toastedmick said:**
> Hey Temüjin,

Sorry about the delay.

01:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]

I know it's an older card, but this is my daughters computer.

Unfortunately, ATI/AMD doesn't care about your card anymore... sorry. ATI's driver won't run your card. The Linux community still cares about your daughter's computer and others like it, and so we make an open-source driver that should give you basic 2D acceleration and possibly some 3D. It is enabled by default.

And that's why there's nothing in the Hardware Drivers program - **the only driver you can use for this card is already in use**.

EDIT: Ndiswrapper is only for wireless cards - there's no equivalent for graphics cards. I'll give you five points for ingenuity though :-)

---

### Post by Toastedmick on 2010-04-24
Hey.

Well at least that answers my question.
Thank you.
I assumed that because there was no driver showing in the hardware drivers list, there was no driver installed at all.
I'll find a newer graphics card during the week and install it and see how I go. I've learnt a lot already though, and thanks to everyone for their help.
I haven't been put off Ubuntu. It just going to take a bit of learning.

---

### Post by clhsharky on 2010-04-24
HI

ATI actively support legacy chips in the OSS 'open source stack' driver. If you would like to contact a ATI/Linux dev go here, look for bridgman.
Open-Source AMD/ATI Linux
[http://www.phoronix.com/forums/forumdisplay.php?f=43](http://www.phoronix.com/forums/forumdisplay.php?f=43)
Do some searching and reading some threads, very informative.

If you would like newer OSS drivers, use this PPa
[https://edge.launchpad.net/~xorg-edgers/+archive/ppa](https://edge.launchpad.net/~xorg-edgers/+archive/ppa)

There are also advantages to using OSS drivers, you can use newer Kernels. 2.6.33.2 is latest stable, debs are here
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

2D acceleration In the radeon driver is superor to fglrx.

Sharky

The new Gallium G3D R300G driver is also available for testing on your chip Toastedmick
Many ATI legacy chips are very well supported, but not with  fglrx.

---

