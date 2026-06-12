---
title: "Issue with administrator password"
date: 2012-05-02
forum: General Help
---

### Post by Sknow on 2012-05-02
I think I broke Ubuntu :(  I only have one account (the default admin account) and I set my password to off. The problem seems to be that I also installed Burg and have my boot screen set to only Windows 7 or Ubuntu 12.04. I unticked the recovery mode option and I've tried restarting numerous times holding down left shift. I can't seem to get into recovery mode. Help :(

---

### Post by jerome1232 on 2012-05-02
repeatedly press shift, don't hold it down. I don't know why everybody says to to hold it down, that has never worked on any machine for me. Once you do get the menu,

To get into recovery mode try editing the Ubuntu line, and adding "single" to the end.

```
#### so if it looked like this before editing
kernel /vmlinuz-2.6.15-27-386 root=/dev/mapper/Ubuntu-root ro quiet splash
#### it would look like this after editing
kernel /vmlinuz-2.6.15-27-386 root=/dev/mapper/Ubuntu-root ro single
```

Hopefully that helps.

---

### Post by Sknow on 2012-05-02
> **jerome1232 said:**
> repeatedly press shift, don't hold it down. I don't know why everybody says to to hold it down, that has never worked on any machine for me. Once you do get the menu,

To get into recovery mode try editing the Ubuntu line, and adding "single" to the end.

```
#### so if it looked like this before editing
kernel /vmlinuz-2.6.15-27-386 root=/dev/mapper/Ubuntu-root ro quiet splash
#### it would look like this after editing
kernel /vmlinuz-2.6.15-27-386 root=/dev/mapper/Ubuntu-root ro single
```Hopefully that helps.

No dice. Here's what I get: the Samsung screen loads really quick then it says GRUB loading for about a millisecond, then Burg immediately pops up with the Windows logo and the Ubuntu logo. Once I select the Ubuntu logo it goes dark for a few seconds and the purple loading screen comes up with the Ubuntu logo and I'm logged in. I've hit left shift the whole time and does nothing. I'm thinking I'm gonna have to delete the whole partition :(

EDIT - Note: I can't even get to the part with the code you put up

---

### Post by jerome1232 on 2012-05-02
So you do get a menu to select which os, then shift is not needed, there should be a key combo you can hit to edit the boot line (in regular grub it is "e" )

---

### Post by Sknow on 2012-05-02
Yeah! If I hit e it comes to a screen that just says GRUB>_ and that's it. I don't know what to put there though. I would assume that's where your code comes in but I don't know what mine is, is there somewhere I could find that without having to have the admin password? :P

---

### Post by Sknow on 2012-05-02
Fixed it! It was exactly as you had said, I just didn't see it because it scrolled off the screen. Got into recovery mode and reset the password, all is well. Thanks a million jerome1232!

---

