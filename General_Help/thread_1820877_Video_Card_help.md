---
title: "Video Card help"
date: 2011-08-08
forum: General Help
---

### Post by arizonagirl11 on 2011-08-08
Hello. I recently updated my computer, which means doing the dreaded driver search. Giving Ubuntu one last chance. I just downloaded the newest one, 11.04 I believe it is. My video card is an ATI Radeon X1600. I downloaded the driver from the site, and it is called "ati-driver-installer-9-3-x86.x86_64.run. I have 32 bit Ubuntu, but the driver said it is for both. I attempted to run the file, and it starts, but then it stops. When I choose "run" from the options after clicking the icon, it does nothing. When I click terminal, it shows it doing something, then an error flashes and it shuts down. Unfortunately, it is so fast , I can not read the error. Does anyone know what to do? How can I get this driver to work on this computer? I am at my end with this. Any help would be greatly appreciated.

---

### Post by mendhak on 2011-08-08
Hi, have you had a look at the ATI Driver page on the Ubuntu help site?

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Try following the instructions there, it covers both ATI's and the open source driver.

---

### Post by arizonagirl11 on 2011-08-08
Thank you very much. I did not see That page. I will go there tomorrow and look at it when I wake up (in bed now on my cell )  thanks again and I will let you know what happens

---

### Post by Mark Phelps on 2011-08-08
Save yourself the trouble -- there is NO restricted driver you can download that will work with your video card and recent versions of Ubuntu (newer than 8.10).  AMD dropped Linux driver support for your card years ago.

The open-source ATI video driver is installed by default when you setup Ubuntu -- and that is all that is available, now.

Any other drivers you download will only corrupt your display -- forcing you to drop into a command line and replace them with the same driver you already have in place.

---

### Post by realzippy on 2011-08-08
> **Mark Phelps said:**
> AMD dropped Linux driver support for your card years ago.
Any other drivers you download will only corrupt your display ....

Yep.
I don 't know why ATI never managed to have a warning on their site [like the debian guys]("http://wiki.cchtml.com/index.php/Debian") or
modified their driver-finding-app to not ignore Xserver version.
Sadly I see those suggestions to install catalyst on "old" ati devices
pretty often here in the forum,creating trouble OP might not can handle...

---

### Post by arizonagirl11 on 2011-08-08
So then, this driver that comes with Ubuntu then, is just as good? 

Silly question, in previous versions, they had effects options. Is there any effects options in Ubuntu 11.04? It is very different then the previous versions. I"m not sure if I am not seeing it cause of the driver, or if it's because it doesn't exist anymore.

Thanks

---

### Post by arizonagirl11 on 2011-08-09
And also, how do you know if this default video driver is working? I do not know if Ubuntu is working in low graphics mode or not?

---

### Post by linuxman94 on 2011-08-09
As long as you don't see a pop up when you turn on the computer that says "Ubuntu is running in low graphics mode," then it is working fine.  Also, the driver you downloaded will work.

Here are the install instructions. 

Make sure the file is saved in your home directory
Open terminal (search for it)

Enter this command and type your password when it asks:

```
sudo sh ./ati-driver-installer-9.2-x86.x86_64.run --buildpkg
```

Once it has finished (assuming no errors), these to commands and reboot.

```
sudo dpkg -i *.deb
sudo aticonfig --initial
```

If the first command exits with an error, post the entire output here and we'll take a look at it.

---

