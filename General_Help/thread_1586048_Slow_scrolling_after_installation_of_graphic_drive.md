---
title: "Slow scrolling after installation of graphic driver(ATI)"
date: 2010-10-01
forum: General Help
---

### Post by stRunF on 2010-10-01
[RIGHT]Hi..
[/RIGHT]
 I've just installed a driver for ATI HD 4850, and I have a huge delay while scrolling, or when entering a folder which contains more files.(While scrolling down/up, vertical lines go down or up slowly, refreshing the image, 1 line/time if I noticed well.. takes like 2-3 secs to 'clear' the image..)
I'm a total beginner at ubuntu, so please reply in standard language, or explain what to do :D
I don't know if I installed the ATI driver properly, I just found that guide on the net..
Any help with this?:confused::confused:
Thanks in advice :)

@PC details, if any needed:

2.7 GHz, AMD dual 5700+
4GB of RAM (2x2GB)
320GB HDD atm

---

### Post by stRunF on 2010-10-01
bump

---

### Post by stRunF on 2010-10-01
any help?:(

---

### Post by stRunF on 2010-10-01
forgot to mention, delay even while moving windows..
i've installed another driver also, but not change..
things worked before this, but ati driver was erased with some other problems, before that my brother installed it..
@i've uninstalled the driver, now it again runs smoothly, but i don't have ATI installed again..
someone can link me from where i can properly install this driver?
installed it from [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English) , again it runs slow..

---

### Post by stRunF on 2010-10-01
I would really use some help with this.. anyone?

---

### Post by andrewthomas on 2010-10-01
What version of ubuntu are you running?

---

### Post by stRunF on 2010-10-01
> **andrewthomas said:**
> What version of ubuntu are you running?
You are using Ubuntu 10.04 LTS
                - the Lucid Lynx

---

### Post by stRunF on 2010-10-01
any help? sorry for impatience, but I would go out after this is fixed:popcorn:

---

### Post by andrewthomas on 2010-10-01
Try using jockey to install fglrx.  It is in the Administration menu.

It may be labeled differently, since I am using 10.10

---

### Post by stRunF on 2010-10-01
great got another problem now..
configured the driver, now ubuntu won't boot..
when it boots the welcome sound is played, then all is purple(desktop~ colour)
should i uninstall ati and reinstall it? and if so, how to do it from livecd?

---

### Post by andrewthomas on 2010-10-01
> **stRunF said:**
> 
@**i've uninstalled the driver**, now it again runs smoothly, but i don't have ATI installed 
Are you sure you completely uninstalled the previous version?

I would also delete any remaining xorg.conf files and regenerate once the driver is installed properly.

---

### Post by stRunF on 2010-10-01
> **andrewthomas said:**
> Are you sure you completely uninstalled the previous version?

I would also delete any remaining xorg.conf files and regenerate once the driver is installed properly.
i've encountered another problem..
installed ati AGAIN, but it was for 9.10 ubuntu.. i wrote some configuration command, and now ubuntu doesn't boot.
the startup sound does play, but all remains violet/pink , and desktop doesn't appear.
my question now, how to uninstall ati driver from a LiveCD?
or should I just simply delete all the xorg.conf files and restart?
or what to do?
thanks for your replies btw :D rly apreciate it

---

### Post by andrewthomas on 2010-10-01
You would have to do it inside a chroot

[http://ubuntuforums.org/showpost.php?p=8883297&postcount=3](http://ubuntuforums.org/showpost.php?p=8883297&postcount=3)

---

### Post by andrewthomas on 2010-10-01
> **stRunF said:**
> 
or should I just simply delete all the xorg.conf files and restart?
or what to do?
thanks for your replies btw :D rly apreciate it
Delete the config and restart

---

### Post by stRunF on 2010-10-01
> **andrewthomas said:**
> You would have to do it inside a chroot

[http://ubuntuforums.org/showpost.php?p=8883297&postcount=3](http://ubuntuforums.org/showpost.php?p=8883297&postcount=3)
should I enter those command lines in a terminal then?
thanks again

---

### Post by stRunF on 2010-10-01
> **andrewthomas said:**
> Delete the config and restart
okey, will try that.. and what about the chroot?

---

### Post by andrewthomas on 2010-10-01
You have to know what partition is your / partition then enter the top set of commands 

then uninstall the driver. 

then enter the bottom set of commands.

I usually just copy and paste the commands one at a time.

---

### Post by stRunF on 2010-10-01
> **andrewthomas said:**
> You have to know what partition is your / partition then enter the top set of commands 

then uninstall the driver. 

then enter the bottom set of commands.

I usually just copy and paste the commands one at a time.
heh.. this is too fast for me :D
remained at the part "delete config files"
still trying to get into that directory](*,)
ok.. got into that directory, can't delete them, permission denied..
i'm trying that chroot now anyways

---

### Post by andrewthomas on 2010-10-01
mount your / partition from the liveCD

then the file should be at 

/etc/X11/xorg.conf

---

### Post by stRunF on 2010-10-01
ok entered chroot, deleted files, what now?
@yes deleted them, didn't know what that chroot is for but found out now, it gives acces..
deleted all xorg.conf files, should i reboot now?

---

### Post by andrewthomas on 2010-10-01
make sure you have no xorg.conf and reboot

You should then be using the radeon driver.

What command did you use to uninstall the fglrx driver?

---

### Post by stRunF on 2010-10-01
> **andrewthomas said:**
> make sure you have no xorg.conf and reboot

You should then be using the radeon driver.

What command did you use to uninstall the fglrx driver?
i didn't uninstall the driver from LiveCD,
just deleted those xorg.conf files.
rebooted, still the same.. pink/purple background, no change basically..
any tips left?:<
(sry for long responding time, was waiting for LiveCD to boot..)
is it a way to uninstall ati driver from an ubuntu Live CD? if it is, then how?

---

### Post by stRunF on 2010-10-01
bu/\/\p

---

### Post by stRunF on 2010-10-01
any help?

---

### Post by stRunF on 2010-10-01
so, my new problem is, that when ubuntu boots, all is blank, with a background color similar to the desktop's..
this is due to some ati graphic driver updates, which i installed before i restarted the pc, and it became like this.
now i deleted xconf files from etc/x11 ,but it's still not working..
i would like to know how to uninstall this from livecd, or how to go in safe mode to uninstall it.
thx in advice

---

### Post by stRunF on 2010-10-01
ok, problem solved
booted in safe mode, uninstalled driver
booted normally, and installed driver from System->Administration->Hardware Drivers.
after reboot it all worked.
thx for you ideeas and time Andrewthomas

---

