---
title: "Virtualbox and USB"
date: 2010-02-22
forum: General Help
---

### Post by Baneblade on 2010-02-22
I have been struggling to get USB support in Virtualbox for quite a few hours now and I have finally cracked it.

So here was the problem. I made sure that I had the latest download from the Virtualbox website (the free "OSE" version in the repo's doesn't include USB support). I had set my filters correctly and double checked them. However, when starting my virtual machines all the USB devices were greyed out!

So... to cut a long story of trial and error with permissions and device mounting short, here is what you need to do:

Go to System => Administration => Users and Groups

Unlock this and authenticate with your password.
Click "Manage Groups" and then choose the properties for "Vboxusers"
Check the box(es) for the account(s) that you wish to use Virtualbox with.

Logout and in again with one of the accounts that you just authorised and you are done!

---

### Post by trvr on 2010-02-22
You are a good man for posting this. So many times I come across unresolved forum threads; so to come across one that is simply an answer is a relief.

Thank you!

---

### Post by altjx on 2010-03-01
I'm not sure what happened to my vboxusers group. It was visible, after adding myself to it and relogging, I went back to check and the group is gone. Anyone know what could be the cause of this issue?

---

### Post by gabo.cr on 2010-03-01
USB in VirtualBox never worked for me, I stopped trying a long time ago.
[-(

---

### Post by Baneblade on 2010-03-02
> **gabo.cr said:**
> USB in VirtualBox never worked for me, I stopped trying a long time ago.
[-(

Does it work now that you followed my little how-to? If not, are the "symptoms" the same as I described?

---

### Post by altjx on 2010-03-02
After installing VirtualBox 3.1 from virtualbox.org, adding myself to the LP and vboxusers group, and succesfully rebooting, I'm now able to use my USB devices in it =)

---

### Post by giddyup306 on 2010-03-02
I fought my USB issue on VM for two straight days before I happened to fix it.  I'm not sure if this is the complete reason why it didn't work but after I watched this video on youtube it worked.

Keep in mind like I said it might be this in conjunction with everything else that I tried...

[http://www.youtube.com/watch?v=Vb3tgejjyBw](http://www.youtube.com/watch?v=Vb3tgejjyBw)

It's worth a try...

---

### Post by terrybbarton on 2010-03-18
Now does anyone know how to keep the USB ports that devices are attached to from swapping if you have multiple identical USB devices being used in a Virtualbox Ubuntu guest OS.  I have two identical USB modems (Huawei E220 attached to ttyUSB0 and ttyUSB1) And they would be completely interchangable except that the phone numbers are not and so I can't have VirtualBox randomly swapping the USB ports that the Ubuntu guest has them attached to while my software is running. I am kind of a noobie. And have searched the Internet, VirtualBox forums as well as posted there and I just can't seem to find the answer.

---

### Post by linden940 on 2010-03-18
hmm someone should make a virtualbox how-2 video/post and have it sticky......

it seems like there is a promble with virtualbox very time you refresh the page on installing it and getting usb to work lol....i know it took me for ever to *first time trying* to get it right...but i made the misstake and did not get the one from there website

anyway if i have time to do this i most likely will but if anyone else have done this..or maybe a older post? i'll say it should be sticky

---

