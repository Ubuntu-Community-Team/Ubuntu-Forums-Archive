---
title: "Boot time.. 8.6 seconds, how is this possible?"
date: 2010-10-04
forum: General Help
---

### Post by schwabdale on 2010-10-04
Can someone provide instructions on how to achieve this?

---

### Post by andrewthomas on 2010-10-04
What are you referring to?   

What link claims an 8.6 s boot?

---

### Post by schwabdale on 2010-10-04
Sorry, 

[http://www.jamesward.com/2010/09/08/ubuntu-10-10-boots-in-8-6-seconds/](http://www.jamesward.com/2010/09/08/ubuntu-10-10-boots-in-8-6-seconds/)

---

### Post by sikander3786 on 2010-10-04
He is booting from SSD in that link. SSDs are pretty faster than IDE HDDs. You want to achieve the same with a SSD or an IDE drive?

---

### Post by CharlesA on 2010-10-04
> **sikander3786 said:**
> He is booting from SSD in that link. SSDs are pretty faster than IDE HDDs. You want to achieve the same with a SSD or an IDE drive?

SSDs are even faster then SATA3 HDDs.

I will never understand why people want super fast boot times, I mean, how many times do you actually boot up the machine when you are using it?

---

### Post by schwabdale on 2010-10-04
IDE or SATA. 

What type of time is possible?

---

### Post by schwabdale on 2010-10-04
> **CharlesA said:**
> SSDs are even faster then SATA3 HDDs.

I will never understand why people want super fast boot times, I mean, how many times do you actually boot up the machine when you are using it?

If its a laptop, you could boot it multiple times a day.

---

### Post by sikander3786 on 2010-10-04
> SSDs are even faster then SATA3 HDDs.

Yes I agree. Just forgot to mention :-)

The only one reason I understand behind fast boot times is to impress your friends and colleagues with your machine and your OS :lolflag:

---

### Post by CharlesA on 2010-10-04
> **schwabdale said:**
> If its a laptop, you could boot it multiple times a day.

Hrm. I don't normally power my laptop off, usually it's set to suspend or hibernate, both of which don't require a full "boot up."

> **sikander3786 said:**
> 
The only one reason I understand behind fast boot times is to impress your friends and colleagues with your machine and your OS :lolflag:

Indeed. Is there really a huge difference between a 10 second boot time and a 30 second boot time, except "haha my computer boots faster then yours." :confused:

---

### Post by Captain Giraffe on 2010-10-04
After POST my boot is about 10 secs on a 10.4; POST however, takes about 25 secs.

---

### Post by Guitar John on 2010-10-04
> **CharlesA said:**
> I will never understand why people want super fast boot times, I mean, how many times do you actually boot up the machine when you are using it?

I don't worry about it right down to the second, but I remember my old 366 MHz machine.  The routine was hit the power button, go make coffee. :(

---

### Post by Captain Giraffe on 2010-10-04
Now on my new windows machine, I hit the power button in the morning, take a shower, make coffe, go to the bakers, drink coffe and have a (not even sudoed) sandwich. Log in, finish sandwich.

---

### Post by davidvandoren on 2010-10-04
mine boots right now in 18 seconds.

If you use grub menu to let you choose between windows and linux you could change that to 1 second instead of ten. 

You can turn of memory check in your bios. 

You can turn off automatic connect to the network but I think it does not matter anymore since I am on my desktop already and ubuntu tries to connect to my local network which it can't.

Go to system personal and startup applications and remove the things you don't need. Bluetooth,ubuntu one,etc

---

### Post by SeanBlader on 2010-10-05
There's usually a thread in the development forum for the next release that has people's Grub to desktop boot times using bootchart. Under Jaunty on my 1.4 GHz Adamo with an SSD I'd get about 13 seconds, and now with Maverick it's Grub to desktop in about 11 seconds both with everything running, bluetooth, pulseaudio, everything a default install places in the startup. Goes to show fast processor time is less important than fast drive speeds.

As for why you do it? I'd say the reasons are many, but the two primaries are:

1. compete with Windows. Windows we all know restarts itself fairly often depending on what you're doing, whether it's weekly patch day, or if it's a random crash, or you just need to clear out some leaking memory.
2. because you can. It's like climbing a mountain, you do it because it's there.

A few others are, for bragging rights on your choice of hardware, for productivity gains, etc.

---

### Post by KegHead on 2010-10-05
Wow!

I just fired up my Dell mini9 w/16gb ssd. (10.10)

It took 45 seconds.

Am I missing something?

KegHead

---

