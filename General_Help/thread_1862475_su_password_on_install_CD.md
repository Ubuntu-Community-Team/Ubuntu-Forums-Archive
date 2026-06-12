---
title: "su password on install CD"
date: 2011-10-16
forum: General Help
---

### Post by moonguide on 2011-10-16
What is the password to use with su when running 10.04 from the install CD?

My desktop machine crashed this morning. This afternoon I booted the machine with the install CD in try-it mode. I'm copying files from that machine to my laptop but I keep running into files and/or folders that I'm told I don't have permission to access. When I look at them with ls -l in a terminal window I see that they have rwxr-x--- permissions. I tried:

su chmod 755 foldername

but got an authentication failure when I used my normal password. Thinking about it I realize I'm not really running "my" machine and the user name, ubuntu, supports that conclusion.

How do I grant myself permission to read those files so I can copy them?

If it helps diagnose the problem these files I can't read are the ones I was working with yesterday before the machine crashed.

Thanks.

---

### Post by kooldino on 2011-10-16
Try just hitting enter?  (no password)

---

### Post by haqking on 2011-10-16
> **moonguide said:**
> What is the password to use with su when running 10.04 from the install CD?

My desktop machine crashed this morning. This afternoon I booted the machine with the install CD in try-it mode. I'm copying files from that machine to my laptop but I keep running into files and/or folders that I'm told I don't have permission to access. When I look at them with ls -l in a terminal window I see that they have rwxr-x--- permissions. I tried:

su chmod 755 foldername

but got an authentication failure when I used my normal password. Thinking about it I realize I'm not really running "my" machine and the user name, ubuntu, supports that conclusion.

How do I grant myself permission to read those files so I can copy them?

If it helps diagnose the problem these files I can't read are the ones I was working with yesterday before the machine crashed.

Thanks.

use sudo, su which if no other name is designated defaults to root which is disabled by default in ubuntu.

see [ROOTSUDO]("https://help.ubuntu.com/community/RootSudo")

the sudo password is always YOUR own password as long as you are in sudo group

---

### Post by moonguide on 2011-10-17
Right idea but wrong secret handshake. As mentioned I should have been using sudo instead of su. Once I did that I was able to change ownership of the files and copy them to my laptop.

Thanks for the replies.

---

### Post by hansdown on 2011-10-17
Hi, moonguide.

Running the live media, open a terminal, and enter...

```
gksudo nautilus

```
You should be able to drag and drop files to a usb, etc.

This will carry the necessary privileges, to read, and write.

---

### Post by haqking on 2011-10-17
> **moonguide said:**
> Right idea but wrong secret handshake. As mentioned I should have been using sudo instead of su. Once I did that I was able to change ownership of the files and copy them to my laptop.

Thanks for the replies.

cool.

Remember to mark your thread as solved using thread tools.

Cheers

---

