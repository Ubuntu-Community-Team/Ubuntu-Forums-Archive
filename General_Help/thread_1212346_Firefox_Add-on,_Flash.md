---
title: "Firefox Add-on, Flash"
date: 2009-07-13
forum: General Help
---

### Post by VipX1 on 2009-07-13
[SIZE=3][FONT=Arial]Firefox add-on *Foxtab* is not doing anything when I hit it's little shortcut button on the toolbar. I get the blank backround but I don't get the tabs or the Web pages.
Has anybody had experience of this?
The Foxtab add-on works with Flash!
[/FONT][/SIZE]

---

### Post by VipX1 on 2009-07-13
I might also add to this that none of the other functions work on the Foxtab page that opens. It's locked my Firefox page until I click on another page tab at the top, on the toolbar. I've got in on Firefox on my PC in work and works fine but that's a different OS. It is this stupid OS that my employer had to pay for?? And all the software for this OS has a Licence, stuff keeps expriring, like food!! Very strange..
This fault is on my laptop DELL M1330 with Ubuntu 9.04 Jaunty. The work PC is listed below..

---

### Post by y-lee on 2009-07-13
That is one add on I haven't tried, it however looks very interesting. Anyway what version of Firefox are you using? And I am assuming your problem with the add on is on a ubuntu machine, what version of ubuntu? And do you have Firefoxs flash plugin installed? If so what version? (type **about[noparse]:p[/noparse]lugins** in the address bar to see plugin information)

I have no idea what is causing the problem but if you open a terminal and then type **Firefox** in at the command prompt and when FF opens try the Foxtab addon, you hopefully will get some error messages which might shed some light on the problem. Copy and paste whatever messages you get in the terminal here when you try that.

---

### Post by VipX1 on 2009-07-14
Thanks for the reply Lee. I ticked the notify box so it would tell me if someone posted on this post... but it didn't, hmm?? Anyhow.. Ubuntu 9.04 on my M1330 DELL.
I'm not sure if I have the Flash Plugin installed but that's first thing I'll check this evening when I go home and then I'll start Fierfox from the terminal to check for add-on erros.. 
I'll post how I get on...

---

### Post by VipX1 on 2009-07-14
None of that works. I don't get any errors either which way.. I've got Adobe Flash Movie and Flashsplash Movie plugins. The rest look like codecs or print plugins...

---

### Post by y-lee on 2009-07-14
Ok Try creating [a new profile ]("http://kb.mozillazine.org/Profile_Manager#Linux")and then install the addon, restart firefox in the new profile and see if the new profile has the same problem.

---

### Post by VipX1 on 2009-07-14
What do mean by new profile? NEW USER

---

### Post by y-lee on 2009-07-14
> **VipX1 said:**
> What do mean by new profile? NEW USER

yes create a new user for firefox, in a terminal type

```
firefox -P
```

and create a new profile. the reason for this is to see if anything in your current FF profile is causing the problem. Sometimes addon conflicts or corrupt data makes FF or its addons not function correctly.

---

### Post by VipX1 on 2009-07-14
I found the link... I ran Firefox with a new profile and it's the same unfortunately. It does the very same thing in every respect.

---

### Post by y-lee on 2009-07-14
Are you using the most recent version of Foxtabs.

