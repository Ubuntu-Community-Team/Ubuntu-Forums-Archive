---
title: "Internet"
date: 2006-04-04
forum: General Help
---

### Post by stocker on 2006-04-04
Hello, I want to put my Edubuntu box on the internet but I do not know how to do it.  Could anyone please give me advice.  I got info if you need it.

Tiscali Broadband
It goes through my telephone socket, so it must be ADSL (well it has a adsl light on the modem box.)
Modem: Sagem F@st 800-840 (USB)

What would I need to do

Thanks

Matt

---

### Post by taurus on 2006-04-04
Download the LiveCD and boot from it.  See if it finds everything on your machine, especially the USB modem because that could be the trouble spot for you...  If everything is fine, then download the actual iso image and install it on your machine, after burning it to a CD first.  :)

---

### Post by stocker on 2006-04-04
Well I have already got it installed on my PC in my bedroom, and was wondering how I would do it.

---

### Post by taurus on 2006-04-04
How would you do what?  Does it allow you to surf the web after you installed it?

---

### Post by stocker on 2006-04-04
I havent tried it, i mean what would I have to do to configure it.  Sorry bout making it look different lol.

---

### Post by taurus on 2006-04-04
Let's do first thing first.  Now that you have Edubuntu on your PC, see if you can surf the web as it.  Fire up firefox by clicking Applications -> Internet -> Firefox and see if you can view any website on the net!  Also, open a terminal by Applications -> Accessories -> Terminal and at the prompt, type
```

/sbin/ifconfig

```
Now, what does the output of that command after you hit the return?

---

