---
title: "Black Screen between GRUB and Ubuntu loading screen"
date: 2010-05-01
forum: General Help
---

### Post by antitoxic on 2010-05-01
Hello,
I don't know whether it is a normal behaviour but the black screen from the moment that I press enter on GRUB to Ubuntu loading screen (dots, illuminated one by one in 10.04) is far more than the actual ubuntu loading.
Is it normal to have such long delay after the choice from GRUB to the Ubuntu loading screen ?

I will give you any debug data just tell me what I need to provide and if possible how.

---

### Post by chriswyatt on 2010-05-01
I've got the same thing, have you got NVidia's official drivers installed?

---

### Post by dino99 on 2010-05-01
nothing is perfect at time but:

sudo dpkg-reconfigure gdm
sudo dpkg-reconfigure plymouth

sudo dpkg --configure -a

might help a little

---

### Post by clhsharky on 2010-05-01
HI antitoxic

Theres a 10sec.timer in grub to let you enter at startup. Can be changed in grub.

Sharky

Sorry I see your starting at selection of grub. I haven't seen grub in so long, I hardly see the dots any more. Start button till on Internet <20sec.

---

### Post by antitoxic on 2010-05-01
Hello,
@chriswyatt I have DELL laptop. I'm not using nvidia video card.
@dino99 It didn't change anything
@clhsharky I'm not talking about GRUB selection timeout.

I still have this huge amount of time where screen is simply black.
This time period starts [COLOR=Red]**after**[/COLOR] GRUB and continues up to the point the ubuntu logo shows up with the dots.
Ubuntu logo splashscreen is very quick (probably 2 seconds) and then the login screen.
The black screen period of time is in the period of 20-40 seconds.

I'm using a laptop with external monitor.
**I found something out:**
After GRUB main monitor is black, as if no output is fed to it (no active pixels), [COLOR=Black]**but**[/COLOR] the laptop monitor shows a [COLOR=Red]**blinking white underscore cursor**[/COLOR]?

Does any of this helps ?
My graphic card is the built in the DELL laptop: Intel 945GM

---

