---
title: "Laptops mousepad not working after login"
date: 2010-08-19
forum: General Help
---

### Post by tanveer on 2010-08-19
Hello,

I have been using ubuntu 10.04 for a couple of months. But recently facing a mouse related problem. 
In my laptop HP Pavillion DV7 last week I added the mouse for some work and after finishing it I removed it. But after that my laptops sensor stopped working whenever I login. wht I mean is now at the login prompt the laptops mousepad works fine but after I press login the pointer gets freeze and doesn't work at all. Then I created another user and with that user its working perfectly. 

Why this weird problem is happening .. is it because I connected the mouse in my laptop or some thing else.
Thanks in advance.

---

### Post by yoobin.jeong on 2010-08-19
I'm having the exact same problem.
I'm running 10.04 on hp pavilion dv5.

---

### Post by GlideKensington on 2010-08-25
I have the same problem with the mouse not working after logging in. The mouse works perfectly fine before I login in. I'm running on a HP pavilion dv7 and I'm also running ubuntu 10.

Please help someone. Thanks.

---

### Post by GlideKensington on 2010-08-25
For those who is having a similar problem, I followed the steps described in this comment and it fixed it right away: [https://bugs.launchpad.net/ubuntu/+bug/549727/comments/103](https://bugs.launchpad.net/ubuntu/+bug/549727/comments/103)

Basically, like the comment said, running the following command fixed it:

```
gconftool --type bool --set /desktop/gnome/peripherals/touchpad/touchpad_enabled true

```

---

