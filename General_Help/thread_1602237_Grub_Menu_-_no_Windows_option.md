---
title: "Grub Menu - no Windows option"
date: 2010-10-21
forum: General Help
---

### Post by pjwilsd on 2010-10-21
I installed Ubuntu onto a separate partition I have.

Now however when i boot up, Grub (v1.98 ) gives m 5 options.

Ubuntu, with Linux 2.6.35-22-generic
Ubuntu, with Linux 2.6.35-22-generic (recovery)
Memory Test (memtest86+)
Memory Test (memtest86+, serial console)
Windows Recovery Environment (loader)

With no Vista option.

I am truly bemused.

When I run the recovery environment however, it runs just my regular vista boot would have. Is this just a name issue? Ideally I would like to have my Vista option back.

Cheers.

---

### Post by Quackers on 2010-10-21
Welcome to Ubuntu Forums :-)
Try selecting the Windows Recovery Environment (Loader) and see if it boots into Windows. Sometimes grub labels Vista wrongly (are you using a Sony Vaio?).
If it boots into the Windows recovery environment just don't continue with booting.

---

### Post by tajiknomi on 2010-10-21
[SIZE=2][I]Check this..

If you installed Ubuntu before you installed Windows, then Ubuntu will not have anything in the grub configuration for Windows. This is where you’ll have to do a bit of manual editing to the grub boot menu file.

If you open the file /boot/grub/menu.lst with the following command:

    sudo gedit /boot/grub/menu.lst

You’ll see a sample section for Windows, which you’ll want to uncomment and add to the boot menu list in whatever position you want it in. (uncomment by removing the #’s)

    # title   Windows 95/98/NT/2000
    # root   (hd0,0)
    # makeactive
    # chainloader   +1

Note that you should also verify that hd0,0 is the correct location for Windows. If you had installed Windows on the 4th partition on the drive, then you should change it to (hd0,3)
[/I][/SIZE]

---

### Post by pjwilsd on 2010-10-21
Thanks for the welcome and cheers for the quick reply.

I have booted into it before and it loads up just as i would expect my regular installation of vista would. So I imagine it's been labeled incorrectly. If that's the case there's nothing to worry about i assume?

As for my machine, the issue is on a Dell inspiron 1545.

---

### Post by Quackers on 2010-10-21
It's just the label then. No problem at all with that. It just looks odd :-)

---

### Post by pjwilsd on 2010-10-21
> **tajiknomi said:**
> [SIZE=2][I]Check this..

If you installed Ubuntu before you installed Windows, then Ubuntu will not have anything in the grub configuration for Windows. This is where you’ll have to do a bit of manual editing to the grub boot menu file.

If you open the file /boot/grub/menu.lst with the following command:

    sudo gedit /boot/grub/menu.lst

You’ll see a sample section for Windows, which you’ll want to uncomment and add to the boot menu list in whatever position you want it in. (uncomment by removing the #’s)

    # title   Windows 95/98/NT/2000
    # root   (hd0,0)
    # makeactive
    # chainloader   +1

Note that you should also verify that hd0,0 is the correct location for Windows. If you had installed Windows on the 4th partition on the drive, then you should change it to (hd0,3)
[/I][/SIZE]


I installed Ubuntu after my Windows installation. 

I just opened the file you suggested and there were no entries in it at all. Just a blank document it would seem.

Also, my partitions are correct, I have Ubuntu in slot 2 and Windows in slot 3. Which is how I specified when installing.

---

### Post by pjwilsd on 2010-10-21
> **Quackers said:**
> It's just the label then. No problem at all with that. It just looks odd :-)

Thanks then. Seems I was getting worried over nothing. I take it there's no way of editing the label?

---

### Post by Quackers on 2010-10-21
As you are using Ubuntu 10.10 and therefore grub2 loader the /boot/grub/menu.lst is empty. This file is not used by grub2. It is a file that was used by grub (in older versions of Ubuntu).
The name can indeed be changed, but it is quite a job to do and you need to be careful. Read here
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

And please make a backup (as advised in the thread) of any files you are going to change) :-)

---

### Post by na5h on 2010-10-21
> Originally Posted by **Quackers**  
It's just the label then. No problem at all with that. It just looks odd 
Yes, it's really nothing to worry about! :) I used to dual boot Vista and Ubuntu and for some reason Vista gets labeled that way...but as Quackers said, you can change the label if it annoys you.

---