### Post by andyanderso on 2010-05-01
I am also having this problem as are folks in this thread:[http://ubuntuforums.org/showthread.php?t=1467365&highlight=long+boot]("http://ubuntuforums.org/showthread.php?t=1467365&highlight=long+boot")

---

### Post by antitoxic on 2010-05-01
No, @andyanderso,** it is not** the same problem. 
I have 20-30 seconds of blinking cursor after the grub. 
They only thing enabled from my BIOS boot sequence is the hard disk.

---

### Post by andyanderso on 2010-05-01
Sorry...Thought it sounded similar enough to maybe combine forces...

---

### Post by antitoxic on 2010-05-03
I've read about the blinking cursor problem. 
I don't have blinking cursor when I load Windows from GRUB.
This is my linux grub2 entry:
```
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set fb9d2ffc-6b70-404a-ad68-915f6e54db44
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=fb9d2ffc-6b70-404a-ad68-915f6e54db44 ro  vga=795  quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
```Windows:
```
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 9ce0fbc7e0fba624
    drivemap -s (hd0) ${root}
    chainloader +1
}
```These are the auto-generated from grub2 entries. I haven't modified them

Does anyone know why does this blinking cursor appear ?

---

### Post by hpg on 2010-05-07
antitoxic,

I am experiencing exactly the same probleme as you:

My machine: Ibm thinkpad, T43p
I'm booting ubuntu linux lucid from external HD which is connected via usb.

Same as you:
After selecting linux boot kernel in grub boot menu (by hitting enter) there does not seem to happen anyting for about 10...15 seconds (though, the LED on the HD blinks, indicating some sort of activity....) 

After that time, booting starts normally, however the graphical screen with the dots only appears shortly before the appearence of the authentication screen.

In /var/log/syslog nothing seems to indicate any problems regarding the kernel.

Karmic did not have this problem. It showed up only after upgrading to lucid. 

Any new thoughts on this?

Regards
Hanspeter

---

### Post by john newbuntu on 2010-05-07
```
sudo update-alternatives --config default.plymouth
sudo update-initramfs -u

``` should take care of it.  See the sticky thread for more details.

---

### Post by Xorlathor on 2010-05-07
> **antitoxic said:**
> Hello,
**I found something out:**
After GRUB main monitor is black, as if no output is fed to it (no active pixels), [COLOR=Black]**but**[/COLOR] the laptop monitor shows a [COLOR=Red]**blinking white underscore cursor**[/COLOR]?

Does any of this helps ?
My graphic card is the built in the DELL laptop: Intel 945GM

I'm having the exactly same problem as you - after I choose the GRUB option there's a black screen with a white underscore cursor that blinks for 10~15 secs...

---

### Post by Xorlathor on 2010-05-07
> **john newbuntu said:**
> ```
sudo update-alternatives --config default.plymouth
sudo update-initramfs -u

``` should take care of it.  See the sticky thread for more details.

Running that code results in the following output:

```
robert@robert-laptop:~$ sudo update-alternatives --config default.plymouth
There is only one alternative in link group default.plymouth: /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth
Nothing to configure.
robert@robert-laptop:~$ sudo update-initramfs -u
update-initramfs: Generating /boot/initrd.img-2.6.32-22-generic
robert@robert-laptop:~$ 

```I'm going to restart and see if there's a new kernel and if it does anything...

_**UPDATE:**_

Rebooted and that code had no effect whatsoever - same white underscore cursor that blinked, and same ~15 second pause between the GRUB menu and my desktop.

---

### Post by birdmanuk on 2010-05-07
I too have the same problem, from grub, I have 30 seconds of flashing - in the top left corner. 

As soon as I see the ubuntu logo, it's 7 seconds till the login window.

Wish that was how fast it was from poweron.

I also see the same problem on my Lenovo T61p

---

### Post by sgage on 2010-05-07
I have 15 seconds of black screen from grub until the ubuntu splash, but then only 3-4 seconds until complete desktop (autologin). Bootchart shows 18-19 seconds boot time.

The ubuntu splash (the thing with the dots) shows only for about 1 second, and then a second or two more and I'm at my desktop.

So I am very happy with my boot time, but still, that black 15 seconds is strange...

This is with latest proprietary nvidia drivers/GeForce 8500 GT.

---

### Post by john newbuntu on 2010-05-08
Ok, try this:
 [FONT=Arial][SIZE=2]```
gksu gedit  /etc/initramfs-tools/conf.d/splash
```[/SIZE][/FONT][FONT=monospace][FONT=Arial][SIZE=2]
In the file that opens up, add[FONT=monospace]:
  [/FONT][/SIZE][/FONT][/FONT]FRAMEBUFFER=y
 [FONT=Arial][SIZE=2]and save it[/SIZE][/FONT].  Then run:
 ```
sudo update-initramfs -u
```This is from:
[http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475)

---

### Post by antitoxic on 2010-05-08
Thank you, John,
The last snippet worked. :)
However I read in the bug comments it is a bit dirty workaround and it might bring some performance overhead.
Some people also suggested adding some extra parameters to kernel start in GRUB:```
video=uvesafb:mode_option=1280x1024-32

```[quote="fireandfuel"]After the update to lucid beta2 vga16fb was set per default. (nvidia  driver 195.36.15)
But vga16fb only support low resolutions with 16 colors.[/quote]

I hope this helps other users for a smooth booting experience.

It is odd that it was supposed to be fixed in the RC of 10.04 and some suggestions were made that video drivers must be loaded first.

---

### Post by woodyg on 2011-11-01
> **john newbuntu said:**
> Ok, try this:
 [FONT=Arial][SIZE=2]```
gksu gedit  /etc/initramfs-tools/conf.d/splash
```[/SIZE][/FONT][FONT=monospace][FONT=Arial][SIZE=2]
In the file that opens up, add[FONT=monospace]:
  [/FONT][/SIZE][/FONT][/FONT]FRAMEBUFFER=y
 [FONT=Arial][SIZE=2]and save it[/SIZE][/FONT].  Then run:
 ```
sudo update-initramfs -u
```This is from:
[http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475)

I'm on Xubuntu 11.10 and I used to have 20 sec of black screen after the grub menu and 3 sec of splash before the login. This fix cut the black screen to about 10 sec... so a nice little improvement. I still have 10 sec of black screen though. Any idea how that can be sorted?

What will

```
video=uvesafb:mode_option=1280x1024-32
```do? (antitoxic's suggestion)

---

### Post by casey-jones on 2011-12-22
> **woodyg said:**
> I'm on Xubuntu 11.10 and I used to have 20 sec of black screen after the grub menu and 3 sec of splash before the login. This fix cut the black screen to about 10 sec... so a nice little improvement. I still have 10 sec of black screen though. Any idea how that can be sorted?

What will

```
video=uvesafb:mode_option=1280x1024-32
```do? (antitoxic's suggestion)

i have the  same problem with xubuntu 11.10

---

### Post by md2406 on 2012-02-06
I am having the same problem with ubuntu 10.04. My black screen, between grub and Plymouth logo, takes more than a minute. I have followed many threads including this one and the one here [http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/]("http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/") but no luck for me. 
I am open for any suggestion that helps to fix annoying splash problem.

---

