---
title: "Last shot before uninstalling for good"
date: 2011-06-25
forum: General Help
---

### Post by Rocktman2 on 2011-06-25
I've had Ubuntu installed in a dual boot environment (separate hd) with Win XP since Ubuntu 6.x LTS. I've wanted to switch to Ubuntu from XP for years, but the peripheral support just wasn't there until 9.x LTS (I think it was). When my Ubuntu upgraded to 10.04, my NICs stopped working while I was tweaking the settings (something I've always done) & they never worked after that. So I left Ubuntu last year & hadn't been back.

I recently D/L'd 11.04 Kubuntu & decided to try it over Ubuntu, but it installed an incompatible video driver (last night). I had 11.04 Ubuntu & installed it over Kubuntu, but that also installed an incompatible video driver. In the forums I read a suggestion to a poster to go back to 10.04 LTS & since I had the CD, I didn't have anything to lose at that point (I see Canonical now charges for the CDs. Bummer!). It seemed to install OK (didn't have time to check out everything, though). 

Like all other versions, it put XP at the bottom of the boot menu (if it didn't delete it entirely, as 1 upgrade did) & I'd always been able to edit menu.lst to rearrange the boot order. However, there doesn't appear to be a menu.lst anymore. It seems to have been replaced by config.grub, if I'm correct & I'm unable to save my edits even using sudo.

I understand the need for security. I've been in IT for a very long time & even have security certs. But I must be losing my geekiness in my "old age" as I just don't have the desire to jump through all these hoops anymore just to make some changes. I'm just too frustrated at this point & if I can't get the boot order rearranged, I'm probably going to uninstall Ubuntu & call it a day. M$ wins (pun intended).

Can anyone give me some help? Thnx in advance.

---

### Post by haqking on 2011-06-25
[http://www.howtogeek.com/howto/17787/clean-up-the-new-ubuntu-grub2-boot-menu/](http://www.howtogeek.com/howto/17787/clean-up-the-new-ubuntu-grub2-boot-menu/)

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by Belfast Food on 2011-06-25
Well i don't know much about changing options, modifying and that stuff, but i have a pretty good idea of what to say for your "last" shot of Ubuntu.
Delete everything from your HDD, and don't use those sloppy programs that will turn off with the computer in the middle of it, but an entier HDD deletion from boot, ( save your files first of course )
And then start clean, no problems - just enjoying your new clean system.
But as i may/may not understand, you can't access XP?
Then try to mess with the boot options ( in boot ) i can't think of that getting any worse than not being able to boot one of your OS's, then again, if it does get worse, try the first thing i said.

Maybe you won't give this a chance, but i know it would be a good thing to keep Ubuntu even if you don't use it too much. Just in case.

( probably didn't help, but got that out of me)

---

### Post by pastalavista on 2011-06-25
> **Rocktman2 said:**
> [snip]....
 if I can't get the boot order rearranged, I'm probably going to uninstall Ubuntu & call it a day. M$ wins (pun intended).

Can anyone give me some help? Thnx in advance.

Install StartupManager... makes it very simple ```
sudo apt-get install startupmanager
```

---

### Post by goldshirt9 on 2011-06-25
i could use that link thanks.:)
can you rename o/s with that as well

---

### Post by Rocktman2 on 2011-06-25
Thanks, haqking, your links provided the answer I needed. I installed Grub Customizer & it made rearranging the boot order a breeze. Instructions can be found at [http://tinyurl.com/5sx68g2](http://tinyurl.com/5sx68g2) for those interested in it.

---

