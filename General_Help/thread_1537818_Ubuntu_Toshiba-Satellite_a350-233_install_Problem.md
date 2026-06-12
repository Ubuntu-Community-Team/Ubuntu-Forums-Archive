---
title: "Ubuntu Toshiba-Satellite a350-233 install Problem"
date: 2010-07-24
forum: General Help
---

### Post by Cagatay on 2010-07-24
Hi All i am from Turkey i have some problem with my notebook.
 
i wanna use ubuntu on my notebook but i can't intall that.
 
because my notebook warning to me.
 
No Value For netbook... <- Waiting 3 - 4 mins and after
 
BUG: soft lockup – CPU#0 stuck for 61s!
BUG: soft lockup – CPU#1 stuck for 61s! 
How can i solve this problem ? 
 
and 
 
i tried whatever saw in all forum but i can not solve :sad:
 
if you wanna screen , i can take.
 
Pls Help to me =(.
 
Note:
Sorry for my english can be a bad =)

---

### Post by Rubi1200 on 2010-07-24
Hi and welcome,
these error messages seems to be related to a kernel issue.

Two ideas for you to try:

1. When you try booting from the CD; do this:

Put the LiveCD in and boot up;

when you see the Ubuntu logo hit Enter;

Choose language and leave the default Try as a live cd or whatever it says again;

Important: hit F6 and then Esc to see the boot line

**file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --**

Now, again this is important, move the cursor backwards and remove quiet splash;

Add the following parameters in this order:

xforcevesa nosplash

In other words, the boot should look like this:

**file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz xforcevesa nosplash --**

Now hit Enter and hopefully you will be at the desktop admiring Lucid Lynx 10.04

2. Try an older version of Ubuntu; the previous version is 9.10
Here is the link:
[http://releases.ubuntu.com/karmic/](http://releases.ubuntu.com/karmic/)

Good luck!

---

