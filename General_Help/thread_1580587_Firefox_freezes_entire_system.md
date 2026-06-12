---
title: "Firefox freezes entire system"
date: 2010-09-23
forum: General Help
---

### Post by rezonatix3 on 2010-09-23
When I click certain links, such as the one below, Firefox consistently crashes.

The bigger problem is that when it does, everything grinds to a halt, and I have to press the machine's power button.

Is there a way to kill processes when the system locks up? This is on Ubuntu 10.04 Lucid Lynx, using GNOME.

[Link to 2 MB PNG file (MAY CRASH YOUR BROWSER)](http://data.glacicle.org/screens/latest-desktop.png)

---

### Post by sikander3786 on 2010-09-23
Try to open the link in Chromium. Install by

```

sudo apt-get install chromium-browser

```

Also please list your system specs.

---

### Post by lykeion on 2010-09-23
Well, I had no problems opening the link, and it's really hard to say why this happen on your computer. 

But does everything freeze or can you still move the mouse cursor, switch to other open applications with alt+tab?

You could try launching firefox from a terminal, that way you can easily kill it with ctrl+c when it freezes.

---

### Post by rezonatix3 on 2010-09-23
I can move the mouse cursor, but I cannot switch to other applications. Clicking on a terminal window doesn't give it focus. So it's like the system is working extremely hard on one futile task to the exclusion of everything else.

My specifications are Intel Core 2 Duo 1.8 GHz and 2 GB RAM. This is on a ThinkPad T61. Had the same problem with Debian Squeeze.

Chromium requires system update, will report when it's done.

---

### Post by lykeion on 2010-09-23
Some things to try to avoid/debug Firefox freezing:

* Launch it from a terminal and watch any error output:
Applications > Accessories > Terminal > enter "firefox"
Resize the windows so you could see them side by side, then enter the troublesome url in the Firefox address field

* Clear Firefox Browser History
Firefox > Edit > Preferences > Privacy > Clear recent history

* Disable visual effects (Preferences > Appearance > Visual Effects > None

* Start Firefox in Safe Mode
See _[http://kb.mozillazine.org/Safe_Mode](http://kb.mozillazine.org/Safe_Mode)_

* Troubleshoot Firefox plugins (Java, Flash, Adobe Redaer)
See _[http://support.mozilla.com/en-US/kb/Troubleshooting+plugins](http://support.mozilla.com/en-US/kb/Troubleshooting+plugins)_

* Disable "Problematic" Firefox Extensions
See _[http://kb.mozillazine.org/Problematic_extensions](http://kb.mozillazine.org/Problematic_extensions)_

Also search this forum using search words like "firefox freeze high cpu" or similar.

---

### Post by Crazedpsyc on 2010-09-23
Also UNINSTALL CHROMIUM RIGHT NOW!!!!!!!!!!!!!!!!!!!!!!!!! Unless you want everything you type to be logged and sent to google? There is at least one keylogger integrated into chrome, as well as a few rootkits. after you uninastall chrome install rkhunter and run "rkhunter --check" just to see if it finds anything left over

---

### Post by lykeion on 2010-09-24
- Firefox consistently crashes...
- Try to open the link in Chromium.

Isn't this a little bit like:
- I have a problem with my car...
- Take the motorcycle instead.

---

### Post by sabya mondal on 2010-09-24
hii sometimes these happens in some other operating system also ....
like in my computer, yahoo mail crashes in firefox, but works fine with chome
sometimes the problems lie in the webpage sturcuture+local system issue

so plzz try another browser

---

### Post by rezonatix3 on 2010-09-24
It's not that my browser crashes that bothers me. It's that it takes the rest of the system with it when it does so.

---

### Post by Machiavelli on 2010-09-24
get rid of firefox and get chrome instead.

---

### Post by Dustin2128 on 2010-09-24
> **Crazedpsyc said:**
> Also UNINSTALL CHROMIUM RIGHT NOW!!!!!!!!!!!!!!!!!!!!!!!!! Unless you want everything you type to be logged and sent to google? There is at least one keylogger integrated into chrome, as well as a few rootkits. 
[IMG]http://www.tfhp.org/images/tinfoil-hat.jpg[/IMG]
It's open source. If on the off chance, you do find them, remove them and recompile. Maybe even submit this as a major security flaw and get paid 3733.70$

Anyway, are you using the vanilla firefox? 4 beta? minefield? 
The top two browsers I'd recommend besides firefox are opera, then chrome(ium).

---

### Post by Aaron5367 on 2010-09-24
I can it making you run out of RAM fairly easily, firefox does love the RAM. Try watching system monitor while it loads?

---

### Post by lykeion on 2010-09-25
I feel a bit sorry for OP here. He's having problems with Firefox (and maybe his system too), and he gets a pointless Firefox vs Chromium debate.

@rezonatix3
Have you tried any of the things I suggested in my _[post]("http://ubuntuforums.org/showpost.php?p=9881310&postcount=5")_ and gave the troubleshooting links I listed any help?

---

### Post by rezonatix3 on 2010-09-26
> **lykeion said:**
> Have you tried any of the things I suggested in my _[post]("http://ubuntuforums.org/showpost.php?p=9881310&postcount=5")_ and gave the troubleshooting links I listed any help?
Yes. I haven't had any problems recently, though. Even the link I posted opens fine.

So either the problem is gone (updated Firefox the other day), or I'll get back to you if I can find a better way to reproduce it.

---

### Post by Wilfred on 2010-09-29
had the same issue.

removing libmoon (sudo apt-get remove libmoon) fixed it for me.

Hope it works for you as well!

---

### Post by gloken on 2010-10-24
I've got an interesting Firefox freeze for you.

On my main account I can use Firefox without any difficulties. On a secondary user account Firefox causes system wide freezes after only a few minutes of use. The second account is bare bones without any extra addons or anything.

Any thoughts on why one account would be affected and not another?

---

