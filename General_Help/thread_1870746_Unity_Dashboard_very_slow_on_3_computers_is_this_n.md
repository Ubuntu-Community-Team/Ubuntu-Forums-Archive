---
title: "Unity Dashboard very slow on 3 computers?? is this normal?"
date: 2011-10-27
forum: General Help
---

### Post by ingramproductions on 2011-10-27
I've installed Ubuntu 11.10 on 3 different computers now, and on every single one of them, the Unity dashboard has been terribly slow. If I hit the super key or click on the icon for the dash, I wait 3 to 5 seconds and then it opens.

I'm just wondering if this is a widespread problem, or if i just picked systems that don't work with Unity very well?

How's the dashboard for you guys?

---

### Post by M!K3_$ on 2011-10-28
What are some of your specs? The slowest computer I'm using is running a single core mobile processor with 1GB of RAM and it runs unity "ok". On my dual core it runs flawlessly (4GB RAM).

---

### Post by ingramproductions on 2011-10-28
One of them was a Dell Optiplex 330 with 2GB ram. Another was a Fujitsu TX100 S1 w 4GB ram. The other was an asus board (not sure which model) with 4 GB of ram.
Basically a variety of systems, but the Unity dashboard ran slow on all of them.
Does anybody else have this problem? I'm not talking about a slight delay opening up the dashboard... I'm talking 2,3, or 5 seconds later it opens

---

### Post by Dustintendo on 2011-10-28
i had this on my p4 3.2 with 2gb ram with unity 2d. unity 2d on natty was usually fast

---

### Post by 3rdalbum on 2011-10-28
What's your graphics card, and what driver are you using for it? The dash should open pretty much instantly.

Are you using Unity 3D or 2D? (in Unity 3D, when the Launcher bar is full of icons, those at the bottom will tilt and look like they are "stacked". In Unity 2D the icon at the bottom looks like it's partly faded)

If you're using Unity 3D, hit Alt-F2 and type "about:config", then click on the first item that comes up in the search. Click the Experimental tab and set the Dash Blur to "Static Blur". Does this help?

---

### Post by ingramproductions on 2011-10-28
Not really sure if it was Unity 3d or 2d. Whatever the default is for 11.10. It looked just like this:

[http://www.vodeblog.com/wp-content/uploads/2011/10/downloadubuntu1110.png]("http://www.vodeblog.com/wp-content/uploads/2011/10/downloadubuntu1110.png")

The asus board had a nvidia something with 1GB of ram built in and it was using the drivers installed through Additional Drivers. The other two systems just used the onboard video adapters.

The Dell and Asus systems, I installed Ubuntu 10.10 on them because of this issue and they work great. They both have effects enabled as well, like wobbly windows

---

### Post by Strike0 on 2011-11-20
Hi, no help, but I searched and feel its a good place to add my dash problem, since it seems related. 
I upgraded from 10.10 -> 11.04 and now 11.10. Also here no hardware issue, plenty of power. 

We have a number of users on the PC. For the users upgraded: If you click dash, the menu appears - but clicking "applications" yields no result. After about 20 seconds, the little "documents" icon on the bottom of the menu appears (it is not there at the beginning). 

Then and just then I can click onto the main buttons at the top (apps, ...). This is pretty annoying since the wait will happen over and over again. 

However, I added a new user and with that one it is not the case, i.e. the menu is there instantly. 

So it must be something to do with one of the upgrades I suppose. I cannot tell about 11.04 really, since I upgraded in a double leap from the splendid Maverick. 

I tried 3rdalbums hint, but the about:config wont start when I click it. 

Any ideas how I can troubleshoot that?

---

### Post by m.kristian on 2011-11-21
> **3rdalbum said:**
> 
If you're using Unity 3D, hit Alt-F2 and type "about:config", then click on the first item that comes up in the search. Click the Experimental tab and set the Dash Blur to "Static Blur". Does this help?

cool - finally some tweak which really helped me - thanx

---

### Post by thordom on 2012-04-18
I also have this issue with the Unity Dashboard being slow when trying to search for things, you start typing and then it 'pauses'.

So I just logged in to a Guest session and Unity is lightning fast!!!

How do I find out if this performance issue is related to files or bookmarks? (I do have allot of both)

Thanks

---

### Post by titaniumbones on 2012-05-28
I'd also like to figure out whether my unity dash slowness comes from some user settings, or cruft in a database somewhere that I could possibly clean up.  Any hints?  Thanks, Matt

---

### Post by NoBugs! on 2012-08-03
Same here, on 2gb-RAM, 2.4ghz dual core laptop. It shouldn't ever be taking 30 seconds to open the dash, or 10 seconds or so to Alt-tab switch, when using Ubuntu 2D!

---

