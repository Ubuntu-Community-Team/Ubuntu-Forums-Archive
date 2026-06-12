---
title: "Sattetlite l300d fan always running"
date: 2009-09-28
forum: General Help
---

### Post by rjarsena on 2009-09-28
Hi,

I'm new to Linux, Ubuntu. I have a Toshiba L300D laptop and the fan is always running even when the system is idle. Any ideas on how regulate this. I have a dual boot system, the fan works fine in Vista. Also my battery life is always showing lower than it should be in Ubuntu. Thanks.

---

### Post by QIII on 2009-09-28
I have read a lot of articles about Toshiba fan issues in Linux.  You seem to be lucky in that your fan actually runs ... most people can't seem to get theirs to run at all.

It appears that the Toshiba engineers chose to defer fan control on some models to the OS (What the...?!?!?) rather than the BIOS.

I can't vouch for this approach, but this guy makes a suggestion (not for your exact model):

[http://swinky-linuxblog.blogspot.com/2009/05/ubuntu-904-on-toshiba-satellite-l305.html](http://swinky-linuxblog.blogspot.com/2009/05/ubuntu-904-on-toshiba-satellite-l305.html)

---

### Post by rjarsena on 2009-09-29
I tried that link and it doesn't work for me, the fan still runs, never shuts off. Any other ideas? Thanks.

---

### Post by rjarsena on 2009-09-29
I tried the steps outlined in the link you provided, doesn't seem to shut the fan off, it just keeps running. Any other ideas? Thanks.

---

### Post by QIII on 2009-09-29
Again -- old, but something to look at

[http://ubuntuforums.org/showthread.php?t=846480](http://ubuntuforums.org/showthread.php?t=846480)

He's using kubuntu, so you'd have to replace "sudo kate" with "gksudo gedit".

But I wouldn't change anything just yet.

And his values for critical temperatures are a bit high IMO.  I'd buy them at Fahrenheit.

The values for max temperature given by OEMs are the point just before they spontaneously erupt into flames and set your fire alarms off.  If you operate for any amount of time anywhere near that, you'll ruin your processors in short order.

I get excited above 50C, but I have a big, hairy cooler.

---

### Post by Juno Eclipse on 2009-11-15
I have the same issue with my Satellite L505 Toshiba laptop. See [https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/321578](https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/321578)
I haven't found anything yet...

---

### Post by kristin70 on 2010-05-02
I have the same model( L300D) and the same problem. till now I have find any solution, the loud sound gets on my nerves! but I really like ubuntu so please help to find a solution!

---

### Post by Gotit on 2010-05-16
> **kristin70 said:**
> I have the same model( L300D) and the same problem. till now I have find any solution, the loud sound gets on my nerves! but I really like ubuntu so please help to find a solution!

This is how I got my A205 to behave a little better, maybe it will help you too :)
[http://ubuntuforums.org/showthread.php?p=9310596#post9310596]("http://ubuntuforums.org/showthread.php?p=9310596#post9310596")

---

### Post by kristin70 on 2010-08-26
> **Gotit said:**
> This is how I got my A205 to behave a little better, maybe it will help you too :)
[http://ubuntuforums.org/showthread.php?p=9310596#post9310596](http://ubuntuforums.org/showthread.php?p=9310596#post9310596)

I did that but it only worked for the first boot. After the second restart the fan problem didn't solved :(

---

