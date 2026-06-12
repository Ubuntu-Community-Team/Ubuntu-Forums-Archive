---
title: "Webcam Surveilance Software"
date: 2009-11-26
forum: General Help
---

### Post by stuart264 on 2009-11-26
Does anyone know of any good reliable software for Ubuntu I can use to set up my webcam to stream off my Ubuntu box upto some server space I have on Bluehost so I can keep an eye on my fish tank while I am away next month?

---

### Post by sedawk on 2009-11-26
There is a bunch of tools to take pictures from a webcam:

[http://tldp.org/HOWTO/html_single/Webcam-HOWTO/#FRAMEGRABBERS](http://tldp.org/HOWTO/html_single/Webcam-HOWTO/#FRAMEGRABBERS)

There is mentioned an application "webcam" that might
do all you need.
(Here is another example which also shows the configuration
 file:[http://www.aboutdebian.com/webcam.htm](http://www.aboutdebian.com/webcam.htm) ).

One alternative solution might be to run a web server on your own PC so you do not need to transfer pictures. In that case
you might need a dynamic DNS entry to find your PC on the internet when it changes IP (e.g using a (free) "dns-provider" like dyndns.org). Then your web page could even show more
advanced data (temperatur, water quality, etc).
I guess there is an USB device for everything ;-)

Instead of having to actively check the status of your
fishtank you can configure your PC to alarm you
in case something is unusual. This requires some
addition hardware and software to send you (or
a neighbour) a SMS or prerecorded phone message.

---

### Post by memilanuk on 2009-11-26
Another possibility:

[http://www.zoneminder.com/](http://www.zoneminder.com/)

---

