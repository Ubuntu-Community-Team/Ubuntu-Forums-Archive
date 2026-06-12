---
title: "CPU Monitor Applet?"
date: 2009-07-17
forum: General Help
---

### Post by bug67 on 2009-07-17
I would like an applet to monitor my CPU (Intel Core Duo 1.60) with a percentage value instead of a graphical representation.  

I have seen the "CPU Frequency Scaling Monitor" but, this isn't a *load* monitor.  The "System Monitor" applet is graphical only and not what I'm after.  Anything out there with the function of the System Monitor but the looks of the CPU Frequency Scaling Monitor?

:popcorn:

---

### Post by blueridgedog on 2009-07-17
Take a look at conky.  I love it and you can make it anything you want.

[http://conky.sourceforge.net/](http://conky.sourceforge.net/)

The default conky config will give you what you want.

---

### Post by bug67 on 2009-07-17
I don't think Conky is quite what I'm looking for.  I want something that sits up in my top panel as an applet, not something that lives on my desktop.  Plus, when I installed it via Synaptic, I couldn't find it anywhere.  Thanks though.

---

### Post by Revolutionary101 on 2009-07-17
The CPU scaling monitor can show the CPU usage as a percentage. You just right click it then click Preferences then click Show as a percentage.

---

### Post by bug67 on 2009-07-17
> **Revolutionary101 said:**
> The CPU scaling monitor can show the CPU usage as a percentage. You just right click it then click Preferences then click Show as a percentage.

Yes, that's how I'm using it now but, is that showing actual CPU *usage* or a percentage of the frequency cycle?  I'm thinking the latter.

Either way, it only shows 50%...even at full idle.  When something more CPU intensive occurs, it spikes up to 100%.  Never anything lower than 50% and never anything between 50-100%.  Doesn't seem quite right to me somehow.  :confused:

---

### Post by devosion on 2009-07-17
Judging by the information you'd like to have displayed conky may be your best choice. You are able to directly monitor your cpu's load, average load, and a myriad of other choices via a config file. It also has an output for percentage. 

And you should be able to install conky from aptitude.

> 
sudo apt-get install conky


---

### Post by bug67 on 2009-07-17
OK.  So after I install Conky via synaptic or the terminal, how do I launch it?  I can't find it anywhere.  It's not in the "Applications" drop-down menu anywhere.

And no, I don't want it on my desktop anyhow.  I want something in my top panel like this:

[IMG]http://i103.photobucket.com/albums/m132/bug67/Miscellaneous/Screenshot.png[/IMG]

---

### Post by Newfoundlander on 2009-07-17
Right-click on the top panel, Add to Panel > System Monitor

Click on it to view your system, processes, resources, etc.

---

### Post by bug67 on 2009-07-17
> **Newfoundlander said:**
> Right-click on the top panel, Add to Panel > System Monitor

Click on it to view your system, processes, resources, etc.

Don't want to click on anything.  Don't want to have to look behind other open windows at something large and obtrusive on my desktop.  I just want to see my CPU usage at a glance.

I use mostly Macs at home and I have this cool little Ubuntu machine that I'm really, REALLY liking.  I've completely moved away from Windoze in my personal computing life.  On my Macs, I use a little app that sits up in the menu bar called iStat menu that does exactly what I want.  I guess there's nothing like that for Ubuntu?

---

### Post by blueridgedog on 2009-07-17
> **bug67 said:**
> OK.  So after I install Conky via synaptic or the terminal, how do I launch it? 


With the command:

```
conky 
```

in a terminal.

to start and then be able to close the terminal:

```
conky &
```

Most have it start as a gnome startup application.

---

### Post by mvelte54 on 2009-07-18
I am a n00be here also and I am trying to find an answer to my situation so please excuse me if I have posted in the wrong area.

I want to install a desktop weather app on my Jaunty Jackalope. I have used the synaptic package manager and installed gDesklets and all the recommended support apps. But when I go to Applications and try to open gDesklets I get an error stating:

Could not launch 'gDesklets'
Failed to execute child process
"gdesklets" (No such file or directory)

I have rebooted and still no change...
Any help would be greatly appreciated. :confused:

---

### Post by bug67 on 2009-07-18
Dewd, you hijacked my thread!  :P



Right click on one of the panels (top or bottom.  where ever you want to add the weather applet), Click on "Weather Report" to highlight it and then click "Add".

This puts the weather app in your panel not on your desktop.  For that, maybe gDesklets?  Applications > Add/Remove > gDesklets

**_EDIT_**:

I see you already tried gDesklets.  I got the same errors you did when I tried it as well.  Sorry, guess I just don't know.

---

### Post by Arup on 2009-07-18
sudo apt-get install lm-sensors hddtemp gkrellm

sudo sensors-detect and say yes to all, reboot and fire up gkrellm from system tools. You got visual CPU load monitor and other monitors.

---

### Post by bug67 on 2009-07-18
> **Arup said:**
> "...gkrellm..."

Yep, tried gkrellm.  Again, I would like something in the panel *not* on the desktop.  Thanks.

---

### Post by DeMus on 2009-07-18
> **bug67 said:**
> Yep, tried gkrellm.  Again, I would like something in the panel *not* on the desktop.  Thanks.

Install (from Synaptic) Hardware monitor, reboot and add Hardware monitor to the panel. You can choose for CPU monitor and with the preferences change from graphics to text. Have fun.

---

### Post by bug67 on 2009-07-18
> **DeMus said:**
> Install (from Synaptic) Hardware monitor, reboot and add Hardware monitor to the panel. You can choose for CPU monitor and with the preferences change from graphics to text. Have fun.

Thank you!  :D

*Exactly* what I was looking for.  :D

> **hijk448 said:**
> Mother: Freddie, why is your face so red? [wow gold kaufen](http://www.just4gold.com/wow-gold-kaufen.html)Freddie: I was running up the street to stop a fight. [eve isk](http://www.just4gold.com)Mother: That's a very nice thing to do. Who was fighting? [power led](http://ledtech-shop.de/LED-Spots-HighPower---9.html)Freddie: Me and Jackie Smith. [sciphone](http://www.yoocart.com/productHtml/Cool-cell-phone32_page1.html)[2moons dil](http://www.ebaymmo.com/game/2moons-dil.html)


Huh?  :confused:

---

### Post by DeMus on 2009-07-18
> **bug67 said:**
> Thank you!  :D

*Exactly* what I was looking for.  :D



I notice now that I also installed it that the values I see there are totally wrong. System monitor tells me I use 100% CPU, this new hardware monitor only shows between 5 and 20%. How could this be possible? See also attached screenshot.

---

### Post by mvelte54 on 2009-07-18
Wow you guys are awesome  but there's just one problem.
I installed it and rebooted and got it up and running but when I look for available apps I'm not finding a 'weather' app.

---

### Post by DeMus on 2009-07-18
> **mvelte54 said:**
> Wow you guys are awesome  but there's just one problem.
I installed it and rebooted and got it up and running but when I look for available apps I'm not finding a 'weather' app.

That's 100% correct. The program hardware monitor does what the name says: monitor the hardware.

---

### Post by bug67 on 2009-07-18
> **DeMus said:**
> I notice now that I also installed it that the values I see there are totally wrong. System monitor tells me I use 100% CPU, this new hardware monitor only shows between 5 and 20%. How could this be possible? See also attached screenshot.

Hmm.  Mine seems to be tracking fairly accurately.  There's a little lag between the two but not much:

[IMG]http://i103.photobucket.com/albums/m132/bug67/Miscellaneous/Screenshot-1.png[/IMG]

> **mvelte54 said:**
> Wow you guys are awesome  but there's just one problem.
I installed it and rebooted and got it up and running but when I look for available apps I'm not finding a 'weather' app.

For the "Weather" applet (and you really should've started you own thread for a completely different topic than that of the OP) right click on the panel, select "Add to panel," select "Weather Report," click "Add."

---

### Post by DeMus on 2009-07-18
> **bug67 said:**
> Hmm.  Mine seems to be tracking fairly accurately.  There's a little lag between the two but not much:

[IMG]http://i103.photobucket.com/albums/m132/bug67/Miscellaneous/Screenshot-1.png[/IMG]



How do you get the values of the two processor cores above each other? I only get one value. I did choose to show me all 4 cores. My value is still way too low. It should say something between 90 and 100% and the max. I have seen is 20%. What is wrong here?

---

### Post by mvelte54 on 2009-07-18
Well duh! I really feel like a n00bie now... I don't know what I did after looking at your thumbnail I noticed you had the weather on your bar so I thought, 'Hmmm what if I right click up here and see what comes up' I did and now I have weather however I'm still not clear if it is because of the gDesklets I installed or the gkrellm? Any help here please is greatly appreciated...  I too hope to be an Ubuntu master such as yourself however I realize I have a long ways to go though.

---

### Post by DeMus on 2009-07-18
> **mvelte54 said:**
> Well duh! I really feel like a n00bie now... I don't know what I did after looking at your thumbnail I noticed you had the weather on your bar so I thought, 'Hmmm what if I right click up here and see what comes up' I did and now I have weather however I'm still not clear if it is because of the gDesklets I installed or the gkrellm? Any help here please is greatly appreciated...  I too hope to be an Ubuntu master such as yourself however I realize I have a long ways to go though.

As the OP also stated please start your own thread. This is not about the weather applet, it is about the hardware monitor.
Just to inform you, the weather applet you see on my screendump is coming from the clock. Right-click on the clock and set your preferences.
Next time you have a problem please start a new thread with a catchy title so people will help you.
I am also just a Linux beginner, I also have to ask a lot here, but sometimes I can give the right answer to a problem I have had and managed to solve.

---

### Post by b.a.w on 2009-07-18
@DeMus 20% seems right for normal computer use. Are you compiling or something that would make it go to 100%? That is very heavy usage and rarely will you get 100% cpu usage unless it is something very intensive especially with your setup.

---

### Post by DeMus on 2009-07-18
> **b.a.w said:**
> @DeMus 20% seems right for normal computer use. Are you compiling or something that would make it go to 100%? That is very heavy usage and rarely will you get 100% cpu usage unless it is something very intensive especially with your setup.

When you look at my earlier post in this thread, the one with the screendump, you will that system monitor is at almost 100% for all 4 cores. I am using a program called Boinc which runs 24/7 on 100%. It's from the university of Berkeley in California where they have different projects which need computer power. So yes, my PC runs at 100% all the time.

---

### Post by bug67 on 2009-07-18
> **DeMus said:**
> How do you get the values of the two processor cores above each other? I only get one value. I did choose to show me all 4 cores. My value is still way too low. It should say something between 90 and 100% and the max. I have seen is 20%. What is wrong here?

Went into preferences and removed whatever the default device was and then added my processors.  Here's how I have mine set up:

[IMG]http://i103.photobucket.com/albums/m132/bug67/Miscellaneous/Screenshot-HardwareMonitorPreferenc.png[/IMG]

[IMG]http://i103.photobucket.com/albums/m132/bug67/Miscellaneous/Screenshot-HardwareMonitorPrefer-1.png[/IMG]

[IMG]http://i103.photobucket.com/albums/m132/bug67/Miscellaneous/Screenshot-ChooseaDevice.png[/IMG]

And then for the other processor I have everything the same except that last photo would be "Only CPU: 2".

So, in your case, with a quad, the first photo would have processor 1, 2, 3, 4 and then from the 3rd photo for each processor, "Only CPU: 1, 2, 3, 4."

I don't know how legible 4 processors stacked on top of each other is gonna be.  Try playing with the font settings and stuff?

---

### Post by DeMus on 2009-07-18
> **bug67 said:**
> Went into preferences and removed whatever the default device was and then added my processors.  Here's how I have mine set up:

[IMG]http://i103.photobucket.com/albums/m132/bug67/Miscellaneous/Screenshot-HardwareMonitorPreferenc.png[/IMG]

[IMG]http://i103.photobucket.com/albums/m132/bug67/Miscellaneous/Screenshot-HardwareMonitorPrefer-1.png[/IMG]

[IMG]http://i103.photobucket.com/albums/m132/bug67/Miscellaneous/Screenshot-ChooseaDevice.png[/IMG]

I see, you added a second line in the first window. Okay, I did that also and the text is out of reach when I want to show 4 cores. But that's okay. I found out I can not use the program. It will never show the 100%. Why not? Because (and I saw that while holding the mouse over the line where you can choose either all cores or just one. The little yellow "help-file" pops up and says: the percentage of time that is spent running foreground processes. My processes are not foreground processes so they are not included in the total score.
Well, okay, I know that now. I'm glad I could have helped you finding what you want. I will delete the program again. Have fun using Ubuntu.

---

### Post by blueridgedog on 2009-07-18
> **bug67 said:**
> Hmm.  Mine seems to be tracking fairly accurately. 

I have used that in the past, but find that the application itself causes some cpu load. I dropped it in favor of conky.

There are a few threads here where people were advised to remove it from the panel in order to solve video playback/performance issues.  However, if, like me, you have ample CPU capacity, you will not notice it.  My quadcore chip handled it well.

---

### Post by mjstelly on 2009-07-20
> **DeMus said:**
> Install (from Synaptic) Hardware monitor, reboot and add Hardware monitor to the panel. You can choose for CPU monitor and with the preferences change from graphics to text. Have fun.

You nailed. All my beans are belong to you!:popcorn:

---

