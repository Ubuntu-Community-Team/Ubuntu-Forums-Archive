---
title: "Wireless mouse is sticky/slow/laggy"
date: 2009-09-20
forum: General Help
---

### Post by russianbandit on 2009-09-20
I'm not quite sure what the right descriptive word here is, but my wireless (USB) mouse becomes unresponsive/laggy for short amounts of time. Like for a period of two minutes the mouse will not cooperate. I'll move the cursor, but it wont move and in about 1-2 seconds will jump to where it should be, so in a way it's sticky. It's really frustrating as the mouse practically becomes unusable for that time, and then suddenly it'll work normally again.

I can't quite figure out what could be causing this. The mouse works fine in Windows, so that rules out the hardware. I'm thinking it may have something to do with wireless pci ethernet card interrupting the wireless mouse signal.

My wireless pci card is Rosewill RNX-G300LX and the mouse is Rosewill RM-8500 2.4 GHZ.

Do you think it's the two interfering and what can I do to solve this problem? Thank you in advance.

P.S I'm on Jaunty.

---

### Post by TobiDN on 2009-09-20
I'm having a similar problem right now.
Are you completely sure it is not the batteries?
But it's *only* in linux for you?
Does it happen very often?

---

### Post by russianbandit on 2009-09-20
Not the batteries. I thought that at first but I switched them out a few times. It has to be something else.
Seems, only in linux, as my windows 7 laptop does not see this problem.
It happens once or twice an hour, depending on how intensly I use the computer.

Next time it happens I'll try to turn off the wireless card and see if it stops, to rule in/out that suspicion.

---

### Post by russianbandit on 2009-09-21
So i moved the mouse USB receiver to the front of the case USB plugin and I don't seem to experience the issue anymore. So I guess that means that it was a problem with the wireless (which is on the back of the case) interfereing somehow. This is a solution for now, but is there anyway to make the two device use separate frequencies/channels so they don't interfere in the future?

---

### Post by P4man on 2009-09-21
I have the same thing with a logitech MX revolution: when there is intensive wifi traffic, the mouse will behave erratic. The AP is right next to my USB hub though and both work in the 2.4 GHz range. I found the problem is reduced significantly after changing the my accesspoint frequency (channel)

---

### Post by russianbandit on 2009-09-21
I also tried changing the channel on my wireless router to channel 11 instead of 9, but that didn't change anything.

So is this fairly normal for the mouse and wireless adapter to interfere with each other like that? Could it be because both of the peripherals are made by Rosewill (frequency and channels are the same)?

---

### Post by P4man on 2009-09-21
> **russianbandit said:**
> I also tried changing the channel on my wireless router to channel 11 instead of 9, but that didn't change anything.

Try further down, go for extremes. Try channel 1.

> o is this fairly normal for the mouse and wireless adapter to interfere with each other like that? 

I guess. They both operate in 2.4 GHz band (as does my cordless phone, bluetooth, wifi and my wireless tv transmitter). If you got a powerful transmitter to close by, expect interference problems.

> Could it be because both of the peripherals are made by Rosewill (frequency and channels are the same)?

I dont think the manufacturer has anything to do with it. Its just interference. If you got a laptop, put it next to your microwave and turn the microwave on, and see how good your wifi connection still is (hint: [http://blogs.zdnet.com/Ou/?p=578](http://blogs.zdnet.com/Ou/?p=578) ). The brand won't have much impact.

---

### Post by pressurepoint on 2009-10-21
So how did you get your rm 8500 wireless mouse to work in the first place? I am running jaunty server 64 bit with a minimum gnome desktop and no wireless joy at the moment, and no luck searching as well.

---

