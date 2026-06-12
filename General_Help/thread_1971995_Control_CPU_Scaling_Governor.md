---
title: "Control CPU Scaling Governor"
date: 2012-05-03
forum: General Help
---

### Post by Hungry Man on 2012-05-03
There are times where I'd like to put my computer on Conservative/ On Demand or set a specific clock rate. I'd like a simple to use GUI application, if it exists, to do so.

I recall there being something for this back when I used Gnome2 a long long time ago. Anyone know of such a thing that works with Unity?

---

### Post by TBABill on 2012-05-03
I don't know of a GUI for Gnome 3/Unity, but you can open a terminal and ```
sudo cpufreq-set --governor ondemand
``` and change ondemand to whatever setting you want to use, then do the same to change it back. you may have to install cpufreq-tools to do so, but I may be wrong. Haven't had cpufreq issues in quite some time and I think the kernel sets ondemand by default.
 
[http://manpages.ubuntu.com/manpages/hardy/man1/cpufreq-set.1.html](http://manpages.ubuntu.com/manpages/hardy/man1/cpufreq-set.1.html)

---

### Post by matt_symes on 2012-05-03
Hi

> **Hungry Man said:**
> There are times where I'd like to put my computer on Conservative/ On Demand or set a specific clock rate. I'd like a simple to use GUI application, if it exists, to do so.

I recall there being something for this back when I used Gnome2 a long long time ago. Anyone know of such a thing that works with Unity?

Is jupiter available for Gnome3/Unity ? I have used that in the past on my laptop under Lucid.

[https://launchpad.net/~webupd8team/+archive/jupiter](https://launchpad.net/~webupd8team/+archive/jupiter)
[http://www.webupd8.org/2011/09/jupiter-applet-finally-available-for.html](http://www.webupd8.org/2011/09/jupiter-applet-finally-available-for.html)

Kind regards

---

### Post by Hungry Man on 2012-05-03
A UI is preferable but I can handle using the terminal if I have to for this.

I'll check those out matt, thanks.

edit: Jupiter doesn't seem to be effecting any settings.

---

### Post by TBABill on 2012-05-03
If you don't use the terminal a great deal, when you re-open terminal and  hit the up arrow it will scroll through previous commands you have issued. Will save you some time getting to the right one versus typing it out, especially if you happen to type at average to slow speeds.

---

### Post by dcstar on 2012-05-03
> **Hungry Man said:**
> There are times where I'd like to put my computer on Conservative/ On Demand or set a specific clock rate. I'd like a simple to use GUI application, if it exists, to do so.

I recall there being something for this back when I used Gnome2 a long long time ago. Anyone know of such a thing that works with Unity?

The CPU Frequency Scaling applet is still available in Gnome 3.

Since there are no panels in Unity, there is nowhere for these Gnome 3 tools to exist (that's the downside of designing an interface for small screen portable devices, they lose so much functionality for people who use big screens).

---

### Post by Hungry Man on 2012-05-03
There's a bar right on the top of the screen with unity. I've seen applications use it. That's what I'm looking for basically.

---

### Post by dcstar on 2012-05-03
> **Hungry Man said:**
> There's a bar right on the top of the screen with unity. I've seen applications use it. That's what I'm looking for basically.

That is for the "Active" application and **nothing **else.

You have just highlighted the "improvement" of Unity, to save one pathetic line that contains a few pixels you lose the old panel that used to hold all these useful tools.

Makes some sense when you are using a small screen device like a phone of pad, makes little sense when using a large monitor - but that's progress (isn't it?)

---

### Post by Hungry Man on 2012-05-03
IDK what you mean. Jupiter would work perfectly if it worked at all. It creates an icon right up at the top and lets me control from that menu. Just like I could with Gnome 2, except it doesn't work for some reason.

---

