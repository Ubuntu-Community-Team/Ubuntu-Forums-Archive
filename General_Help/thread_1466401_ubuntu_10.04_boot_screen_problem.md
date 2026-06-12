---
title: "ubuntu 10.04 boot screen problem"
date: 2010-04-30
forum: General Help
---

### Post by khaos1 on 2010-04-30
Hi guys. I've just upgraded to Ubuntu 10.04 LTS. All are ok except some small bugs. The biggest one is that the boot screen is not showing. After the startup of my netbook (MSI wind ns011) a black screen is coming up and after a while is shown the login menu. In the shut down the shutdown screen is shown correctly.

My problem is how to fix that problem in order to show the boot screen (the purple with the red proccess bars :p)

Thanks
cya

---

### Post by ambdeep on 2010-04-30
i got the same problem...

---

### Post by philinux on 2010-04-30
> **khaos1 said:**
> Hi guys. I've just upgraded to Ubuntu 10.04 LTS. All are ok except some small bugs. The biggest one is that the boot screen is not showing. After the startup of my netbook (MSI wind ns011) a black screen is coming up and after a while is shown the login menu. In the shut down the shutdown screen is shown correctly.

My problem is how to fix that problem in order to show the boot screen (the purple with the red proccess bars :p)

Thanks
cya

Are you using the nVidia driver?

---

### Post by khaos1 on 2010-04-30
> **philinux said:**
> Are you using the nVidia driver?

I don't think so:
```
lspci -nn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GME Express Integrated Graphics Controller [8086:27ae] (rev 03)
```
Also in Hardware Drivers, it says that I have no prop. hardware driver needed
Is a graphics card / driver problem?

Thanks for your answer

---

### Post by philinux on 2010-04-30
Does Plymouth show at all even briefly?

---

### Post by khaos1 on 2010-04-30
> **philinux said:**
> Does Plymouth show at all even briefly?

If I understood what trying to say, what arg in plymouth I must type in order to test? I tried plymouth --help but I didn't understand cause I have no experience with plymouth.

Thanks

---

### Post by ambdeep on 2010-04-30
> **philinux said:**
> Does Plymouth show at all even briefly?

No it doesnt....

---

### Post by dino99 on 2010-04-30
sudo dpkg-reconfigure gdm
sudo dpkg-reconfigure plymouth

---

### Post by philinux on 2010-04-30
You can try this. If this does not work then reverse it.

```
gksu gedit /etc/initramfs-tools/conf.d/splash
```

and add this option FRAMEBUFFER=y, save the file.
Then

```
sudo update-initramfs -u
```

Reboot to see if it works. No guarantees.

There is a bug open.
[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540801](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540801)

---

### Post by ambdeep on 2010-04-30
> **dino99 said:**
> sudo dpkg-reconfigure gdm
sudo dpkg-reconfigure plymouth
still getting the same black screen....

---

### Post by khaos1 on 2010-04-30
> **philinux said:**
> You can try this. If this does not work then reverse it.

```
gksu gedit /etc/initramfs-tools/conf.d/splash
```and add this option FRAMEBUFFER=y, save the file.
Then

```
sudo update-initramfs -u
```Reboot to see if it works. No guarantees.

There is a bug open.
[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540801](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540801)

Now the boot screen is shown but with a delay and the black screen is shown also before the boot screen. It's ok I think but maybe the delay and the blackscreen before the boot screen maybe a prob for someone cause 10.04 ubuntu promised quicker boot

---

### Post by ambdeep on 2010-04-30
> **philinux said:**
> You can try this. If this does not work then reverse it.

```
gksu gedit /etc/initramfs-tools/conf.d/splash
```

and add this option FRAMEBUFFER=y, save the file.
Then

```
sudo update-initramfs -u
```

Reboot to see if it works. No guarantees.

There is a bug open.
[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540801](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540801)
thanks.....it did the trick....

---

### Post by drorlev on 2010-04-30
Hi guys,

Have you considered this reason:

