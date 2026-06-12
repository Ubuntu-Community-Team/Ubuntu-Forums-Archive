---
title: "Nothing boots anymore... (Urgent)"
date: 2011-08-09
forum: General Help
---

### Post by new_b on 2011-08-09
So after installing linux for the first time - version 11.04,  first there are 1000 problems which don't fix especially the fact it didn't boot into linux half the time. I managed to get on it and there was an update, thinking this would fix something I updated it and now I can't do anything on my laptop!

Before I could atleast log onto windows but I can't even do that now. The place where you can press f12 to go into the bios and change priority I can't even get there because when it says to press f12 I press it but nothing happens and it still takes me to a blank screen with no grub menu no nothing.

I really badly need a quick fix on this as soon as possible before I go crazy

---

### Post by Kira_Belka on 2011-08-09
so your ubuntu can load still?

---

### Post by new_b on 2011-08-09
> **Kira_Belka said:**
> so your ubuntu can load still?

Nope, when I say nothing I actually mean it. If I could atleast see the grub menu I could've logged into windows 7 and deleted linux so I can try another version and see if it's compatible but here is what happens....

1) I press power button on laptop
2) Toshiba's logo comes on, under it says press F2 to enter some setup place, F12 to go to bios. I try pressing either of them and nothing happens. Instead I am led to..
3) Blank screen where there's a small white line (not blinking) on top left corner which doesn't accept inputs.

---

### Post by Kira_Belka on 2011-08-09
sorry.. I'm 1000% blondie sometimes) mmmmm.. so are you have ubuntu live CD?

---

### Post by new_b on 2011-08-09
> **Kira_Belka said:**
> sorry.. I'm 1000% blondie sometimes) mmmmm.. so are you have ubuntu live CD?

Haha it's okay. And by live cd do you mean the usb where I installed ubuntu from? If you do then yes I have it

---

### Post by Duncan Williams on 2011-08-09
Try supergrub-2.
Its a small program that you burn onto a CD and then use it to boot your computer into grub.
[http://www.supergrubdisk.org/super-grub2-disk/](http://www.supergrubdisk.org/super-grub2-disk/)

---

### Post by new_b on 2011-08-09
Oh my good. I think I might've just fixed it. took the battery out and put it back in and now i'm in the bios!! Next thing to do is delete this version of linux. Can you help me with that?

---

### Post by cariboo on 2011-08-09
Just remove your Ubuntu partition, you can use the Windows disk management tools to do it. His is assuming you did an installation on a partition, and not with wubi. If you installed Ubuntu using wubi, just go to add remove programs to remove your Ubuntu installation.

---

### Post by new_b on 2011-08-09
Okay I'm on disk management. I have a few disks here, none of them have any kind of names, apart from the main one which says NTFS. I don't want to delete something which will mess my system up. e.g. a lot of them are called "primary partition" and "healthy, active" etc.

---

### Post by new_b on 2011-08-09
Don't worry about it. Found a good tutorial on youtube and fixed everything now. Thanks for all the responses

Here's the tutorial for other people who may have had similar problems: [http://www.youtube.com/watch?v=JwGsghbumxE](http://www.youtube.com/watch?v=JwGsghbumxE)

---

