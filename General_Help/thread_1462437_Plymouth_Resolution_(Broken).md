---
title: "Plymouth Resolution (Broken)"
date: 2010-04-25
forum: General Help
---

### Post by jnew93 on 2010-04-25
Hey all,

Upgraded to the beta 2 of 10.04 some days ago, and I've been keeping with the daily updates. Now, when I first upgraded, the install botched the fglrx packages and I had to finagle to get the driver removed and then reinstalled. (I guess this was a common problem)?

Now, when the driver was **not** working at all, Plymouth detected my LCD's resolution (1680x1050) fine and the boot screen looked very nice (if you like maroon). However, as soon as I fixed the issue and got the fglrx drivers running again, plymouth no longer detected my resolution, and shows the boot screen at a very low, stretched, and ugly setting.

My questions are:
Is this issue common?
Fixable?
If not fixable (I know the fglrx driver can be a pain), is there a settings file or a way to override the plymouth resolution?

Any help would be much appreciated, as this is the only gripe I have with the new version. Thanks!

Ubuntu 10.04, 2.6.32-22-generic, with fglrx drivers on a Radeon HD4830.

---

### Post by coolcaseley67 on 2010-04-25
hi 
 
- "(I guess this was a common problem)?" yes , i would not try to install or mess with any drivers until 10:04 is out .
 
- i would think there is a workround for the plymouth resolution. but i dont know about  plymouth . 
 
-move this post to the [[IMG]http://ubuntuforums.org/images/buttons/collapse_thead.gif[/IMG]]("http://ubuntuforums.org/#top")[**[SIZE=3][COLOR=#cc0000]Lucid Lynx Testing and Discussion[/COLOR][/SIZE]**]("http://ubuntuforums.org/forumdisplay.php?f=377")  
 
bit then more people can help you .
 
 
 
-hope it helps

---

### Post by themusicalduck on 2010-04-25
I think this is a problem with proprietry graphics drivers not supporting a feature (kernel mode setting if I remember right) that Plymouth needs to function properly. Basically, I have the same problem using the Nvidia drivers and you just have to either live with it or use open source drivers.

Not sure if there's a setting to change the resolution somewhere else though, but I don't think there is one.

---

### Post by coolcaseley67 on 2010-04-25
hi 
 
-yep that's it , same here . I have an Nvidia (3thparty) driver in 10:04 after uninstalling Nouveau  driver  . I dont know about a fix :confused:

---

### Post by jnew93 on 2010-04-25
Thanks guys. Hmm, maybe it's time to check on open-source drivers...

---

### Post by coolcaseley67 on 2010-04-26
hi 
 
- yerh that what we are saying , try using the open-source drivers to see if that fixs it .
 
-see this wiki  [http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page) it does help lot . see [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide) for 10:04 installing Guide(i think that the 3rd party one am not to sure ......
 
hope it helps

---

### Post by clhsharky on 2010-04-26
HI

Proprietary 'ATI/NV' drives don't and wont work with Plymouth in Lucid. Its not a bug its the design of Proprietary drivers to run in UMS ;user space' and Plymouth works with KMS 'kernel mode'. All OSS drivers use KMS.

Sharky

---

### Post by coolcaseley67 on 2010-04-26
hi 
 
ok , so we are stuck with out KMS until the Proprietary  are updated  , if ever .:lolflag:
 
Thanks

---

### Post by donsy on 2010-04-26
For a workaround try removing the "quiet splash" option in Grub2
```
gksudo gedit /etc/default/grub

GRUB_CMDLINE_LINUX_DEFAULT=""

sudo update-grub
```This will show a black screen with startup processes displayed. At least you'll see something is happening during startup. On my system it also significantly reduced the startup time.

See [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275) for more details.

---

### Post by itsjustarumour on 2010-04-30
For those peeps who don't want to faff around too much, these issues with Plymouth and the proprietary NVidia driver are a know bug affecting both Ubuntu and Kubuntu.  So it might be worth just hanging fire for a bit as the devs are currently working on a fix - see [https://bugs.launchpad.net/ubuntu/+source/kubuntu-default-settings/+bug/551290](https://bugs.launchpad.net/ubuntu/+source/kubuntu-default-settings/+bug/551290) for further details. (Or switch over to the Nouveau driver as mentioned earlier in this thread, if you don't need the 3G acceleration and faster frame rates.)

---

### Post by coolcaseley67 on 2010-04-30
hi

-thanks for letting us know , we will wait for a fix when its out :KS

-jnew93 would you mark this solved ?

thanks

---

### Post by NoFearDJB on 2010-04-30
This helped me!
[http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/](http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/)

---

### Post by zeiz on 2010-05-02
This helped me too! 

Whatever I tried I couldn't get grub2 menu splash on 1680x1050 monitor.
Two other machines displayed pictures on the fly but this one refused.
Now it's fine.

Thanks for the link!

---

### Post by kevpatts on 2010-05-04
This doesn't work for me because I had to install using grub 0.97 (not grub2) because I use a fakeraid setup.

Any idea how to achieve this for grub 0.97?

---

### Post by GeoMX on 2010-05-08
How do I now what driver am I using?
How do I use the nouveau driver? Where do I find more info about this one?

---

### Post by coolcaseley67 on 2010-05-09
hi  GeoMX

- nouveau is build in to Ubuntu 10.04 .   

- to reinstall it see [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia/Nouveau](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia/Nouveau)

happy ubunting !

---

### Post by coolcaseley67 on 2010-05-26
HI ALL

see [http://community.linuxmint.com/tutorial/view/37](http://community.linuxmint.com/tutorial/view/37) this very good fix !!!! :KS


Happy ubunting

---