> FoxTab 1.1.2 has few issues with some Linux distributions which affect certain users.
All the problems you had regarding FoxTab display panel were addressed in the new version which you can download from:
[https://addons.mozilla.org/en-US/firefox/addons/versions/8879#version-1.2](https://addons.mozilla.org/en-US/firefox/addons/versions/8879#version-1.2)

[The FoxTab Team]("https://addons.mozilla.org/en-US/firefox/reviews/display/8879?show=20&page=5")



---

### Post by VipX1 on 2009-07-15
No Joy. I got the most recent version (1.2) and it still doesn't work. It something stupid, a wrong setting or a application extension missing.. but which one??

---

### Post by VipX1 on 2009-07-17
I have more info to add:
I was trying the Web [speedtest]("http://www.speedtest.net"), which works fine on my Ubuntu 9.04 desktop. On my laptop I don't get the little speed-dial at the bottom of the picture. I get the frame of the dial but none of the moving bits in the middle!
I'm quessing that the Foxtab problem and the graphic not working on the speedtest page are the same problem. 
Is it the Java runtime environment that creates those graphics?
What piece of software isn't working? :confused:

---

### Post by y-lee on 2009-07-17
> **VipX1 said:**
> None of that works. I don't get any errors either which way.. I've got Adobe Flash Movie and Flashsplash Movie plugins. The rest look like codecs or print plugins...

you should have 

[INDENT][SIZE="3"][B]Shockwave Flash
[/B][/SIZE]
    [INDENT]File name: libflashplayer.so
    Shockwave Flash 10.0 r22[/INDENT][/INDENT]

> **VipX1 said:**
> I have more info to add:
I was trying the Web [speedtest]("http://www.speedtest.net"), which works fine on my Ubuntu 9.04 desktop. On my laptop I don't get the little speed-dial at the bottom of the picture. I get the frame of the dial but none of the moving bits in the middle!
I'm quessing that the Foxtab problem and the graphic not working on the speedtest page are the same problem. 
Is it the Java runtime environment that creates those graphics?
What piece of software isn't working? :confused:

Both the Foxtab addon and the speedtest web site require adobe flash, so it is my quess that flash is not installed on your system or you are using  Swfdec, the GNOME version of the flash player, or the GNU SWF player. However when i try either of these flash alternatives both the Foxtab addon and the speedtest web site say i need to install adobe flash. Whatever i still feel something is wrong with your flash addon.

So first can you play you tube videos in firefox?

And two, type **about[noparse]:p[/noparse]lugins** in the address bar to see plugin information again and then copy and paste all that info here please.

Three if no flash plugin shows up in this list at all and you are sure of it then open a terminal and type :

```
sudo apt-get install flashplugin-installer
```

You may have to restart firefox after this.

---

### Post by VipX1 on 2009-07-17
Thanks for hanging in there Y-Lee..
Yep, Youtube works fine.
I can see a few refrences to *Flash* in about:plugins
**Shockwave Flash**
application/x-shockwave-flash - Adobe falsh movie
application/futuresplash - Futuresplash movie
**VLC Multimedia Plugin**
video/flv - Flash video

There all enabled (yes). I've only one that isn't enabled but it doesn't refer to Flash.. (File name:  libnullplugin.so [Enabled: No ]). All the rest of the plugins are codecs by the look of them and one or two printing plugins.. That's it!

I prefer aptitude as apose to apt-get.. so do think I should--```
sudo aptitude install flashplugin-installer
```

---

### Post by VipX1 on 2009-07-17
:p swfdec-gnome _wasn't_ installed but his buddy swfdec-mozilla was installed. I installed -gnome and restarted firefox but it didn't solve anything. I thought that was it for a second but no Joy!

---

### Post by VipX1 on 2009-07-17
Adobe Falsh Player 10.0.22.87 installed

---

### Post by y-lee on 2009-07-17
> **VipX1 said:**
> :p swfdec-gnome _wasn't_ installed but his buddy swfdec-mozilla was installed. I installed -gnome and restarted firefox but it didn't solve anything. I thought that was it for a second but no Joy!


Ok Uninstall both **swfdec-gnome** as well as **swfdec-mozilla**, you don't need them. Now *Shockwave Flash* is the one you need, so it seems to be installed so after you uninstall the two above, start or restart FF and see if it is working? Does you-tube videos still play, does the speedtest web site now work and lastly did this help the addon? If no to any and or all of these try uninstalling flashplugin-installer and then reinstalling it.

> **VipX1 said:**
> I prefer aptitude as apose to apt-get

Understandable, use whatever you wish to uninstall and or install :)

---

### Post by VipX1 on 2009-07-17
:DFair Plat Y-Lee that's it....
I uninstalled those two fellas in Synaptic and restarted Firefox and tried Foxtab and it worked perfect.....\\:D/
**Thanks** for help, Cheers!

---

### Post by VipX1 on 2009-07-17
That's suppose to be "Fair Play" not "Plat" I was a bit excited...
Thanks again Y-Lee..

---

### Post by y-lee on 2009-07-17
> **VipX1 said:**
> :DFair Plat Y-Lee that's it....
I uninstalled those two fellas in Synaptic and restarted Firefox and tried Foxtab and it worked perfect.....\\:D/
**Thanks** for help, Cheers!

\\:D/ fantastic. What happened was you had more than one plugin to handle flash and for whatever reason the foxtab addon crashed or something. Good luck.

And Btw I had never used that add on before but working on this lead to me installing it. Pretty neat add on i think :)

---

