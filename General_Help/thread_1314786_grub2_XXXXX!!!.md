---
title: "grub2 XXXXX!!!"
date: 2009-11-04
forum: General Help
---

### Post by Cyclone42 on 2009-11-04
Sorry, I have to vent about this.  I simply cannot belive that people can replace grub with something so overtly user-hostile as grub2.  All I want to do is simplify the grub boot-screen so there are only two options -- Ubuntu and windows, with simplified descriptions of each.  Right now, the boot screen has about 563 different options for just Ubuntu alone, with intimidating-looking variations on each.  The people who wrote this monster piece-of-XXX should look into the MythTV mailing lists and read about something there called the "Wife Acceptance Factor".  How is she supposed to understand that stuff when booting my computer from Ubuntu to Windows?

Anyway, I was trying to figure out how to configure this thing.  First I noticed that /boot/grub/menu.lst is obviously no longer used.  I discovered grub.cfg in the same directory, but it is freaking SCRIPT, not a configuration file, and says "DO NOT EDIT" at the top.  The script points to files /etc/default/grub and files in /etc/grub.d.  The former is also a script, but I could not figure out how to use it to pear-down my grub menus.  The latter directory has a bunch of unfriendly-looking files like "00_header" and "30_os-prober".  I looked at these, and they are also scripts.

First, I'd like the geniuses behind this crap to come down from their high mountain and make something that can be configured by someone WITHOUT a Ph.D. in computer science.

Second, I'd like one of these geniuses to tell me how I can pear down my grub2 boot screen to just Ubuntu and Windows, and give these two options friendlier descriptions.

Thank you.

---

### Post by skatinjj on 2009-11-04
I believe [this]("https://wiki.ubuntu.com/Grub2") should help you.

---

### Post by coffeecat on 2009-11-04
Another link:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

And another useful one:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by phillw on 2009-11-04
> **Cyclone42 said:**
> Sorry, I have to vent about this.  I simply cannot belive that people can replace grub with something so overtly user-hostile as grub2.  All I want to do is simplify the grub boot-screen so there are only two options -- Ubuntu and windows, with simplified descriptions of each.  Right now, the boot screen has about 563 different options for just Ubuntu alone, with intimidating-looking variations on each.  The people who wrote this monster piece-of-XXX should look into the MythTV mailing lists and read about something there called the "Wife Acceptance Factor".  How is she supposed to understand that stuff when booting my computer from Ubuntu to Windows?

Anyway, I was trying to figure out how to configure this thing.  First I noticed that /boot/grub/menu.lst is obviously no longer used.  I discovered grub.cfg in the same directory, but it is freaking SCRIPT, not a configuration file, and says "DO NOT EDIT" at the top.  The script points to files /etc/default/grub and files in /etc/grub.d.  The former is also a script, but I could not figure out how to use it to pear-down my grub menus.  The latter directory has a bunch of unfriendly-looking files like "00_header" and "30_os-prober".  I looked at these, and they are also scripts.

First, I'd like the geniuses behind this crap to come down from their high mountain and make something that can be configured by someone WITHOUT a Ph.D. in computer science.

Second, I'd like one of these geniuses to tell me how I can pear down my grub2 boot screen to just Ubuntu and Windows, and give these two options friendlier descriptions.

Thank you.

This thread should help you out, both with the why's where-fores & reasons that things had to change...   [http://ubuntuforums.org/showthread.php?t=528276](http://ubuntuforums.org/showthread.php?t=528276)

I'm still on 'old Grub', it's going to be a large 'GULP' moment for me when I tell the new grub to take over from my existing one. But, progress is progress... I remeber back when 'X' first appeared for UNIX (Yeah, the real propriatory one) .. Things evolve - In the Linux community we should welcome that, else we'd not have things like cell phones, chat areas, e-mail etc.  Launching Grub2 onto the Ubuntu users would not have been a decision made quickly. Grub2 is required for the furtherment of the system.

People on here had uproar when Shiretoko was launched ... I love it, people complained when Open Office went to v3 .... I love it, just works for me.

As to sorting your menu out ? ... hit the thread and ask... I'll be along there in the near future, asking questions !!!:D

Phill.

---

### Post by Giblet5 on 2009-11-04
:lolflag:

Huzzah!

I've got my pitchfork and torches! C'mon!

---

### Post by Cyclone42 on 2009-11-04
I appreciate the replies, but no-go.  

The conclusion that I have reached is that the developers of grub2 have given NO thought AT ALL to configurability.  You can add boot-menu options or remove them, but you CANNOT change them.  There is simply no way to do it, period.  Correct me if I am wrong, but I know that I am not.

Grub2 basically locks the user out of his or her computer.  It is a power-grab on the part of the developers.  Everything is totally automagic.  The user is unable to customize anything beyond global settings like colors or screen resolutions.  The details are locked out.

---

### Post by sliketymo on 2009-11-05
" sudo apt-get startup manager"

---

### Post by BenAshton24 on 2009-11-05
This might help you... [http://grub.enbug.org/grub.cfg](http://grub.enbug.org/grub.cfg)

I personally think the scripting idea is a good move although I haven't had the need to configure grub in ages since I never even see my computer booting. I just turn it on and go and make a cup of tea :)

If you're angry at the configuration of grub, then I'd love to see what you make of the notify-osd configuration; you have to edit the source just to change a font!

Hope this helps you,
Ben.

EDIT: Also, how about using the grub-mkconfig utility with os-prober installed...
EDIT2: Example menu entrys: [http://svn.savannah.gnu.org/viewvc/trunk/grub2/docs/grub.cfg?root=grub&view=markup](http://svn.savannah.gnu.org/viewvc/trunk/grub2/docs/grub.cfg?root=grub&view=markup)

---

### Post by coffeecat on 2009-11-05
> **Cyclone42 said:**
> You can add boot-menu options or remove them, but you CANNOT change them.  There is simply no way to do it, period.  Correct me if I am wrong, but I know that I am not.

Errr... Correct me if I'm wrong, but I think you've answered your own question. If I wanted to change an entry, I would remove it first by making the appropriate /etc/init.d script non-executable. Then I'd add the modified grub menu entry to /etc/init.d/40_custom and run update-grub. Job done. Actually it's all there in the second link I gave. Look for "**[COLOR=Black]Building a Totally Customized Menu[/COLOR]"**.

I'm not defending grub2 here. I share **some** of your sentiments. Grub2 has all the hallmarks of a project run by geeks for geeks. After all, it's only a bootloader but it has the complexity of an operating system. And I don't criticise the Ubuntu devs for biting the bullet and adopting grub2. The decision was imminent. Apart from a few patches, legacy grub is not being developed and is neglected. It is suffering from bit rot and will have to be abandoned sooner or later - probably sooner.

---

