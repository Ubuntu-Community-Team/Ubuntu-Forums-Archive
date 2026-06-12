---
title: "Root File System Problems"
date: 2006-04-18
forum: General Help
---

### Post by SethNieman on 2006-04-18
Last night I turned off my computer and when I turned it on today, it didn't boot up.

It got to the load screen, where is checks to make everything works, but when it got to "Checking Root File System" it went to a diffrent screen where it checked the file system. I them got a couple of errors telling me that I will have to fix it manually and whatnot. Here are some screenshots:

[IMG]http://www.wearebrilliant.com/linux/01.jpg[/IMG]

[IMG]http://www.wearebrilliant.com/linux/02.jpg[/IMG]

[IMG]http://www.wearebrilliant.com/linux/03.jpg[/IMG]

Thank you very much.

---

### Post by cskeide on 2006-04-19
did you follow the instructions on the screen?

- type the mount command in the instructions
- run fsck manually, "fsck /"

---

### Post by SethNieman on 2006-04-19
Yeah, lol, I'm kind of an advanced user (when it comes to working in the GUI) but most of that screen was goobledygook to me. So just to make it clear, I will actually tpye "fsck /" ?

Thanks for your help!

---

### Post by Ramses de Norre on 2006-04-19
```
mount -n -o remount,rw /
fsck /
```
Not sure whether it is in this order (it's reversed on the screen but previous poster said to do it like this, haven't done this myself yet).

---

### Post by SethNieman on 2006-04-19
Ok, thanks I'll try it and tell you what i did

---

