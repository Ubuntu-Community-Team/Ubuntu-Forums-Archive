---
title: "Need help with LIRC badly"
date: 2011-03-22
forum: General Help
---

### Post by epac90 on 2011-03-22
Hi guys,

I need some help with configuring LIRC.  Here is my situation:

I work for a local tv station in the IT department, and we control our local malls' TV schedule.  We have a linux box (ubuntu i believe) setup at the mall with a serial NTSC tv tuner on it.  From there it goes into a splitter (maybe an amp first, not sure), then to all the TV's.  The mall sends us a schedule of the TV shows that they want to show in a date/time format.  My boss wrote a simple script that would allow us to make a text file including the date and time of the show and it would automatically change the channel to the one requested when it came time for that show to come on.  With this script we only had to make up the schedules once a week, and everything else automatically do everything itself.

Well the cable provider is comcast, and they're going all digital, which means we'll have to use a DTA box to control the channels and not the TV's, which means our analog tuner is now worthless.  Here's where I need help:

We are going to hook all the TV's up to the DTA via a 4 way splitter, but we now won't be able to control the channels remotely anymore.  We built a very simple serial transmitter and are wanting to be able to change the channels with this.  Ive installed LIRC and have tried almost everything I can thing of as far as configuring it as a transmitter only but i haven't seen anybody trying to do what we're wanting to do.  We want to be able to TRANSMIT only, we do not need to recieve signal, just be able to transmit remote code to change the channels on the DTA box. 

Is this even possible?? are they're better alternatives?? What exactly do I need to do to accomplish this??
Any help would be greatly appreciated

---

### Post by blueridgedog on 2011-03-22
I suggest you post this to the LIRC mailing list:

[https://lists.sourceforge.net/lists/listinfo/lirc-list](https://lists.sourceforge.net/lists/listinfo/lirc-list)

---

### Post by epac90 on 2011-03-23
no worries guys, i got it working perfectly! thanks

---

