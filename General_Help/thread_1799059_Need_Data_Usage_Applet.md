---
title: "Need Data Usage Applet"
date: 2011-07-07
forum: General Help
---

### Post by Rushyang on 2011-07-07
Hey guys,
I need applet which shows the total data usage (In+out) (of the current session or since the uptime) on the panel. 

I searched a lot, but everytime I had to click somewhere to see my data usage. I don't want that. I want my data usage displayed regularly on the panel.

---

### Post by CatKiller on 2011-07-07
You can get Conky to do it, or there's a Netmonitor screenlet that can show you that information. Both of those sit on the desktop, so you have room to display all sorts of information.

---

### Post by Rushyang on 2011-07-07
> **quee.raj said:**
> i need a simple internet data usage meter which works in back ground and tell me detaits about internt data usage per day.

I am using "KNEMO" for that. It's great tool. You can also set the limits between some duration, if it exceeds that limit.. YOu will be notified too.

---

### Post by Rushyang on 2011-07-07
> **CatKiller said:**
> You can get Conky to do it, or there's a Netmonitor screenlet that can show you that information. Both of those sit on the desktop, so you have room to display all sorts of information.

netspeed's applet doesn't show the "total data usage".. It just shows the speed of net you're using.

---

### Post by CatKiller on 2011-07-07
> **Rushyang said:**
> netspeed's applet doesn't show the "total data usage".. It just shows the speed of net you're using.
That's why I told you to use Netmonitor... :)

---

### Post by Rushyang on 2011-07-08
> **CatKiller said:**
> That's why I told you to use Netmonitor... :)
:confused:I need TOTAL DATA USAGE displaying applet for the current session.

For example, If I have used internet for 2 hours, then it should show the usage of whatever I have used let's say 150 MB, to the top panel...

What you're suggesting is the speed..like  250kbps etc..

---

### Post by CatKiller on 2011-07-08
> **Rushyang said:**
> :confused:I need TOTAL DATA USAGE displaying applet for the current session.

For example, If I have used internet for 2 hours, then it should show the usage of whatever I have used let's say 150 MB, to the top panel...

What you're suggesting is the speed..like  250kbps etc..

Pay attention.> 

[Screenlet Package] 
Name=NetmonitorScreenlet
Author=Jovicic Nemanja aka drxnele based on Netmonitor0.6 by Helder Fraga
Desc=A Screenlet that displays net traffic , and **month or day totals**
Version=0.9
ApiVersion=0.1.2
Created=2007/10/08]

Not "netspeed" or any other thing that doesn't do what you want, but the **very thing** that you've been given the name for that does **exactly what you want**.

---

### Post by Rushyang on 2011-07-11
To CatKiller,
Yeah you're right. I was reading it wrong. I thought you've given me netspeed. I just checked netmonitor & netmonitor **screenlet** might is doing what I tell.. but to be honest, I don't want ** screenlet **. 

I need **Applet**. which can constantly shown on above panel in ubuntu. To be honest, I hate screenlets.

Thanks for your kind reply. :D I'm sorry i was reading that wrong. ;)

---

### Post by CatKiller on 2011-07-11
> **Rushyang said:**
> To be honest, I hate screenlets.

Fair enough :)

If you don't mind it being per-session, there's a couple of options. One that's a panel applet is *gnome-netstatus-applet*, in the Universe repository. It doesn't display the usage directly, but if you click on it, it will show you the per-session activity.

Other options that open a window are System -> Administration -> System Monitor and System -> Administration ->Network Tools. Both of these will show information about your usage.

Personally, I use Conky to do this. I've just got *${totaldown eth0}* and *${totalup eth0}* in my .conkyrc. I don't see any reason in principle why you couldn't get Conky to draw its box on top of the panel as an alternative to having a panel applet.

There are a variety of different console or graphical tools to let you monitor network usage (Linux is often used on servers and routers, after all) of varying degrees of user-friendliness. The simplest is probably querying the kernel itself:```
cat /proc/net/dev
```Everything else is nicer than that. There's a list of tools near the bottom of [this page]("http://humdi.net/vnstat/") that might point you to something that you like. I haven't yet been able to find a panel applet that does it, but if you don't mind getting your hands dirty you could probably write a simple one that displays the output from one of the other tools.

---

### Post by Habitual on 2011-07-11
+1 for conky and what CatKiller said about your own tool(s)

vnstat (could be used with conky) for example:

vnstat | \grep -A 5 daily
```
   daily
                     rx      |     tx      |    total    |   avg. rate
     ------------------------+-------------+-------------+---------------
     yesterday     39.25 MiB |   11.15 MiB |   50.40 MiB |    4.78 kbit/s
         today     89.77 MiB |   96.21 MiB |  185.97 MiB |   34.78 kbit/s
     ------------------------+-------------+-------------+---------------
```

Hourly, daily or Monthly could just as easily be displayed on the output.
This is just an EXAMPLE of what some basic coding can do. Combined with conky,it could easily be displayed on the desktop.

---

### Post by CatKiller on 2011-07-13
[This]("http://sourceforge.net/projects/netramon/") came up in another thread. Don't know if it's the kind of thing that you want.

---