Boot options hidden by default on Desktop and Netbook CDs
---------------------------------------------------------
The Ubuntu 10.04 LTS Desktop and Netbook CDs feature a new boot interface that is noninteractive by default. 
To configure advanced boot options, press any key at the first boot screen. 

This was copied from the [10.4 Release Notes]("http://www.ubuntu.com/getubuntu/releasenotes/1004").

Hope this helps,
dror

---

### Post by philinux on 2010-04-30
> **khaos1 said:**
> Now the boot screen is shown but with a delay and the black screen is shown also before the boot screen. It's ok I think but maybe the delay and the blackscreen before the boot screen maybe a prob for someone cause 10.04 ubuntu promised quicker boot

Subscribe to the above mentioned bug. Then do this.

```
apport-collect 540801
```

Only way to these issues solved is via launchpad.

---

### Post by khaos1 on 2010-04-30
> **philinux said:**
> Subscribe to the above mentioned bug. Then do this.

```
apport-collect 540801
```Only way to these issues solved is via launchpad.

When I Type that and followed the instructions it popups to me a msg that Im not the publisher or subscriber. I have loged in my launchpad account first

What's the prob?

---

### Post by philinux on 2010-04-30
> **khaos1 said:**
> When I Type that and followed the instructions it popups to me a msg that Im not the publisher or subscriber. I have loged in my launchpad account first

What's the prob?

Have you subscribed to that bug?

---

### Post by philinux on 2010-04-30
> **drorlev said:**
> Hi guys,

Have you considered this reason:

Boot options hidden by default on Desktop and Netbook CDs
---------------------------------------------------------
The Ubuntu 10.04 LTS Desktop and Netbook CDs feature a new boot interface that is noninteractive by default. 
To configure advanced boot options, press any key at the first boot screen. 

This was copied from the [10.4 Release Notes]("http://www.ubuntu.com/getubuntu/releasenotes/1004").

Hope this helps,
dror

Thats on the **livecd **installer. Not after installation
The Ubuntu 10.04 LTS Desktop and Netbook CDs feature a new boot interface that is noninteractive by default. To configure advanced boot options, press any key at the first boot screen.
That is to see menu where you can check cd for defects etc.

---

### Post by CoreyB. on 2010-04-30
> **ambdeep said:**
> thanks.....it did the trick....

Worked for me too.

---

### Post by SiegHard on 2010-04-30
Same problem, with trick it loads slowly ;/

---

### Post by Devi 710 on 2010-04-30
I had the same problem with the boot splash in 10.04.

Just install startup-manager from the Software Centre, then go to System > Administration > Startup Manager and change the Display Resolution to yours (mine is 1280x1024).

I also increased the colour depth, checked both boxes under Misc. and changed my boot loader menu resolution under the 'Advanced" tab.

Hope that helps.

Devi

---

### Post by andrewabc on 2010-04-30
> **philinux said:**
> You can try this. If this does not work then reverse it.

```
gksu gedit /etc/initramfs-tools/conf.d/splash
```

and add this option FRAMEBUFFER=y, save the file.
Then

```
sudo update-initramfs -u
```

Reboot to see if it works. No guarantees.

There is a bug open.
[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540801](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540801)

Thanks this solved my problem.

Same problem as others. no plymouth at all. Just a flashing _ for a bit, then some text, then desktop.
asus eeebox b202. intel GMA950 1.6ghz atom.

Looks like a lot of netbook (atom n270) owners are going to have the same problem since I have same hardware (except in a nettop).

The weird thing is that it worked fine with liveusb, but as soon as I installed it stopped working?

EDIT:
On shutdown I get some text, then plymouth. Only lasts 4 seconds so not important.

---

### Post by NoFearDJB on 2010-04-30
This website's solution worked for me!
[http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/](http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/)

---

### Post by G4MAC on 2010-05-01
philinux,

       You keep mentioning that if it does not work, then reverse it, I have not tried anything yet but will probably do so, most likely editing the splash and updating, if I knew how to reverse it, if you could please help with this it would be appreciated, thanks

