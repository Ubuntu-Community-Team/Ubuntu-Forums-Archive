---
title: "LILO works, Grub is trash."
date: 2010-05-04
forum: General Help
---

### Post by brucewestfall on 2010-05-04
I upgraded to 10.04, then on reboot, grub refused to work.  I picked another partion and installed 9.10.  Grub still didn't work (file cannot be read, must load kernel first..)  So I got Debian 5.  

Debian will boot with LILO, grub will boot absolutely nothing.

I am a Linux and Ubuntu fan, but if grub was my first exposure to open source, I am afraid of what operating system would be my choice.

Why has grub caused me problems since it replaced LILO?  I NEVER had any problems with LILO, but grub is the only real problem I've ever faced.

Right now, I cannot get LILO to see /dev/sda6, where UBUNTU 9.10 is installed.  

Any ideas????

---

### Post by cariboo on 2010-05-05
Why not fix grub instead of installing several other operating systems? Have a look at [this]("https://help.ubuntu.com/community/Grub2") document, scroll down to Reinstalling GRUB 2

---

### Post by brucewestfall on 2010-05-05
I have tried fixing grub following all the recommendations I could find.  The thing that bugs me is that this has happened several times over the past couple years.

Especially when I only had one computer it gets really frustrating when grub stops working for no apparent reason.  This last time I still have no idea why it did what it did.

I finally fixed it by installing a different hard drive and doing another fresh install.  Even from the grub prompt I could not get it to cooperate.

I'm wondering if it has something to do with the SATA drive I have.  It's just enormously frustrating losing several days of work and even a reinstall of the system with an allegedly new copy of grub doesn't fix anything.

I do appreciate the improvements over LILO, but what kind of improvement is it when grub refuses to work?  Even when I tried a Debian install with the option to use grub, it failed.  LILO was the only thing that would get an installed operating system going again.

OK, </venting>

I will print out the relevant info from the page you referred to and hope I never need it again.

Thanks.

---

### Post by brucewestfall on 2010-05-10
Ubuntu is absolved again!

The whole problem was HARDWARE.  I was so worried about Linux messing up, but it looks like it is something on the motherboard, or perhaps the BIOS itself.

My apologies to all who tried to help me.

Unfortunately, I must go apologize in another section of the forum, since there were several problems going on at the same time.

Please forgive me.

(The problem here came from LILO working with fewer needed files.  GRUB could not find the files it needed due to a BIOS error.  I do still like LILO better, but my apologies again to the GRUB creators and maintainers, along with anyone else I offended.)

---

### Post by -humanaut- on 2010-05-10
Just wondering what was the BIOS problem?

---

### Post by Padapwa on 2010-05-10
> **brucewestfall said:**
> I upgraded to 10.04, then on reboot, grub refused to work.  I picked another partion and installed 9.10.  Grub still didn't work (file cannot be read, must load kernel first..)  So I got Debian 5.  

Debian will boot with LILO, grub will boot absolutely nothing.

I am a Linux and Ubuntu fan, but if grub was my first exposure to open source, I am afraid of what operating system would be my choice.

Why has grub caused me problems since it replaced LILO?  I NEVER had any problems with LILO, but grub is the only real problem I've ever faced.

Right now, I cannot get LILO to see /dev/sda6, where UBUNTU 9.10 is installed.  

Any ideas????


Yeah, i have an idea, reinstall Ubuntu.

Obviously the Grub2 installation didn't complete proper and the Ubuntu installation was not successful or you'd be able to see it via LILO (which is pretty much never updated anymore, i like it but it's ancient by now).

So PEBKAC, reinstall and try again.

It could be that you made a mistake and did something wrong during your first install, it seems likely to me that that is the case since you seem very impatient and would probably just click anything without looking.

---

### Post by Padapwa on 2010-05-10
> **brucewestfall said:**
> Ubuntu is absolved again!

The whole problem was HARDWARE.  I was so worried about Linux messing up, but it looks like it is something on the motherboard, or perhaps the BIOS itself.

My apologies to all who tried to help me.

Unfortunately, I must go apologize in another section of the forum, since there were several problems going on at the same time.

Please forgive me.

(The problem here came from LILO working with fewer needed files.  GRUB could not find the files it needed due to a BIOS error.  I do still like LILO better, but my apologies again to the GRUB creators and maintainers, along with anyone else I offended.)

Wow, so you are still going to maintain that it was not your fault? How did you fix the BIOS code? Did you reprogram it yourself?

---

### Post by brucewestfall on 2010-05-10
I have no idea if it was my fault or not.  But it does appear to be a hardware problem.  Several things brought me to this conclusion - once again, perhaps I'm wrong..

First, Grub could not find files needed to boot.  Installation seemed to work, but perhaps either all data was not written, or it could not be read.

Next, my wireless card would not function, even after doing all I could find about how to install it properly (It has worked fine for the last 6 months...)

Also, I could not read files on a drive that was not edited during reinstalls.  That and errors about SATA not working properly.

Finally, the BIOS took about 45 seconds to start.  After unplugging my SATA drive, it seems to be working.

I really need to USE my computer, so I'm not going to experiment anymore for a while - just going to leave it running and WORKING!

What do you think?  Is it a BIOS problem, or maybe a motherboard going bad?  Once I get some things finished I'll try to track down the exact problem.

Again, I am sorry for any confusion I have caused.

---