### Post by arizonagirl11 on 2011-08-09
Ah it did error out :( Below is the error log

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.38-8-generic; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.Z4s0Yh

---

### Post by realzippy on 2011-08-09
**[SIZE="2"]@linuxman94[/SIZE]**
You give malicious instructions!!
Why do you ignore post  #4 and 5# ?
The ATI FGLRX DRIVER DOES NOT WORK for ATI Radeon X1600!!!!!!!
Please read [this]("http://wiki.cchtml.com/index.php/Debian") 
and [this]("http://wiki.cchtml.com/index.php/9.4") before giving advice to install catalyst/fglrx to
somebody in the future...

@arizonagirl11
 please ignore linuxman94's instructions.You cannot install the driver he  
 suggests.It will not work or even corrupt your system !!!!!!
The free ati driver (the only one existing) is working out of the box (included in the "system").
There is nothing you can install...

---

### Post by Duncan Williams on 2011-08-09
There is supposedly little malware available to mess your linux system.
However...
There is a lot of advice using sudo commands that cause just as much havoc.

---

### Post by arizonagirl11 on 2011-08-09
ok thank you. I will delete the driver that I downloaded.

---

### Post by realzippy on 2011-08-09
Btw,did you have problems with the free ati driver?

If so,there are a few modified versions out there in some PPAs,which
could be used *if* you have trouble.

---

### Post by arizonagirl11 on 2011-08-09
I"M honestly not sure. I don't see any ways to have the "effects" the previous versions of ubuntu have (I now have 11.04), and my Second LIfe game was slightly messed up. I do not know if that's because of the driver or not.

---

### Post by Duncan Williams on 2011-08-09
Second life won't run on my system even though I am using latest nvidia drivers. It won't work correctly with open-source (as far as I know)
How did you get second life to even come up?

The open-source ati drivers are ok for most things.
(I used them re/ amd 9200) but they are not the best with any 3D stuff. (including unity/compiz - games )

Using unity 2D will give you a more responsive desktop with a few affects.

---

### Post by realzippy on 2011-08-09
> **arizonagirl11 said:**
> I"M honestly not sure. I don't see any ways to have the "effects" the previous versions of ubuntu have (I now have 11.04), and my Second LIfe game was slightly messed up. I do not know if that's because of the driver or not.

Yep,there is a regression.Maybe your card is blacklisted (some are in 11.04).
If you do not need unity,you might stay with 10.04/10....

@DW
 [I]Second life won't run on my system even though I am using latest nvidia  drivers.
[/I]

..then there is something wrong with your configuration.The driver handles it fine normally..

---

### Post by linuxman94 on 2011-08-09
> **realzippy said:**
> **[SIZE="2"]@linuxman94[/SIZE]**
You give malicious instructions!!
Why do you ignore post  #4 and 5# ?
The ATI FGLRX DRIVER DOES NOT WORK for ATI Radeon X1600!!!!!!!
Please read [this]("http://wiki.cchtml.com/index.php/Debian") 
and [this]("http://wiki.cchtml.com/index.php/9.4") before giving advice to install catalyst/fglrx to
somebody in the future...


Yeah I just saw that page about it not working in natty.  Sorry about that.  However, that driver would technically work if you don't have the latest X stack.

---

### Post by .... on 2011-08-09
X1k cards use the open-source R300g driver for 3D. This should handle Unity/Compiz just fine (my X1300 does). I'm not sure about SLife.
> If you do not need unity,you might stay with 10.04/10....There is no reason to downgrade 11.04 even if Unity doesn't work. Ubuntu Classic (GNOME 2.x) and Unity 2D are available and/or easily installable in Natty.
> I don't know why ATI never managed to have a warning on their site [like the debian guys]("http://wiki.cchtml.com/index.php/Debian") Well, the AMD/ATI page does link you to the unofficial wiki, and the same big, red warning is present in the Ubuntu and Debian install guides. Of course, if user doesn't attempt to read documentation....

---

### Post by Duncan Williams on 2011-08-11
i got 3D flying here, avant and major mods, but....   secondlife wont work...

---

### Post by Mark Phelps on 2011-08-11
> **linuxman94 said:**
> Yeah I just saw that page about it not working in natty.  
It's NOT about it not working in Natty.  It does not work on ANY Ubuntu version newer than 8.10.  So, it didn't work on the 9.x or 10.x versions, either.

> However, that driver would technically work if you don't have the latest X stack.
And .. you were going to walk a new person through the difficult process of X-server regression and locking out X-server package updates??

So, once again -- do NOT give bad advice.

---

