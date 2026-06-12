---
title: "Ubuntu and GRUB Predicament"
date: 2010-01-03
forum: General Help
---

### Post by B-Witty on 2010-01-03
Hello everybody,

I may have just made a big blunder, but anyway my situation is that I set the delay in GRUB to 1 second (which I thought would suffice if I needed to use GRUB) because my Windows Vista has a loader as well. I did this in case I needed to go to Vista I could just easily access it without going through GRUB and then going through Vista's loader. But the problem is that the delay for GRUB is too short for the menu to come up and pressing any keys (like Up and Down and Esc) have no effect to pause or control GRUB. And it turns out that the Vista loaders doesn't properly load Ubuntu (aka just black screen). 

So I need some advice. Is there anyway I can change GRUB's delay from Vista or boot my Ubuntu so I can natively change the delay value? I've tried some ext2/ext3 viewers in windows with no avail (because they don't work right). 

Thanks for any help,
~BW

---

### Post by Leppie on 2010-01-03
you can access your ubuntu system using a linux livecd (for instance the ubuntu installation cd).

it's usually better to skip windows os menus and use grub to boot the different os's with. microsoft software handles microsoft software best (and doesn't always do it that well).

---

### Post by B-Witty on 2010-01-03
Thank you, I tried that, but how would I login on to my account?

The CD allows only a demo of ubuntu, therefore, my permissions on that account don't allow me to write to my ubuntu side. How would I logon on to my account to gain permissions to edit the GRUB boot delay?

---

Oh yeah... my boot delay is set to 1, since I thought that would give me enough time to boot differently but it appears that it takes at least 2 seconds for the menu to appear...

Thanks again,
~BW

---

### Post by Leppie on 2010-01-03
in order to change the boot options in a not-too-complex way, you should first be able to boot into ubuntu.

anyways, if after selecting ubuntu in the windows menu you press an arrow key, or ESC, or "e", you should be able to see the grub menu without timeout. don't wait for the menu to show up and just keep pressing that key repeatedly.

---

### Post by B-Witty on 2010-01-03
Booting from Vista's loader, Ubuntu never boots correctly. The Ubuntu icon comes up for a few minutes and then black scree. Also when booting Ubuntu from Vista's loader and hitting ESC only brings up different modes for booting Ubuntu (which none of them work) and doesn't show the regular boot options (such as ubuntu, vista, memory test, etc.).

But I got another question. If I reinstalled GRUB would it overwrite its current settings? Because if it did then I could just reinstall it from a floppy.

Thanks much more,
~BW

---

### Post by Leppie on 2010-01-03
reinstalling grub without modifying the configuration files, normally would only install it to your hard drives mbr.
however, the installation process does not only consist of installing into the mbr.

---

### Post by garvinrick4 on 2010-01-03
Do you have sda1 as boot sda2 as Vista OS and sda3 or sda4 as vista recovery and linux
in which ever Vista recovery is not sda3 or sda4. Or do you have a extended partition with
linux and a swap residing in the extended as logical. Or you could have seperate / and /boot and /home logical partitions. I know you just want to fix grub and here is a link but if you do
not understand Primary, Extended and Logical partitions and MBR or what I have just written life will be a whole lot easier if you take an hour and read up on partitioning drives. Below is a link on grub2 and below that a old one on partitioning but easy to understand. I am a long way from being a whiz kid but google and read, google and read, google and read helps me a lot to understand what is going on, most of the time.  Have a nice day.



[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)




[http://www.pcguide.com/ref/hdd/file/structPartitions-c.html](http://www.pcguide.com/ref/hdd/file/structPartitions-c.html)

---

### Post by dcstar on 2010-01-03
> **B-Witty said:**
> Hello everybody,

I may have just made a big blunder, but anyway my situation is that I set the delay in GRUB to 1 second (which I thought would suffice if I needed to use GRUB) because my Windows Vista has a loader as well. I did this in case I needed to go to Vista I could just easily access it without going through GRUB and then going through Vista's loader. But the problem is that the delay for GRUB is too short for the menu to come up and pressing any keys (like Up and Down and Esc) have no effect to pause or control GRUB.


The Shift Key opens the Grub2 menu, hold it down as the system boots.

---

### Post by B-Witty on 2010-01-11
Thanks all, I've fixed my problem now.

---

### Post by miniyak on 2010-01-11
I know you have all ready solved the problem but just for others stumbling across this

you can install software in the live environment

so once in live enviornment, reload the software sources, w/ system>admin>software sources (in karmic hmph..)

then> Applications> software center> start-up manager 

install start-up manager

then edit with start-up manager (in the admin menu)

Or

make a "super ubuntu" live cd or usb

startup manager is include along with a few other interesting things

---

