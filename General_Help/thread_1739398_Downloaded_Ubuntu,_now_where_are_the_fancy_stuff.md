---
title: "Downloaded Ubuntu, now where are the fancy stuff?"
date: 2011-04-25
forum: General Help
---

### Post by Lanuk on 2011-04-25
Okay, so about a year back I saw my friend using Ubuntu (this is when I didn't even know what the heck it was), and he could make his windows wiggle around and switch workspaces with ease. It would minimize into a screen with a block that said: Ubuntu in the middle or something like that. The point is, it looked really cool. I just downloaded 10.10, and it obviously is much more boring than that. Sorry for being such a noob, but could someone please tell me how to do things like this?

---

### Post by tgm4883 on 2011-04-25
> **Lanuk said:**
> Okay, so about a year back I saw my friend using Ubuntu (this is when I didn't even know what the heck it was), and he could make his windows wiggle around and switch workspaces with ease. It would minimize into a screen with a block that said: Ubuntu in the middle or something like that. The point is, it looked really cool. I just downloaded 10.10, and it obviously is much more boring than that. Sorry for being such a noob, but could someone please tell me how to do things like this?

Go into System > Preferences > Appearance and select the Visual Effects tab then select Normal or Extra. If you want to dive in further, install compiz config setting manager.

---

### Post by matt_symes on 2011-04-25
Hi

Download compizconfig-settings-manager and enable compiz.

```
sudo apt-get install compizconfig-settings-manager
```

Start it by tying 

```
ccsm
```

or using the menu. You might also want to install the extra plugins.

Kind regards

---

### Post by Lanuk on 2011-04-25
> **tgm4883 said:**
> Go into System > Preferences > Appearance and select the Visual Effects tab then select Normal or Extra. If you want to dive in further, install compiz config setting manager.

Ahh, okay thanks. But what might this "compiz config setting manager" thing be and how would I go about downloading it? Sorry for all the trouble!

Haha, never mind, the guy that posted just before me answered that question. Thanks guys, case closed!

---

### Post by tgm4883 on 2011-04-25
> **Lanuk said:**
> Ahh, okay thanks. But what might this "compiz config setting manager" thing be and how would I go about downloading it? Sorry for all the trouble!

It basically lets you configure each part of compiz. The Normal and Extra settings are just preconfigured profiles for compiz. You would download it like any other package using apt-get, synaptic, or software centre. Package name is compizconfig-settings-manager

---

### Post by Lanuk on 2011-04-25
> **tgm4883 said:**
> It basically lets you configure each part of compiz. The Normal and Extra settings are just preconfigured profiles for compiz. You would download it like any other package using apt-get, synaptic, or software centre. Package name is compizconfig-settings-manager

Ahh I get it, thanks. I guess I closed this a bit too early, I hope I can fit in one more quick question! Is there an easier way to switch workspaces without having to drag the mouse to the bottom of the screen and click each box?

---

### Post by tgm4883 on 2011-04-25
> **Lanuk said:**
> Ahh I get it, thanks. I guess I closed this a bit too early, I hope I can fit in one more quick question! Is there an easier way to switch workspaces without having to drag the mouse to the bottom of the screen and click each box?

ctrl+alt+arrow (left or right, depending on which workspace you want)

---

### Post by matt_symes on 2011-04-25
Hi

Just for completeness, the extra plugins are in the package compiz-fusion-plugins-extra. A bit of extra eye candy

```
sudo apt-get install compiz-fusion-plugins-extra
```

Kind regards

---

### Post by Lanuk on 2011-04-25
> **matt_symes said:**
> Hi

Just for completeness, the extra plugins are in the package compiz-fusion-plugins-extra. A bit of extra eye candy

```
sudo apt-get install compiz-fusion-plugins-extra
```Kind regards

oo, thanks :)! Now how do I open these new functions :confused:

---

### Post by Quade97 on 2011-04-26
The manager itself is under System -> Preferences -> CompizConfig Settings Manager. Once you're in there you can start playing with all the settings :)

Sometimes it is kinda weird to find where apps get installed. If you can't find it you can always open the Ubuntu Software Center, Then search for the app and go to details, It'll show you where it ends up.

Just saying, I like wobbly windows :D

---

### Post by Lanuk on 2011-04-26
> **Quade97 said:**
> The manager itself is under System -> Preferences -> CompizConfig Settings Manager. Once you're in there you can start playing with all the settings :)

Sometimes it is kinda weird to find where apps get installed. If you can't find it you can always open the Ubuntu Software Center, Then search for the app and go to details, It'll show you where it ends up.

Just saying, I like wobbly windows :D

Ahh, thanks! And yes, the wobbly windows are awesome :3

---

### Post by Lanuk on 2011-04-26
Oh dear, I just deleted my bar at the bottom. How do I get this back!

---

### Post by Dutch70 on 2011-04-26
Edit: Go on to my next post.

You right click somewhere (top panel I think) and select "add panel" I'm not on Ubuntu right now though, so I can't remember exactly. 

I'm going to go login to it now though, I've got a link or 2 I think you'll like....brb.

---

### Post by Dutch70 on 2011-04-26
Ok, right click your top panel, select "new panel" where ever it puts it, right click it again and select properties. Click the orientation box to get it to the bottom if it's not already there. Right click it again and select "add to panel" to add the icons you want. It probably won't be long before you get rid of that panel anyway though.

Here is a link to help you get started with Compiz. I'ts kind of old and like I said, it's just a start, but should get you going pretty good....lol. Have fun.
[[COLOR="RoyalBlue"]http://forlong.blogage.de/entries/2008/4/26/How-to-set-up-Compiz-Fusion-074[/COLOR]]("http://forlong.blogage.de/entries/2008/4/26/How-to-set-up-Compiz-Fusion-074")

---

