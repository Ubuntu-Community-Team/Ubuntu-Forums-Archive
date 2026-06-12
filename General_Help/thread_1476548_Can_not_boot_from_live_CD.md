---
title: "Can not boot from live CD"
date: 2010-05-07
forum: General Help
---

### Post by CommanderOne on 2010-05-07
Hey,

I have a laptop I don't seldom use, which I want to reformat. I decided the best way to do this was to put Ubuntu on it, since I really just need it for web browsing and a bit of downloading, but I can't seem to do it.

Every time I put in a Ubuntu Live CD, it doesn't load at all (which I assume is an issue with the laptop), so I mounted the ubuntu ISO onto a flash drive, and tried to run it off there.

That worked fine to start with, but I could only get as far as the first menu, I couldn't actually get into the live CD to install it, and I can't think of any reason why.

I was wondering if someone might be able to help me out, or suggest some alternatives.

Thank!

---

### Post by Vined Adobo on 2010-05-07
> **CommanderOne said:**
> Hey,

I have a laptop I don't seldom use, which I want to reformat. I decided the best way to do this was to put Ubuntu on it, since I really just need it for web browsing and a bit of downloading, but I can't seem to do it.

Every time I put in a Ubuntu Live CD, it doesn't load at all (which I assume is an issue with the laptop), so I mounted the ubuntu ISO onto a flash drive, and tried to run it off there.

That worked fine to start with, but I could only get as far as the first menu, I couldn't actually get into the live CD to install it, and I can't think of any reason why.

I was wondering if someone might be able to help me out, or suggest some alternatives.

Thank!

I know this reply doesn't really match your issue, but Ill try anyway.
Older machines cannot change the boot order.  You have to look at your BIOS  and see if  your laptop allows you to boot off a CD or a USB disk.  If you can use a CD set it as first boot priority.  If your BIOS can boot from a memory stick, set that as first boot priority.  Perhaps you have already done this.  Some BIOSs will revert to HD first if it tries to boot a CD and doesn't find one.  This is how my BIOS behaves.  If I get no joy booting the CD or memory stick. I return to BIOS settings and set it right again.  It REALLY irritates me when the OS manufacturer or BIOS, or even a lame application  thinks it knows more than I do and changes what I have set.  They should ONLY issue a warning.  Grr!!!

One last question: did you use usp to startup disk creator to populate your usb drive?

I know I probably didn't help, but I thought I'd give it a try.

Regards,
Dave

---

### Post by CommanderOne on 2010-05-07
Hey,

Thanks for your time. 

It should in theory work, because it gives the option and I have run Ubuntu from that laptop in the past, which is why I'm so confused with this issue. I'm given the option to bot from CD, or USB but booting from CD just makes the machine think for a couple of seconds, then boot from the HDD, which makes me think the DVD drive may be suffering issues, perhaps.

When I burn the ISO to a USB drive, it looks like everything is fine, but I just can't click on the button to launch the installer.

Not quite sure about your last question in regards to populating the USB

Thank you again!

---

### Post by oldfred on 2010-05-08
There are some video issues in the Lucid default install. If that is the problem and you get the first menu, use f6 and add nomodeset or some of the other choice. I had to use the nomodeset both on install from USB and first boot, but once I had nvidia installed it works great. Other video cards also have the same issues.

---

### Post by Catharsis on 2010-05-08
Did you check the md5sum of the iso before using it? You might also want to select "check disc for errors" in the menu of your CD. Press any key at the first purple screen to get to the menu.

Do you mind explaining a bit more what exactly happens as you boot the CD or USB? What screens do you see? Where does it hang, and what does the screen look like (i.e. blank, flashing cursor in top-left, etc).

If you have an Intel graphics card, you might also want to try booting with KMS enabled.

From the menu, hit F6 to edit, like above. Then hit Esc so you can edit the text, and replace "quiet splash" with "i915.modeset=1". 

If neither "nomodeset" nor "i915.modeset=1" work, you can try replacing it with "xforcevesa noapic noapci nosplash irqpoll" instead.

---

### Post by nikefalcon on 2010-05-08
> **Catharsis said:**
> 

If you have an Intel graphics card, you might also want to try booting with KMS enabled.


please check this: [http://ubuntuforums.org/showthread.php?t=1476182](http://ubuntuforums.org/showthread.php?t=1476182)
What is KMS and how do you enable it??

---

### Post by nikefalcon on 2010-05-09
Ok everyone. here's a fix!
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

---

