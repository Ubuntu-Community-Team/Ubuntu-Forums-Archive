---
title: "Sun Java 6"
date: 2009-07-17
forum: General Help
---

### Post by Felicity_X on 2009-07-17
My system is Hardy Heron and I am very happy with it on the whole.  However, the last couple of weeks I have found that it is not up to some webinars I attend, in particular those which use a lot of small java applets opening up moveable child windows all over the place.

I recently attempted to use Oanda currency trading platform, [www.fxtrade.com](www.fxtrade.com).  Running from the web did not work at all.  I was assured by their help person that downloading the desktop should work on Ubuntu, despite the fact that they only give instructions for windows and mac.  However, I got a message that the desktop could not download because something was missing.  Their tech people have subsequently e-mailed me to say that it looked to them like the java was not set up properly.

I have looked on Synaptic Manager and I have installed:
     sun-java-6-bin
     sun-java6-jrc

I have available but not installed the plugin and the fonts.

I am presuming that the plugin & perhaps fonts are what could be missing as, since I don't develop, the source code and development tools are unlikely to be needed. 

What I want to know is; should their java based desktop work on Ubuntu, or is it dangerous to download?

Secondly, I have had bad experiences in the past with getting java in a knot.  What is the correct way to download the missing files?  Can I just download them from Synaptic Manager in the usual way, or do I need to completely remove the current java environment and reload everything together??:-k

---

### Post by kostkon on 2009-07-17
Yes, try installing the Sun Java plugin from Synaptic.

Then you'll need to open a terminal and give the following command
```
sudo update-java-alternatives -s java-6-sun
```
to set the Sun Java as the default JVM in your system. This will also make Firefox to use the Sun Java plugin and not the OpenJDK one.

---

### Post by Felicity_X on 2009-07-18
Thank you very much, Kostkon.  I did as you said and everything works perfectly.

---

### Post by isparkes on 2009-07-30
Wow. Ubuntu forum support sometime really rocks!

Thx Kostkon

---

