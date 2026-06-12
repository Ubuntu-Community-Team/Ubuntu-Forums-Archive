---
title: "Problems w/ Suspend"
date: 2012-08-01
forum: General Help
---

### Post by Dan Again on 2012-08-01
I just built a computer last night...i3 processor, SSD. It seems to be having a problem w/ suspending. When I manually put the computer into suspend mode, the monitor never turns off or goes to sleep. Furthermore, when I walk away from the computer, the monitor goes to sleep after 5 minutes, when Ubuntu turns the display off, but seems to turn back on after 10 minutes when Ubuntu puts the computer into suspend. I'd like the monitor to go to sleep during suspend. Does anyone know how I can make this happen?

---

### Post by irv on 2012-08-01
> **Dan Again said:**
> I just built a computer last night...i3 processor, SSD. It seems to be having a problem w/ suspending. When I manually put the computer into suspend mode, the monitor never turns off or goes to sleep. Furthermore, when I walk away from the computer, the monitor goes to sleep after 5 minutes, when Ubuntu turns the display off, but seems to turn back on after 10 minutes when Ubuntu puts the computer into suspend. I'd like the monitor to go to sleep during suspend. Does anyone know how I can make this happen?

It would be helpful to know what the monitor is? Did you check setting on the monitor in its setting. I am taking that this is not a laptop? You did give much information. Have you check your setting in the power manager?

---

### Post by Dan Again on 2012-08-01
> **irv said:**
> It would be helpful to know what the monitor is? Did you check setting on the monitor in its setting. I am taking that this is not a laptop? You did give much information. Have you check your setting in the power manager?

I am using an [ASUS VK248H-CSM]("http://www.newegg.com/Product/Product.aspx?Item=N82E16824236261") monitor. I did check the monitor settings and did not see anything that seemed relevant. Furthermore, since the monitor goes to sleep when Ubuntu turns the display off, I don't think the problem is the monitor settings. You are correct, this is not a laptop. I am using the motherboard that comes with [this]("http://www.newegg.com/Product/Product.aspx?Item=N82E16856115047") system. I have checked my power settings insofar as that is where I set the behavior for putting the system into suspend mode after 10 minutes.

---

### Post by Dan Again on 2012-08-01
Bump. Just to make sure the problems is absolutely clear, Ubuntu is able to turn off the display after 5 minutes, per the settings I selected in "Brightness & Lock". However, after 10 minutes, when Ubuntu puts my computer into suspend mode, per the settings I selected in "Power Management", my monitor turns back on and does not go back to sleep. It appears that for some reason suspend mode is keeping my monitor awake.

---

### Post by ahallubuntu on 2012-08-01
Is your computer going into suspend at all, or is it just locking up? Can you resume successfully?  It could just be locking up - that could be why the monitor is "stuck on."

It's very common for Linux to have issues with suspend.  I built a Sandy Bridge system (Intel H61 northbridge chipset) recently to be used as a server.  I briefly played with suspend on it and it did not work.  Suspend works great on some older systems with Core 2 Duo CPUs - I have another server that is mostly suspended but I wake it up with "Wake On Lan" occasionally to access it, then put it back to sleep.

You have an Intel H77 chipset on your Biostar.  Maybe it has issues with suspend, too?  You might find Hibernation (suspend to disk) works better, and with an SSD Hibernation (and resume) should be very fast.  If suspend doesn't work but hibernation does, you can also change the default sleep mode to "hibernation."  Hibernation is disabled by default in 12.04 LTS - I re-enabled it (forget how - easy, google for it).  You might give that a try.

---

### Post by audiomick on 2012-08-01
How much RAM do you have, and how big is your swap? Suspend will only work when you have a little more swap than you have RAM.

---

### Post by Dan Again on 2012-08-01
> **ahallubuntu said:**
> Is your computer going into suspend at all, or is it just locking up? Can you resume successfully?  It could just be locking up - that could be why the monitor is "stuck on."

