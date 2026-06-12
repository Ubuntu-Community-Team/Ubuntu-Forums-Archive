---
title: "Monitor Input signal out of range!"
date: 2010-11-28
forum: General Help
---

### Post by coolcam on 2010-11-28
Hi,

I basiclly destroyed my laptop a couple of years ago. Windows XP wouldn't even start but it didn't come with an installation disk. I tried recovering it but it just died. So a few months ago I put a box of thing on top of it which broke the screen! I was going to chuck it out until I stumbled upon a page which told you you could use it as a web server.

I decided to use it to host my website. I installed ubuntu without a problem however it wasn't until I was about to start it up I found out it was against BT's terms and conditions!! So since I installed ubuntu I thought I might as well make use of it and use it to render my files. When I went to turn it on for the second time and plugged it into the monitor it said input signal out of range!

I can see the login screen but I can't move the mouse or anything. I can't access the terminal, how can fix this?!

Thanks,
Cameron

---

### Post by coolcam on 2010-11-28
Anyone?!

---

### Post by coolcam on 2010-11-28
Please!!!

---

### Post by coolcam on 2010-11-28
*bump* ........

---

### Post by coolcam on 2010-11-28
!!!!???????????????????????????????????!!!!!!!!!!!!!!!!!!!!

---

### Post by coolcam on 2010-11-29
Re: *BUMP* !!!

---

### Post by coolcam on 2010-11-29
??? If I'm not giving enough infomation please tell me!!

---

### Post by coolcam on 2010-11-30
No progress...........................

---

### Post by rahilm on 2010-11-30
what happens if you press ctrl+alt+f1 ?

---

### Post by coolcam on 2010-11-30
No, I tried that after looking at another looking at another forum...

---

### Post by coolcam on 2010-11-30
...

---

### Post by rahilm on 2010-11-30
does booting into a Live-CD work?

---

### Post by coolcam on 2010-11-30
My CD burner is broken but using a live usb works.

---

### Post by coolcam on 2010-11-30
??????????

---

### Post by celsdogg on 2010-11-30
just to clarify, you cant even get a tty?

I have gotten out or range messages when x is starting up before. if even a cli wont come up at all, have you tried remoting to the machine via ssh or similar?

regards.

---

### Post by coolcam on 2010-11-30
shh??? !!! What's that... I don't think I can access tty nothing happens when I press ctrl + alt and f1

---

### Post by celsdogg on 2010-11-30
im confused. you say your monitor says out or range, yet you can see the login screen? usually its one or the other.

ssh gives you the ability to login remotely from another machine via command line. you can research it on wiki. basically you need it connected to the network and need to know the hostname or ip address of it, which you might not know either.

if i recall correctly, there isnt a lot in the way of remote connectivity installed by default in a standard ubuntu desktop installation. you need some way of getting to a command line so that you can edit conf files and run x configuration in order to change X itself.

upon booting, can you see or bring up Grub?

---

### Post by coolcam on 2010-11-30
Sorry, I should of explained better, I can see the login screen but it is frozen, however on other monitors I can't see it at all.

EDIT: I can bring up grub

---

### Post by celsdogg on 2010-11-30
> **coolcam said:**
> Sorry, I should of explained better, I can see the login screen but it is frozen, however on other monitors I can't see it at all.

EDIT: I can bring up grub

from grub, have you tried using recovery mode?

---

### Post by wojox on 2010-11-30
Why don't you install Ubuntu Server and not The Desktop Edition?

---

### Post by coolcam on 2010-11-30
I tried using recovery mode but for some reason that won't start up... I asume that's nothing to do with the input signal so I may have to work to get that solved. And what is the user interface like for the ubuntu server edition as I hadn't given it very much though because I have ever only really used windows computers?

---

### Post by coolcam on 2010-12-01
...

?????!!!!!!

...

---

### Post by coolcam on 2010-12-01
???

---

### Post by coolcam on 2010-12-01
Sorry, but the only time I've had any success was a few mintes after a bump! I'll stop bumping so often though.

---

### Post by coolcam on 2010-12-01
I tried using recovery mode but for some reason that won't start up... I  asume that's nothing to do with the input signal so I may have to work  to get that solved. And what is the user interface like for the ubuntu  server edition as I hadn't given it very much though because I have ever  only really used windows computers?

---

### Post by rahilm on 2010-12-02
if the ubuntu via live-usb works.. then there is some problem with ubuntu installation...

---

### Post by coolcam on 2010-12-02
Ok It's 8 in the morning for me so I will try reinstalling it after school!

---

### Post by wojox on 2010-12-02
> **coolcam said:**
> And what is the user interface like for the ubuntu server edition as I hadn't given it very much though because I have ever only really used windows computers?

It's all command line. ;)

---

### Post by coolcam on 2010-12-02
> **wojox said:**
> It's all command line. ;)

Oh... I won't be using that then!

---

### Post by coolcam on 2010-12-02
...or was that wink meaning you were being sarcastic?!

---

### Post by coolcam on 2010-12-02
I did a reinstall and it now works! It must have been something to do with the updates I did.

---

### Post by coolcam on 2010-12-02
Hmm... It seems I was talking to myself 74.1% of the time on this forum... Well actually it's exactly 75% including this post!

---