---

### Post by lampakting on 2010-05-01
> **andrewabc said:**
> Thanks this solved my problem.

Same problem as others. no plymouth at all. Just a flashing _ for a bit, then some text, then desktop.
asus eeebox b202. intel GMA950 1.6ghz atom.

Looks like a lot of netbook (atom n270) owners are going to have the same problem since I have same hardware.

The weird thing is that it worked fine with liveusb, but as soon as I installed it stopped working?

EDIT:
On shutdown I get some text, then plymouth. Only lasts 4 seconds so not important.
Yup, same problem on my netbook (eeepc 1005)

---

### Post by CoreyB. on 2010-05-01
> **G4MAC said:**
> philinux,

       You keep mentioning that if it does not work, then reverse it, I have not tried anything yet but will probably do so, most likely editing the splash and updating, if I knew how to reverse it, if you could please help with this it would be appreciated, thanks

All you have to do to reverse it is type in the first command to bring up the file in gEdit, than erase the FRAMEBUFFER=y line, then run the second command.  Just like how you would do the change in the first place.

---

### Post by anirbans2006 on 2010-05-02
> **philinux said:**
> You can try this. If this does not work then reverse it.

```
gksu gedit /etc/initramfs-tools/conf.d/splash
```and add this option FRAMEBUFFER=y, save the file.
Then

```
sudo update-initramfs -u
```Reboot to see if it works. No guarantees.

There is a bug open.
[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540801](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540801)

I had Kubuntu boot screen before upgrading to Ubuntu 10.04. After upgrading I wanted to revert back to the Ubuntu boot screen. So I did:

> aptitude search plymouth
>sudo aptitude install  plymouth-theme-ubuntu-logo
>sudo update-alternatives --config  default.plymouth

