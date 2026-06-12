---
title: "Could someone PRETTY PLEASE tell me how to add kernel parameters in GRUB2?"
date: 2009-11-13
forum: General Help
---

### Post by ortaa23 on 2009-11-13
Right,

Installed Ubuntu 9.10 5 days ago, my first Linux after wiping WinXP. And still can't get the internet to work. Apparently to get it to work with my Ethernet Controller, I need to add the kernel parameter irqfixup (detailed in [another post]("http://ubuntuforums.org/showthread.php?t=1319174")). However I have absolutely no idea how to do this, as the documentation I can find is all for GRUB.

I also posted on the same topic in the absolute beginners forum, so far no reply, so maybe nobody that posts there has a clue either? Person whose computer I am using for internet is getting a bit pissed off with me.

My gratitude would lack words to express it...

---

### Post by delcypher on 2009-11-13
You can manually add parameters at boot up at the grub menu. If you menu does not appear at boot up then you need to hold down the shift key.

You then highlight the entry you want to boot, press edit (that's the 'e' key on my machine I think). Then you can add the the kernel parameter. On mine I would add it here.

```
linux /boot/vmlinuz-2.6.31-14-generic root=UUID=XXXXXXXXXXXXXX ro quiet splash irqfixup
```

Then press CTRL+x to boot.

If your ethernet controller now works you can permanently add that kernel parameter by editing /etc/default/grub and then running sudo update-grub afterwards.

---

### Post by ranch hand on 2009-11-13
OK.  See link in my sig.  There are a lot of links in it to in depth resources.


The first thing you want to do is select your OS in the menu and hit "e".  This will allow you to edit the entry with out making any perminent changes.  You will see the line with all the other instructions on it.  It is the line starting with "linux".

If this works then you will need to make a custom menu file.  This is covered in my post and the first 2 links in my post.

More problems - just fire away.

---

### Post by ortaa23 on 2009-11-13
Wowee the beginners forum wasn't really the place to post was it?

Many thanks for your replies. Unfortunately, neither irqfixup or noapic, which was the other suggested parameter to try in this forum in the bug reports I searched, worked.

So I will start another thread in this forum on the subject.

---

