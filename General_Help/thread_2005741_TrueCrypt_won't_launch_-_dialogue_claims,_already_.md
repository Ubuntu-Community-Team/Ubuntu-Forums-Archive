---
title: "TrueCrypt won't launch - dialogue claims, already running."
date: 2012-06-18
forum: General Help
---

### Post by scruffyeagle on 2012-06-18
I'm running Unbuntu v10.04 32-bit on a Toshiba Satellite A205 laptop. I downloaded a copy of TrueCrypt v7.1a from the TrueCrypt website, & installed it. I used it for quite a while w/o any problems at all. Recently, it's developed a glitch in the start-up. When I click on the launcher in the menu, the result is a dialogue box popping up in screen center with the message "TrueCrypt is already running.". This is despite there being no TrueCrypt icon on the panel, and no TrueCrypt process running in the list. I could boot the computer, start a Gnome session, immediately try to use TrueCrypt - and, the result is the same.

I've tried uninstalling TrueCrypt using
```
sudo truecrypt-uninstall.sh

```.
There was no problem uninstalling.
I rebooted, & reinstalled TrueCrypt v7.1a. When I tried to use it, the same disfunction happened as during the previous installation of the program - the "TrueCrypt is already running" error dialogue box.

I've run out of things to try, to resolve this problem, so I came here to inquire. Does anybody have any ideas how to fix this? Thanks in advance.

---

### Post by na5h on 2012-06-18
Just delete the file named .truecrypt_lock (or similar...I don't remember the exact name) in your Home folder. It's a hidden file so you need to press CTRL+H in order to see it.

---

### Post by scruffyeagle on 2012-06-20
> **na5h said:**
> Just delete the file named .truecrypt_lock (or similar...I don't remember the exact name) in your Home folder. It's a hidden file so you need to press CTRL+H in order to see it.

THANKS!!!

It worked perfectly. For anyone seeking to make use of this info: The file turned out to be .truecrypt_lock-*profilename*. (When searching, replace *profilename* w/ whatever Linux session user name is in use for the Gnome session; i.e., same as the home directory.)

---

