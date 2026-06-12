---
title: "StickAm not working right!"
date: 2009-07-24
forum: General Help
---

### Post by Steelclan on 2009-07-24
When I go on StickAm I can see the chat and what not I just can't click the enter chat button.

Please help me fix it!

---

### Post by basementgeek on 2009-08-16
Did you ever get this figured out?  I have the same problem.  I've tried it in Opera and Firefox.  Is this a flash issue?

---

### Post by MrLeN on 2009-08-16
> **Steelclan said:**
> When I go on StickAm I can see the chat and what not I just can't click the enter chat button.

Please help me fix it!

I am also having problems.

I have not been able to use stickam for months. I have to log off and log back in with vista. I have spend DAYS searching for answers and searched all over these forums and all over the Internet.

It's not just stickam. There are hundreds and hundreds of complaints that Ubuntu wont work with ANY flash based chat site or application with a web cam.

I have a Logitech webcam, and it works fine in cheese. It just wont work with any flash based application.

I have gone through copious amounts of grief to try to STAY using Ubuntu and not vista, and after switching back and forth many times over the last years, and installing wine and sun virtual box and spending days weeks and months trying to find the best suitable replacement programs, I am finally able to bare with Ubuntu.

It's not Ubuntu I have a problem with - it's just the much smaller 3rd party software variety, but I am sure that will continue to grow.

However, not being able to use any flash based sites (with my web cam) is one of the last few things I have to reboot back into Vista for.

I can see that this problem has been around for years, and I can't find a solution. I have tried everything.

I don't think there will be a proper solution here today.

Maybe in future..

*sniff sniff* :(

---

### Post by High Roller on 2009-08-17
To answer the OP's question:

The missing elements problem is related to windowless mode and is a bug in flash.  To _workaround_ this problem do as follows.

Go to terminal...

```
sudo mkdir /etc/adobe
sudo gedit /etc/adobe/mms.cfg
```

Add the line
```
WindowlessDisable = 1
```
Then save the file.

So far this has fixed the stickam chat problems for me.  The only thing I've noticed is drop-down menus might sometimes fall behind the content in some instances.
I haven't taken the time to file a bug at Adobe...  If anyone wants to beat me to the punch feel free! :)

---

