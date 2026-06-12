---
title: "save me!"
date: 2009-08-30
forum: General Help
---

### Post by wisal on 2009-08-30
[COLOR=Blue][B][I]Hi guys
OK this is the first time I am hear and on populously I came hear to learn little bit about ubuntu!
this is my story.. please read this until finish and give me a help to get rid of this
I have HP pavilion dv 6000 laptop. few months ago I was very satisfied with windows OS.
but then I wanted to learn how to hack into my neighborer's wire less network. so I start to Google. but when I found this materials concerning hacking thing I also learn If I am going to do this hacking thing first of all I need to learn Linux. then I got this Linux CD. but after I install ubuntu I found far more advantages in it more than windows!!
So finally I am not interested in hacking any more. What I want now is learn ubuntu!
but meanwhile I learnt my laptop is not fully functioning with ubuntu OS. 
So Is there any one  to tell how to find all the drivers for my laptop
Actually still I even don't know whether the problem is in drivers. but I will tell you 
I can't work with some things like skype( I think my camera and Mic is not installed yet) I tried to fin drivers but couldn't also I have some problems with archive some softwares I downloaded cant install It says a problem with a archive manager
So guys please HELP ME!
Thank you in advance
:confused:[/I][/B][/COLOR]

---

### Post by RabbitWho on 2009-08-30
This is unrelated to your question but that laptop is running a faulty nVidia graphics card and you need to install a BIOS update if you haven't already. 

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01087277&lc=en&cc=us](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01087277&lc=en&cc=us)


I already know someone with one of these which just completely stopped working. If you Google it you will find millions of people with your laptop and this problem. The components of the card melt when it overheats. It is absolutely imperative that you stop your laptop from overheating and all the bios update does is keep the fan running all the time. You should get a cooling mat (a tray for laptops with a fan built into it) and don't run it for too long. 

The bios update is free from HP and will prolong the use of your computer, it has nothing to do with your OS and you can still go to ubuntu.

---

### Post by wisal on 2009-08-31
> **RabbitWho said:**
> This is unrelated to your question but that laptop is running a faulty nVidia graphics card and you need to install a BIOS update if you haven't already. 

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01087277&lc=en&cc=us](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01087277&lc=en&cc=us)


I already know someone with one of these which just completely stopped working. If you Google it you will find millions of people with your laptop and this problem. The components of the card melt when it overheats. It is absolutely imperative that you stop your laptop from overheating and all the bios update does is keep the fan running all the time. You should get a cooling mat (a tray for laptops with a fan built into it) and don't run it for too long. 

The bios update is free from HP and will prolong the use of your computer, it has nothing to do with your OS and you can still go to ubuntu.
[COLOR=Blue]***Thanks man! but did you see they do not have any update for ubuntu users!***[/COLOR]

---

### Post by holycow131415 on 2009-08-31
lspci
 
will show you your devices

---

### Post by stderr on 2009-08-31
You'll likely have to use the command mentioned by holycow above to discover information about your hardware devices and go about finding the relevant drivers individually. HP is unlikely to supply a Linux driver bundle for your laptop.

Googling the device name with "ubuntu" on the end should help if you're really stuck.

You may well need more information than lspci gives my default, so use

```
lspci -v
```

Regarding software installation, always try to install from repositories when possible before resorting to downloading things manually from the web and installing by hand. When you do it manually, they won't automatically update, and you'll likely wind up having trouble keeping track of versions. See [Ubuntu Help on Repositories]("https://help.ubuntu.com/community/Repositories/Ubuntu")

BTW, it may be a good idea to remove the additional information from your first post regarding your neighbour's network...

---

### Post by AlexanderDGreat on 2009-08-31
Did you say HP dv6000 series laptops?

Check this out:

[http://aldeby.org/blog/index.php/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops](http://aldeby.org/blog/index.php/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops)

Mine is HP dv2000 series.

Hope to help.

---

