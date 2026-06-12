---
title: "Unable to boot"
date: 2010-01-27
forum: General Help
---

### Post by Ferto on 2010-01-27
I don't know much about Ubuntu  and BASH but I'll try to explain the problem.

Since yesterday, I have been unable to boot. I use both Ubuntu 9.10 and Windows Vista on one laptop. (I only use Vista when there's a problem with Ubuntu.) I installed Ubuntu with Wubi and I have been using it for over a year now.
So everytime I start the computer and choose Ubuntu, it doesn't boot Ubuntu but instead, it shows a black command screen with white letters. These letters give me a lot of numbers etc. and then it says something like "Minimal BASH command is possible." Then it says "grub>" So I tried to type in some things. I tried "boot" and it reacted with: "In order to boot, you must first load the kernel." So I tried: "load kernel" but it just said: Command not found. I tried pushing ESC. It brought me to a menu where I could choose about 9 options. One was "boot halt". When I selected this, it showed "booting halt..." for minutes and minutes doing absolutely nothing at all. It had commandline, which brought me back where I was, and a large number of commands that started with find and ended with /menu.lst. (find /ubuntu/drivers/grub/menu.lst, find /ubuntu/install/grub/menu.lst etc. etc) When I tried this, it said: Error: file not found.
I think this problem started one time when I was out of battery power while booting normally.

---

### Post by maybeway36 on 2010-01-27
Looks like the GRUB bootloader can't find its config file. Because of Wubi I'm not sure where that file would be placed.

---

### Post by Silvertones on 2010-01-27
I had this problem after an update. I found a fix but don't remember were to get it. What you need to do is download a new wubildr file & replace the old. It lives in C:/wubildr in windows. I kept a copy and can send if I have an email address or do a look up for it.
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1984509.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1984509.html)

---

### Post by Leppie on 2010-01-27
my advice: remove the wubi install and do a normal side by side install.
ntfs is not a reliable filesystem!

---

