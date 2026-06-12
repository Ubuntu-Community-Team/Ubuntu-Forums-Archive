---
title: "splash screen problems"
date: 2010-11-23
forum: General Help
---

### Post by suf3r on 2010-11-23
Hello,
After xubunutu succesfully instalation and nvidia drivers install some strange things happening after every boot up.
Then starting up computer, goes these things:

1. Hardware check (good)
2. Goes blank screen (that's the problem)
3. xubuuntu logo displayed (good)
4. desktop loaded (good)

I have maked video which is about ~1 minute:
[http://rapidshare.com/files/432670317/V1801_23-11-10.3gp](http://rapidshare.com/files/432670317/V1801_23-11-10.3gp)

Question: It's possible replace blank screen display with logo show (instead of blank screen display logo)?

Computer spec: Attached file ...
By the way i'm using mine compiled kernel but i'm sure 99% that's not the problem. Thats happened and with 2.6.35-22/23-generic kernel's.

(I think it's GRUB2 or plymouth problem)

How to fix described below...

---

### Post by cariboo on 2010-11-23
Much depends on your video hardware, I didn't see anywhere in the file you attached what make/model graphics card you are using, except that is agp.

---

### Post by suf3r on 2010-11-23
> **cariboo907 said:**
> Much depends on your video hardware, I didn't see anywhere in the file you attached what make/model graphics card you are using, except that is agp.

NVIDIA GeForce FX 5500

EDIT:

This fixed my problem:
[http://ubuntuforums.org/showpost.php?p=9175901&postcount=4](http://ubuntuforums.org/showpost.php?p=9175901&postcount=4)

---

