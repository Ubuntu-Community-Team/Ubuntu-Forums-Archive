---
title: "Installing Windows"
date: 2010-09-04
forum: General Help
---

### Post by banquo on 2010-09-04
Hello every1!


I really love ubuntu, and is definitively not chaning back to Windoooows, however I have problems getting the most out of my hardware (yes Im talkning about gaming) and think that it would b a good idea to install windows xp or 7 to play Starcraft 2 on.

My questions are : 
[B]1) Whats the easiest way to install Windows? (if I wanna dual-boot w ubuntu?
 [/B]*i.e. should i make a partition and install windows on that one or should i backup my stuff, format my hdd, install windows then reinstall ubuntu?*
[B]2) The only reason that i want windows is spelled Starcraft 2. Should i get xp or 7?
     

[/B]thx in advance! // Oskar

---

### Post by scorp123 on 2010-09-04
Starcraft 2 supposedly works under WINE? Try googling "ubuntu starcraft 2 WINE" ...

And you should **_always_** **install Windows first**. Windows doesn't play well with other OS. If you install Linux first and then Windows, then Windows will delete the boot block so you can't easily boot into Linux anymore. There are numerous threads about this in this forum, the search function will help you find those threads.

---

### Post by ajgreeny on 2010-09-04
Though nothing that scorp123 says is wrong, I do not agree that you should "**_always_ install windows first"** as he puts it.

Whilst it is easier to do things that way, there is very little point in wiping a good install of ubuntu just to avoid having to restore grub after a windows install.  If you are running ubuntu 10.04 or 9.10, grub2 finds windows for you, and should add that OS to the menu automatically when you run "sudo update-grub".

Restoring grub is a quick job with the live CD
Ubuntu 9.10 uses Grub 2, so you need to find out what your drives are using live CD:
    ```
sudo fdisk -l
```
From that you need to find the device name of your Ubuntu drive, something like “/dev/sda1&#8243;.
Still in the terminal, type:
```
sudo mkdir /media/sda1
sudo mount /dev/sda1 /media/sda1
```
To reinstall grub:
```
sudo grub-install --root-directory=/media/sda1 /dev/sda
```
Push enter and you’re done! Of course you need to replace “/dev/sda1&#8243; and “/dev/sda” with what you found in the fdisk output.

---

### Post by JedMeister on 2010-09-04
I'm not sure about which OS is best for StarCraft 2 - although I'd check out Wine first if that's the only reason to install Win. WinXP supports DX9, Win7 has DX11 but is hardware dependent (AFAIK will downgrade to suit hardware - but could be wrong). I'm not sure what StarCraft uses. If your hardware supports DX10/11 and the game does too then it would depend somewhat on system specs, Win7 is much better than Vista but is still heavier on lower spec equipment than XP in my experience. I'd go Win7 if your hardware has plenty of headroom (and you'll be able to use DX10/11) otherwise XP.

As for installing Win second, I'm with ajgreeny. When starting with a blank system, its generally easier to install Win then Ubuntu but unless you want to reinstall Ubuntu, in your instance it'll be much easier to just fix GRUB after.

---

### Post by banquo on 2010-09-04
ok.. thanks guys, first of all for all the help, and also to hear some opinions, pro/cons =)
Ive hade some problems with wine lately, its really slow.
Maybe e should reinstall wine (how?) completely and give that a shot first.

---

### Post by ajgreeny on 2010-09-04
To get rid of wine completely it's probably easiest to open synaptic, and use the "Completely remove" option.  Then before you reinstall it, delete the hidden ~/.wine folder from your home.  This will give you a completely new start, with new configuration, and hopefully the new wine will run better and faster.

I have to admit that in the days when I tried wine, I found it slower than a native XP run of the parts of Lotus Smartsuite that I used, but not so slow as to be a problem.  It was also the startup of the applications rather than the running that was slow.

---

### Post by scorp123 on 2010-09-04
> **ajgreeny said:**
>  I do not agree that you should "**_always_ install windows first"** as he puts it. It helps avoid trouble :D

But of course ... if you know your way around, then you can pretty much install anything in any order. Just be aware that some OS (especially Windows and Solaris) don't play nice with others. 

Peace! ):P

---

### Post by banquo on 2010-09-04
Ok thanks you guys.
Im gonna try with wine (which actually works now) first, and plan B is my Gf laptop (ubuntu but better hardware) and as a last resort... only windows remains -.-

---

