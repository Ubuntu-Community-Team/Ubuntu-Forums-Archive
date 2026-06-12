---
title: "Make Dual Boot Pretty."
date: 2010-04-19
forum: General Help
---

### Post by gunnarlinux on 2010-04-19
Hey all,
I have Ubuntu 9.10 running inside Windows XP Home Edition SP3 with Wubi. Is there a way I can make the screen where I select what Operating System to boot into look nicer? I was thinking of something like the Windows 7 Background with 2 pictures, one of the Windows logo (would boot Windows), one of the ubuntu logo (would boot ubuntu)
Thanks,
-Gunnar

---

### Post by Felix-the-Cat on 2010-04-20
You should look at "Startup-Manager" under add-remove programs. If you just search for "boot" its the 2nd, 3rd, or 4th result. That will give you a painless way to do it but if you are willing to mess with grub configuration files you may be able to do even more - but only if you are adventurous.

---

### Post by gunnarlinux on 2010-04-23
So theres no easier script to do that for me? Anyone? Bumb??
I saw something like this at a hotel I stayed at once a while back on their lobby pc...

---

### Post by oldfred on 2010-04-23
That was another boot loader, which I have seen but do not remember the name. 
If you have wubi you are actually using the windows boot loader to choose between windows and Ubuntu at startup then it goes to the grub menu.
My goal is to have the boot menu go as quick as possible and the graphics just slow it down.

---

### Post by Bölvaður on 2010-04-23
> **gunnarlinux said:**
> So theres no easier script to do that for me? Anyone? Bumb??
I saw something like this at a hotel I stayed at once a while back on their lobby pc...

yes it is possible with GRUB.
But because you are using WUBI (as stated before) the windows boot loader is actually in control.. and it's extremely ugly and I doubt it is easy to config it.

Btw welcome to the forums if no one has said it yet and cool (RL) name.

---

### Post by gunnarlinux on 2010-04-26
> **Bölvaður said:**
> yes it is possible with GRUB.
But because you are using WUBI (as stated before) the windows boot loader is actually in control.. and it's extremely ugly and I doubt it is easy to config it.

Btw welcome to the forums if no one has said it yet and cool (RL) name.

Thanks, you actually were the first person to say that (thought people here were supposed to be nice jk:) ) Could you help me with configuring GRUB? I don't really understand it. I was hoping on using it on my main computer for guests, but it would be nice to configure it for my laptop...

---

### Post by gunnarlinux on 2010-04-26
> **Bölvaður said:**
> yes it is possible with GRUB.
But because you are using WUBI (as stated before) the windows boot loader is actually in control.. and it's extremely ugly and I doubt it is easy to config it.

Btw welcome to the forums if no one has said it yet and cool (RL) name.
 
And sorry for the noob question but whats RL?

---

### Post by Bölvaður on 2010-05-02
> **gunnarlinux said:**
> And sorry for the noob question but whats RL?
Real Life



and about the background for grub2 (the one in the latest ubuntu releases)

[http://linux.aldeby.org/configure-grub2-options-and-background.html](http://linux.aldeby.org/configure-grub2-options-and-background.html)

---

### Post by dino99 on 2010-05-02
i'm always surprised with those users installing linux inside a woindoz file :lolflag:

better to make a real install or install it with virtualbox

---

### Post by gunnarlinux on 2010-05-02
> **Bölvaður said:**
> Real Life



and about the background for grub2 (the one in the latest ubuntu releases)

[http://linux.aldeby.org/configure-grub2-options-and-background.html](http://linux.aldeby.org/configure-grub2-options-and-background.html)

Thanks so much! It really looks nice now.

---

### Post by gunnarlinux on 2010-05-02
> **dino99 said:**
> i'm always surprised with those users installing linux inside a woindoz file :lolflag:

better to make a real install or install it with virtualbox

I've been putting off partitioning the hard drive and installing nix on it for a while. Might do it today actually.

---

