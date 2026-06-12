---
title: "Maveric GUI gone south"
date: 2010-11-30
forum: General Help
---

### Post by ventrical on 2010-11-30
I just updated MM. When it restarted I got double icons (network indicator) overlaying each other on the menu bar. I removed the icon indicator from the menu bar and now cannot get it back (or just don't know how to get it back). I tried startup apps .. etc...

Perhaps I am in wrong forum.

Anybody have similar experience?

thanks

---

### Post by lancest on 2010-11-30
Seen that many times.
Solved it though on my machines.

Using Compiz?
Put this in startup: 

Command:
compiz --replace --sm-disable --ignore-desktop-hints ccp --loose-binding --indirect-rendering

Make sure to enable Compiz as your Window manager in the Compiz setting manager too.

Problem solved.

My theory is that Compiz isn't perfected working with Gnome.
This isn't good for new users, so I hope for better Compiz development with Unity.


Forget to mention a right click/add to panel on the top will bring back any indicator you desire.

---

### Post by ventrical on 2010-11-30
> **lancest said:**
> Seen that many times.
Solved it though on my machines.

Using Compiz?
Put this in startup: 

Command:
compiz --replace --sm-disable --ignore-desktop-hints ccp --loose-binding --indirect-rendering

Make sure to enable Compiz as your Window manager in the Compiz setting manager too.

Problem solved.

My theory is that Compiz isn't perfected working with Gnome.
This isn't good for new users, so I hope for better Compiz development with Unity.


Forget to mention a right click/add to panel on the top will bring back any indicator you desire.

Thanks lancest but it didn't work . Perhaps I did not explain myself correctly or I did something wrong.
 At the top of the screen there is that long grey bar where all the little icons are. when I did an update yesterday on my SONYVAIO2.4GHZ there was a double indicator overlaying each other. It was the wireless indicator - the little wavy thingy that looks like a radio transmission. Anyways , to get rid of it I removed it from the panel , then, went into startup and tried to find the wavy thingy (wireless indicator) but it is not there in startup.

The wireless is working fine .. I just can't find the indicator .. etc..

 any other ideas or did I do something wrong with compiz? ie; "how do you enable compiz as your Windows manager??

 thanks  in advance.

 also I would like to hear your theory about updates for Maveric and Lucid. Somepeople are saying not to update but I sort of like the idea and so far -up to now- I have not had any problems with updates on Lucid, Maveric, Fedora 13, Lubuntu , Kubuntu.

 Your thoughts , welcome.

*ahh yes .. it is called "Network Manager" It is enabled in the startup but the icon will not come up on the menubar.

---

### Post by Decatf on 2010-11-30
Assuming your using the default applications (gnome-panel and network manager) then right click the panel and select Add to Panel. Then add the Notification Area applet.

---

### Post by WorMzy on 2010-11-30
Right-click on some empty space on a panel (the thing the indicators were on) and choose "Add to panel". In the box that pops up, look for "indicator applet", I *think* that's what you need, but I'm not 100% sure. Just double click the name or drag the name onto the panel.

If that's not what you removed, then try some of the other applets in the list, it will be one of them.

---

### Post by ventrical on 2010-11-30
> **Decatf said:**
> Assuming your using the default applications (gnome-panel and network manager) then right click the panel and select Add to Panel. Then add the Notification Area applet.

  Thanks decatf.  Thats it .. the NOTIFICATION AREA applet!!! That got the wavy wireless thingy back !! 

Super.

hehe .. In the process I messed something else up.. I think I did something with Dwell Click for the mouse because now when I hold my mouse over an item the arrow fills up with red and then executes  the icon that the mouse arrow is hovering over :)

  I think I know how to fix this. 

 Fun stuff!!:)

Really.

 Thanks you bunch of  geniuses.:)

---

