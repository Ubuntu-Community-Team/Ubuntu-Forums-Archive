---
title: "Grub 2 Troubles. How can I remove it?"
date: 2010-09-06
forum: General Help
---

### Post by RomanP on 2010-09-06
Hi everyone!

I need help getting rid of grub 2. If you need the full story read on. Otherwise go to the red text. Sorry if the description is too long...


I recently purchased a new netbook with windows xp and installed ubuntu on it on a different partition. So I had XP and ubuntu dual booting. Later I figured I didn't want ubuntu any more so I formatted the ubuntu partition. Then I couldn't boot and got the grub rescue> prompt. So I booted off a usb key with ubuntu and reinstalled grub. I booted into windows an in an attempt to replace grub with the XP bootloader, I used EASYBCD. Now when I boot I get the grub> prompt and trying to use that to boot into windows, but I get the NTDLR not found error. My netbook has a partition with windows PE on it which runs symantec ghost. 
Ghost restored XP and its bootloader but grub still haunts me.

[COLOR="Red"]Current Situation:[/COLOR]

Now when I get the grub> prompt again I must do 

root (hd0,1)
chainloader +1
boot

And windows xp starts up.

I'm really tired of this and I want Grub gone. how can I achieve this and restore windows bootloader??

Sorry if its a bad description, I'm not much of a forum guy =(

---

### Post by vttay03 on 2010-09-06
I used EasyBCD to restore a Vista bootloader awhile back...it was pretty straightforward but I can't remember exactly what I did.  I think if you basically boot into XP and install the program, you should be able to figure it out pretty easily...I think there's some type of option like 'Restore Bootloader' or something.  Link is below:

[http://neosmart.net/dl.php?id=1]("http://neosmart.net/dl.php?id=1")

---

### Post by RomanP on 2010-09-06
Thank you very much Grub is gone. But now I have a new question - I still want to install linux, but I want to experiment with different distros. I picked a new one and when I install it I'm 99.9% sure grub will be back. Will it be safe to use the same method to remove it again?

---

### Post by vttay03 on 2010-09-06
Theoretically, yes, you can use this same method to restore the Windows bootloader each time.  However, if you're really that interested in exploring different distros I'd recommend getting a second hard drive and using that to test different distros.

---

### Post by vttay03 on 2010-09-06
I guess I should also mention that if you did decide to get a second hard drive to install and test distros on, you'd want to install the bootloader to that hard drive, not your windows hard drive.  A lot of times the bootloader will install to your first hard drive as a default, so it might still install to your windows hard drive.  For example, on an Ubuntu install the last page has an 'Advanced' button you click to specify where to install the bootloader.  It will usually default to /dev/sda or the first hard drive in your computer...

---

### Post by RomanP on 2010-09-07
Well thanks for the warning, but I doubt that I'm going to be getting a second drive as I'm using a netbook. Good to know either way thanks very much for your Help guys.

---

### Post by muteXe on 2010-09-07
> **RomanP said:**
> Thank you very much Grub is gone. But now I have a new question - I still want to install linux, but **I want to experiment with different distros**. I picked a new one and when I install it I'm 99.9% sure grub will be back. Will it be safe to use the same method to remove it again?

Can I suggest running a virtual machine within windows?  This way you can run/try as many flavours of linux as you want without having to partition and install until you've found the one you like.

---

