---
title: "slow boot time"
date: 2010-10-14
forum: General Help
---

### Post by 16sinker on 2010-10-14
I've got two laptops running Ubuntu. Both have had Lucid installed from the live cd. I have upgraded one of them to Maverick. Both distributions are running great after they boot up, but I haven't experienced any faster boot times with either distibution. Both boot to Bios and then the screen goes black with a  blinking cursor in upper left corner of the screen. The black screen remains for 30 to 45 seconds and then I get the Ubuntu splash screen for maybe 5 seconds, and then desktop. Why am I not seeing faster boot times? I realize 45 to 60 seconds is good compared to other os's, but I anticipated much faster boot times. Shut down on the other hand is quite fast at maybe 5 to 10 seconds. Does anyone else get this black screen on boot? Seems like wasted time cause I can't tell what's going on during the time there is a black screen. This is not a real big deal breaker, as I don't reboot very often, but I just wonder why bootup isn't faster.

---

### Post by Megaptera on 2010-10-14
Is it that 'Plymouth' isn't working?After BIOS and before black screen, Do you get a purple screen with'Ubuntu' written in white with a line of blinking dots underneath?

---

### Post by 16sinker on 2010-10-14
> **Megaptera said:**
> Is it that 'Plymouth' isn't working?After BIOS and before black screen, Do you get a purple screen with'Ubuntu' written in white with a line of blinking dots underneath?
No I don't get that screen after bios. Just 35 to 40 seconds of black screen, then the Ubuntu screen with the dots loading for about 5 seconds.  Then I'm in my desktop.

---

### Post by 16sinker on 2010-10-14
I've checked Synaptic and Plymouth is installed but is evidently not working. How do I enable Plymouth?

---

### Post by Megaptera on 2010-10-14
You could try this?

[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

---

### Post by 16sinker on 2010-10-14
> **Megaptera said:**
> You could try this?

[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)
Well yes, that took care of the problem. Thanks for the link. I'll mark this solved.

---

### Post by Megaptera on 2010-10-15
You're welcome!

---

### Post by New00Folder on 2011-03-20
> **Megaptera said:**
> You could try this?

[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)


Hi Megaptera! Any chance you know how to totally undo the stuff described on the page you suggested.
What is the default entry in [COLOR=#008080]* /etc/initramfs-tools/conf.d/splash?*[/COLOR]
I'm unable to post any comment there.
I'd like to know more about putting
```
[COLOR=#008080]*GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1280x1024-24,mtrr=3,scroll=ywrap"*[/COLOR]
```in /etc/default/grub. I changed the resolution to 1280x800 which is the resolution of my screen. What about other options?
Though the splash screen didn't take long to appear but stayed for a longer time and I got a terminal instead of GDM. I changed the entry back to "quiet splash" and updated grub.cfg. GDM is back on reboot but I want to make sure that nothing else got screwed.

---

