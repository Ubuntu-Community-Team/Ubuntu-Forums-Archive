---
title: "Battery indicator drops to half"
date: 2011-05-06
forum: General Help
---

### Post by bxojr on 2011-05-06
Hi, all. I'm new to Linux but not to computers. I've got Natty installed on a Lenovo IdeaPad S12 netbook, and for the most part it's working well. However, I'm having a small annoyance with the battery indicator. I've seen a few other threads about the battery indicator, but not this exact problem.

When I first power up after a full charge, the battery indicator shows full as I expect it to. But within minutes, it drops to about half. (If I reboot into Windows, it shows full.) Sometimes it doesn't drop quite that much, but it's always a sudden and significant drop, within the first five minutes or so. The actual battery is healthy, as far as I know; I've been using it under Windows with no problem.

It's not clear to me whether my actual battery life is any shorter (I haven't used it enough to judge), but Ubuntu certainly seems to think it has much less of a charge than it has. Any ideas?

---

### Post by varunendra on 2011-05-07
I'd suggest to test and see yourself how long ubuntu runs on battery. If this duration is significantly less than expected, then it may be a problem with resource usage (CPU, HDD, LCD brightness,... etc.), not the indicator itself.

In that case (if it is so at all), you may have to tweak/troubleshoot power management options rather than battery sensing/indication.

The battery state is mostly determined by sensing its voltage which may drop significantly if too much ampere is consistently drawn off it. And will again rise significantly as soon as this ampere drops. This may be an explanation why windows sees it 'full' when you switch to it (assuming Ubuntu is using too much power for some reason, thus consistently drawing high amperes).

But we can be sure only after you confirm the uptime on battery. If it is okay, then the indicator may be on fault.

---

### Post by bxojr on 2011-05-07
OK, that makes sense. Thanks for the suggestion ... I'll post again when I have some results.

---

### Post by bxojr on 2011-05-11
OK, I have some results from my battery tests.

I ran two tests on Ubuntu 11.04 and two on Windows 7. In each case, I unplugged the computer with a full charge; I had a Web browser open to twitter.com so there would be some activity, but otherwise did not use the computer at all. All power-saving features were turned off, and I let the computer run until it automatically went into suspend due to low battery.

The results were as follows:

[LIST]
[*]Windows: 3:13 and 3:45
[*]Ubuntu: 3:42 and 3:55
[/LIST]
So there's obviously no problem with Ubuntu's actual battery usage.

The battery gauge, however, continues to behave unpredictably on Ubuntu. The first time, it didn't show any sudden drops, but it reached empty at least an hour before the battery actually quit. The second time, it dropped immediately to about 80%, then jumped back up to 100%, then dropped again. And again it reached empty about an hour too soon.

So my conclusion from all of this is that, on my hardware at least, the Ubuntu battery gauge is erratic, and pretty consistently shows less charge remaining than is actually available. Not a show-stopper (better than showing a charge when there is none!) but a bit disconcerting.

---

### Post by wildmanne39 on 2011-05-11
> **bxojr said:**
> OK, I have some results from my battery tests.

I ran two tests on Ubuntu 11.04 and two on Windows 7. In each case, I unplugged the computer with a full charge; I had a Web browser open to twitter.com so there would be some activity, but otherwise did not use the computer at all. All power-saving features were turned off, and I let the computer run until it automatically went into suspend due to low battery.

The results were as follows:

[LIST]
[*]Windows: 3:13 and 3:45
[*]Ubuntu: 3:42 and 3:55
[/LIST]
So there's obviously no problem with Ubuntu's actual battery usage.

The battery gauge, however, continues to behave unpredictably on Ubuntu. The first time, it didn't show any sudden drops, but it reached empty at least an hour before the battery actually quit. The second time, it dropped immediately to about 80%, then jumped back up to 100%, then dropped again. And again it reached empty about an hour too soon.

So my conclusion from all of this is that, on my hardware at least, the Ubuntu battery gauge is erratic, and pretty consistently shows less charge remaining than is actually available. Not a show-stopper (better than showing a charge when there is none!) but a bit disconcerting.

Hi, that does seem to be a problem when reporting battery life in natty, I will research it for you and see if there is a fix for it.:)

---

### Post by wildmanne39 on 2011-05-11
> **bxojr said:**
> OK, I have some results from my battery tests.

I ran two tests on Ubuntu 11.04 and two on Windows 7. In each case, I unplugged the computer with a full charge; I had a Web browser open to twitter.com so there would be some activity, but otherwise did not use the computer at all. All power-saving features were turned off, and I let the computer run until it automatically went into suspend due to low battery.

The results were as follows:

[LIST]
[*]Windows: 3:13 and 3:45
[*]Ubuntu: 3:42 and 3:55
[/LIST]
So there's obviously no problem with Ubuntu's actual battery usage.

The battery gauge, however, continues to behave unpredictably on Ubuntu. The first time, it didn't show any sudden drops, but it reached empty at least an hour before the battery actually quit. The second time, it dropped immediately to about 80%, then jumped back up to 100%, then dropped again. And again it reached empty about an hour too soon.

So my conclusion from all of this is that, on my hardware at least, the Ubuntu battery gauge is erratic, and pretty consistently shows less charge remaining than is actually available. Not a show-stopper (better than showing a charge when there is none!) but a bit disconcerting.

Hi, this is what I found on your problem and it is being worked on here is the link.
[http://www.phoronix.com/scan.php?page=news_item&px=OTM2NQ](http://www.phoronix.com/scan.php?page=news_item&px=OTM2NQ) :)

---

### Post by bxojr on 2011-05-12
Hmm ... thanks for the link. From what I read, that issue seems to cause increased power consumption, which is not what I'm seeing; as far as I can tell, my power consumption is normal, but the gauge just isn't registering accurately. But of course I don't know how the power subsystem works, so maybe these issues are interrelated.

---

### Post by varunendra on 2011-05-13
So at least it is clear now that the power consumption is not the problem. That's good!

Now install acpi first:
```
sudo apt-get install acpi
```
then, when the indicator applet shows battery low or empty (when it should not), enter this command in terminal and see what it tells:
```
acpi -V
```

If it (wrongly) shows the status same as the applet, then it may be a bug in the kernel. If it shows a different (and correct) status, it may be a bug in the Gnome-Power management module or the applet itself.

In the latter case, you may try installing 'battery-stats' from the repositories,
```
sudo apt-get install battery-stats
```
(will install multiple packages for support)
or 'Battery Status Indicator' suggested here: [http://www.techdrivein.com/2011/05/10-useful-application-indicators-for.html](http://www.techdrivein.com/2011/05/10-useful-application-indicators-for.html)
```
sudo apt-add-repository ppa:iaz/battery-status
sudo apt-get update
sudo apt-get install battery-status
```
(will install a single package which can be easily removed if required)

Alternatively, you may try KDE (again, for the latter case, but not suggested for such a minor problem, especially when it is not 'guaranteed' to work)

Hope to hear something better. :)

---