After that I followed the instructions above to fix the resolution. Now I get the purple boot screen with 4 dots. But the word 'Ubuntu 10.04' appears in plain text rather than in the usual Ubuntu style and also there is no ubuntu logo. I checked the boot screen picture on the page
[http://www.ubuntu.com/products/whatisubuntu/1004features](http://www.ubuntu.com/products/whatisubuntu/1004features)
but mine was not similar to the one here.

---

### Post by d3drocks on 2010-05-02
I get no boot splash here as well. all i get is a flashing underscore for a few seconds, then the login screen. I dont really mind though, it is lightning fast on my netbook!

---

### Post by Jason Cook on 2010-05-03
> **khaos1 said:**
> Now the boot screen is shown but with a delay and the black screen is shown also before the boot screen. It's ok I think but maybe the delay and the blackscreen before the boot screen maybe a prob for someone cause 10.04 ubuntu promised quicker boot

The black screen is likely GRUB (the bootloader)

> **anirbans2006 said:**
> I had Kubuntu boot screen before upgrading  to Ubuntu 10.04. After upgrading I wanted to revert back to the Ubuntu  boot screen. So I did:

> aptitude search plymouth
>sudo aptitude install  plymouth-theme-ubuntu-logo
>sudo update-alternatives --config  default.plymouth

After that I followed the instructions above to fix the resolution. Now I  get the purple boot screen with 4 dots. But the word 'Ubuntu 10.04'  appears in plain text rather than in the usual Ubuntu style and also  there is no ubuntu logo. I checked the boot screen picture on the page
[http://www.ubuntu.com/products/whatisubuntu/1004features](http://www.ubuntu.com/products/whatisubuntu/1004features)
but mine was not similar to the one here.

This is the same problem I am having.

---

### Post by eorisis on 2010-05-04
Same problems here, I upgraded an hour ago and almost everything went wrong. My ubuntu 9.10 was working perfect on my laptop and it hadn't that much of software on except some basics. Right now I am installing 10.04 from the beginning (losing all I had done on my previous system). In a way I can say that this is alright, because I love ubuntu and linux generally, on the other hand, I am going to think about it a lot, to upgrade next time. I am not a linux guru, and also don't have much time to work on problems that in a way should not be there really, it was just an upgrade from a recently installed 9.10...

by the way, the 10.04 installation looks amazing.

.. all step by step from the beginning again !

---

### Post by gingivere0 on 2010-05-05
> **philinux said:**
> You can try this. If this does not work then reverse it.

```
gksu gedit /etc/initramfs-tools/conf.d/splash
```

and add this option FRAMEBUFFER=y, save the file.
Then

```
sudo update-initramfs -u
```

Reboot to see if it works. No guarantees.

There is a bug open.
[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540801](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540801)

THANK YOU! Finally a solution!  Doing this activated the boot splash and took about 15 seconds off of my boot time!

---

### Post by emagine on 2010-05-05
> **Devi 710 said:**
> I had the same problem with the boot splash in 10.04.

Just install startup-manager from the Software Centre, then go to System > Administration > Startup Manager and change the Display Resolution to yours (mine is 1280x1024).

I also increased the colour depth, checked both boxes under Misc. and changed my boot loader menu resolution under the 'Advanced" tab.

Hope that helps.

Devi
Thanks Devi!
This worked perfectly for me.

---

### Post by antrunner85 on 2010-05-08
> **anirbans2006 said:**
> I had Kubuntu boot screen before upgrading to Ubuntu 10.04. After upgrading I wanted to revert back to the Ubuntu boot screen. So I did:

> aptitude search plymouth
>sudo aptitude install  plymouth-theme-ubuntu-logo
>sudo update-alternatives --config  default.plymouth

After that I followed the instructions above to fix the resolution. Now I get the purple boot screen with 4 dots. But the word 'Ubuntu 10.04' appears in plain text rather than in the usual Ubuntu style and also there is no ubuntu logo. I checked the boot screen picture on the page
[http://www.ubuntu.com/products/whatisubuntu/1004features](http://www.ubuntu.com/products/whatisubuntu/1004features)
but mine was not similar to the one here.


 Hi everyone, I want to share a little bit of my experience since I had a similar problem but this response didn't work for me. 

I had an ugly splash image with no logo at boot splash. I tried doing what was recommended here but I had no change. Then I went on and tried this other solution.

[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

The result, I was unable to start the x server, left only with a low resolution boot. I went back and unchanged all what I did before and that seem to get me back to my xorg original configuration.

Finally I actually just went to synaptic manager and look for plymouth-theme-ubuntu-logo. Turns out that when I upgraded from Ubuntu 9.10 to Ubuntu 10.04 RC it never got installed. So after I installed this I got a beautiful splash image!

Hope this help somebody!

Cheers

---

### Post by eorisis on 2010-05-08
I was about to post about the above link 10 minutes ago, well it did the job and worked fine.

I also had another issue possibly caused by the startup-manager application after changing resolution there etc. I was getting this message right after I would choose to boot ubuntu from grub:

[B][Linux-bzImage, setup=0x3400, size=0x3d4860]
vga=769 is deprecated. Use set gfxpayload=640x480x8,640x480 before linux command instead.[/B]

looks like a known bug or something:
[https://bugs.launchpad.net/startup-manager/+bug/483262](https://bugs.launchpad.net/startup-manager/+bug/483262)

so I edited the line:
GRUB_CMDLINE_LINUX=" vga=769"

to:
GRUB_CMDLINE_LINUX=""

I think this is how it was before, I am not sure.

Now I only get this message right after grub boot:

[B][Linux-bzImage, setup=0x3400, size=0x3d4860]
[Initrd, addr=0x373fe000, size=0xbf16b0][/B]

everything else related to the boot screen is perfect.
anyone knows if the above message is normal ?

---

### Post by G4MAC on 2010-05-08
> **philinux said:**
> You can try this. If this does not work then reverse it.

```
gksu gedit /etc/initramfs-tools/conf.d/splash
```

and add this option FRAMEBUFFER=y, save the file.
Then

```
sudo update-initramfs -u
```

Reboot to see if it works. No guarantees.

There is a bug open.
[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540801](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540801)

The solution somewhat worked, before on startup after grub it would have a blank screen with a blinking cursor for around 10 seconds and then change resolution still with the blinking cursor for another 10 seconds; after this an unanimated Plymouth screen shows up for just a few seconds and I am in with automatic login.  With the fix, the blinking screens have been shortened to a couple seconds a piece, but the remaining time is replaced with an animated Plymouth screen till the unanimated shows up. Boot time total is around 26 seconds, way longer than it should be with the equipment I have.

---

### Post by G4MAC on 2010-05-09
Here is my bootchart; hopefully this can help somehow, I have a hard time understanding it.

---

### Post by kenweill on 2010-05-10
> **NoFearDJB said:**
> This website's solution worked for me!
[http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/](http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/)

Thanks mate.
Worked for me too.

I used to have 1024x720 boot screen resolution until I installed the proprietary drivers of nvidia, changed to something like 800x600.

The procedures found on the link worked. I now got 1024x720 24bit boot screen resolution.

---

### Post by yakinikku on 2010-06-02
oddly enough i dont get this problem at startup on my mini 9, perhaps its because it is dual booting and grub shows?  i dont know.

however, on my mini 10 i get this problem.  i am going to try the solutions posted here when i get home.  

does anyone have a solution for the verbose mode messages that show for a little bit during shutdown?  i get that on both of my laptops and i would like to fix it. TIA.

---

### Post by emagine on 2010-06-02
> **yakinikku said:**
> oddly enough i dont get this problem at startup on my mini 9, perhaps its because it is dual booting and grub shows?  i dont know.

however, on my mini 10 i get this problem.  i am going to try the solutions posted here when i get home.  

does anyone have a solution for the verbose mode messages that show for a little bit during shutdown?  i get that on both of my laptops and i would like to fix it. TIA.
I completely  agree.  I would like to get rid of that.  Write back if you figure it out.

---

### Post by yakinikku on 2010-06-03
an update, this worked for the boot screen on the mini 10.  there still is a bit of time where i get the blinking cursor but i assume thats due to the video drivers not being loaded just yet.  i set the grub timeout to 0 just in case but it didnt change anything.

still would like to figure out how to prevent the verbose messages from showing before the shutdown screen.  still researching it.  if anyone has any tips that would be awesome.

---

### Post by green69 on 2010-06-09
> **philinux said:**
> You can try this. If this does not work then reverse it.

```
gksu gedit /etc/initramfs-tools/conf.d/splash
```

and add this option FRAMEBUFFER=y, save the file.
Then

```
sudo update-initramfs -u
```

Reboot to see if it works. No guarantees.

There is a bug open.
[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540801](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540801)

This solution works perfectly for me! :guitar:

Thanks!

---

### Post by wewa on 2010-09-10
I did this and now I get an error busybox (initramfs) and cannot boot.
I am booting previous kernel.

How do I reverse this?

I deleted framebuffer=y and saved the file, but still no boot.

do I 'rm' the 'splash' file?

Thanks.



> **philinux said:**
> You can try this. If this does not work then reverse it.

```
gksu gedit /etc/initramfs-tools/conf.d/splash
```

and add this option FRAMEBUFFER=y, save the file.
Then

```
sudo update-initramfs -u
```

Reboot to see if it works. No guarantees.

There is a bug open.
[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540801](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540801)

---

### Post by Jetro on 2011-01-23
I had problems with the boot screen after installing the nVidia drivers. I have a Dell Inspiron 9400 with a nVidia 7900 GS Go graphics card, and before activating the driver, the boot screen was fine. After installing it, it became 640x480.

I tried changing this with startupmanager, but it only ended up making things worse. It varied from doubling my bootscreen within a 640x480 with destroyed colours, to flashing momentarily; in general being screwed up.

I would advise everyone to *not* to try startupmanager, as it has limited uses and only screws up your boot screen even further.

The Softpedia article antrunner85 linked to, though, works! :D However it does not work with a widescreen resolution, such as the one I wanted, 1920x1200.

---