It's very common for Linux to have issues with suspend.  I built a Sandy Bridge system (Intel H61 northbridge chipset) recently to be used as a server.  I briefly played with suspend on it and it did not work.  Suspend works great on some older systems with Core 2 Duo CPUs - I have another server that is mostly suspended but I wake it up with "Wake On Lan" occasionally to access it, then put it back to sleep.

You have an Intel H77 chipset on your Biostar.  Maybe it has issues with suspend, too?  You might find Hibernation (suspend to disk) works better, and with an SSD Hibernation (and resume) should be very fast.  If suspend doesn't work but hibernation does, you can also change the default sleep mode to "hibernation."  Hibernation is disabled by default in 12.04 LTS - I re-enabled it (forget how - easy, google for it).  You might give that a try.

This is a good point. I assumed that the system was successfully suspending, because when I wake it, I am asked for a password. However, I am in no way certain that it is completely suspending. I will try re-enabling hibernation and seeing how that works.

> How much RAM do you have, and how big is your swap? Suspend will only work when you have a little more swap than you have RAM.

I have 8G RAM. Not sure how big swap is...I just did a simple install of Ubuntu onto the HD w/o partitioning it.

---

### Post by Dan Again on 2012-08-01
> **ahallubuntu said:**
> Is your computer going into suspend at all, or is it just locking up? Can you resume successfully?  It could just be locking up - that could be why the monitor is "stuck on."

It's very common for Linux to have issues with suspend.  I built a Sandy Bridge system (Intel H61 northbridge chipset) recently to be used as a server.  I briefly played with suspend on it and it did not work.  Suspend works great on some older systems with Core 2 Duo CPUs - I have another server that is mostly suspended but I wake it up with "Wake On Lan" occasionally to access it, then put it back to sleep.

You have an Intel H77 chipset on your Biostar.  Maybe it has issues with suspend, too?  You might find Hibernation (suspend to disk) works better, and with an SSD Hibernation (and resume) should be very fast.  If suspend doesn't work but hibernation does, you can also change the default sleep mode to "hibernation."  Hibernation is disabled by default in 12.04 LTS - I re-enabled it (forget how - easy, google for it).  You might give that a try.

So, I checked, and hibernation seems to work fine on my computer. This is an acceptable solution for me. However, I followed the steps in [this]("https://help.ubuntu.com/12.04/ubuntu-help/power-hibernate.html") guide, and I do not see a "Hibernate" option anywhere. What do you mean when suggest I set my default sleep behavior to "Hibernate"?

---

### Post by audiomick on 2012-08-01
> **Dan Again said:**
> I have 8G RAM. Not sure how big swap is...I just did a simple install of Ubuntu onto the HD w/o partitioning it.

If you're interested, you could look in the system monitor. One of the tabs in there shows you how much RAM and how much swap your are using, and the total available.

---

### Post by Dan Again on 2012-08-02
So, the problem is "solved" insofar as I have implemented an acceptable alternative to successfully suspending my system. Per ahallubuntu I re-enabled hibernate on my system, then I used dconf to set the default sleep behavior of my system.

---

### Post by irv on 2012-08-02
> **audiomick said:**
> If you're interested, you could look in the system monitor. One of the tabs in there shows you how much RAM and how much swap your are using, and the total available.

You can also just open a terminal and type "top" and it will give you this information.

Also I am running a server using 10.04 I do not use suspend or hibernation but just turn off the monitor. To be honest with you I can remember the last time I turn the monitor on. I just remote into it using my laptop and do update and changes. In fact I did it this morning.
[ATTACH]222137[/ATTACH]

---

### Post by Dan Again on 2012-08-02
> **irv said:**
> You can also just open a terminal and type "top" and it will give you this information.

Also I am running a server using 10.04 I do not use suspend or hibernation but just turn off the monitor. To be honest with you I can remember the last time I turn the monitor on. I just remote into it using my laptop and do update and changes. In fact I did it this morning.
[ATTACH]222137[/ATTACH]

Well, this is a desktop system, not a server. In fact, one of the primary qualities I was going after when building this system was the large monitor. So this solution does not work for me.

---

