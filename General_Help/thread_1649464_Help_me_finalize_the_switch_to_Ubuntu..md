---
title: "Help me finalize the switch to Ubuntu."
date: 2010-12-20
forum: General Help
---

### Post by Matthew24 on 2010-12-20
Hi all,

I have Ubuntu 10.04 on my [newer] Asus laptop.
This laptop is my primary computer and I am 
dual booting Windows 7 ultimate [64-bit] & 
Ubuntu [64-bit].

I really want to break out my DBAN CD [it's a
program to format the hard drive completely]
and *just* have Ubuntu on my laptop... but there
are two factors restricting me to do this b/c
I need Windows for them [as of now, that is.]

1] I record music on my laptop using this usb
"soundcard" dongle. It's made by M-audio and
Ubuntu doesn't pick it up, and I have no idea
how to enable it for recording. I also like 
the idea of being able to choose between my
laptop speakers and the usb soundcard. Here
is a picture of the device, it's rather simple:

[http://cache.gizmodo.com/assets/resources/2006/08/sessionwithusb.jpg](http://cache.gizmodo.com/assets/resources/2006/08/sessionwithusb.jpg)

2] I can't seem to make my screen any brighter
on my laptop. Windows 7 is very bright, but my
Ubuntu installation is at full brightness and
is still dull. Is there a 3rd party program I
can get to fix this? Or would upgrading to the
10.10 version fix it?


Thank you for any input and please help my 
efforts to free myself from Microsoft once
and for all!

-Matthew

---

### Post by Matthew24 on 2010-12-20
Can anyone help me on either of these concerns?

---

### Post by FacesComix on 2010-12-20
if you still have your installation cd for 7 you could always format the drive and run 7 inside virtual box. I'm running ubuntu 10.10 with virtualbox ose (I think, I'm using whichever one can run USB devices...) running windows XP pro...

that's the easiest way I've found to make a complete switch while still keeping my necessary windows activities available. (i.e. iTunes)

---

### Post by cchhrriiss121212 on 2010-12-20
Firstly, you should wait at least a day before bumping a thread.

Regarding problem 1:
Do you have a product name for the USB dongle? Open up a terminal and paste this:
lsusb && arecord -l
Then post what output you get.

---

### Post by kanishkdudeja on 2010-12-20
could you please tell the model number of ur m audio sound recording card?

---

### Post by cchhrriiss121212 on 2010-12-20
> **FacesComix said:**
> if you still have your installation cd for 7 you could always format the drive and run 7 inside virtual box. 
A bad idea if he wants to record audio, a virtualised OS cannot handle that kind of activity with acceptable performance.

---

### Post by FacesComix on 2010-12-20
> **cchhrriiss121212 said:**
> A bad idea if he wants to record audio, a virtualised OS cannot handle that kind of activity with acceptable performance.

Good point, I hadn't thought about that.

Even with a faster cpu?

---

### Post by Matthew24 on 2010-12-20
> **cchhrriiss121212 said:**
> Firstly, you should wait at least a day before bumping a thread.

Regarding problem 1:
Do you have a product name for the USB dongle? Open up a terminal and paste this:
lsusb && arecord -l
Then post what output you get.

Hi there,

Here is my outputted terminal information:
[IMG]http://img195.imageshack.us/img195/2307/screenshothkm.png[/IMG]

I see that it says "Bus 007 Device 002: ID 0763:201a Midiman M-Audio Micro"... so Ubuntu is picking up the device then? 



@FacesComix - My laptop isn't powerful enough to handle a recording program in a virtual machine, nor do I think in
this day and age a virtual machine would suffice for music
recording. Thanks for the input though, I appreciate it!

@kanishkdudeja - On the back says "PN:ML03-00233", on the
front it says "M-AUDIO". 

Thank you all so much for the help so far, I would love
to make the switch completely over to linux, that's been 
my goal for the last few years but the whole recording
situation restricts me from doing so... I don't even mind
if my screen is a little dim, if I could just get this 
m-audio working I'll be waving "goodbye" to Microsoft 
immediately! 

Thanks,
-Matthew

---

### Post by cchhrriiss121212 on 2010-12-20
I can't find any reports the M-audio Micro works with Ubuntu, and the ouptut you posted shows the system does not recognise the device as a recording source (although it does see it is there).

With this in mind I'd say it is not supported on Ubuntu. You could either stick with Windows or trade it in for a device that is supported. Like the M-Audio fast-track for example.

---

### Post by kanishkdudeja on 2010-12-20
agreeing with chris121212

---

### Post by Matthew24 on 2010-12-20
> **cchhrriiss121212 said:**
> I can't find any reports the M-audio Micro works with Ubuntu, and the ouptut you posted shows the system does not recognise the device as a recording source (although it does see it is there).

With this in mind I'd say it is not supported on Ubuntu. You could either stick with Windows or trade it in for a device that is supported. Like the M-Audio fast-track for example.

Well that's a bummer. I think I'm just going to format my drive anyway and leave the windows partition really small just for recording purposes... hopefully someday I can get support for
this device because it's really great for recording and I can't
afford to buy another interface unfortunately.

Thank you for all the help!
-Matthew

---

### Post by kanishkdudeja on 2010-12-20
no problems..:)

---

### Post by Matthew24 on 2010-12-20
> **kanishkdudeja said:**
> no problems..:)

Appreciate it.

I'm going to head over to the "Multimedia & Video" section of the site and see if anyone knows of any hacks or something for this.. I'd love to be free from Windows entirely! lol.

Take care everyone.

---

