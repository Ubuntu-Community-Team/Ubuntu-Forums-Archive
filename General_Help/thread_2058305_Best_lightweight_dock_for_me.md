---
title: "Best lightweight dock for me?"
date: 2012-09-15
forum: General Help
---

### Post by fallenshadow on 2012-09-15
Hi all,

I am doing an experiment to create a Unity experience using just classic gnome and perhaps a dock/search tool too.

This is being done because Unity 2D doesn't feel quite lightweight enough for this little netbook.

So this dock will need to be the following:

- Lightweight
- Able to function vertically on the left
- Hold minimized windows
- Allow to quit an app by right clicking on the icon on the left
- Possibly have a built in search tool for launching apps

Any suggestions for something to fit what I need?

---

### Post by LewisTM on 2012-09-15
**Cairo-dock** is lightweight enough to run smoothly on my netbook.
It can sit anywhere, hold minimized windows and you can quit the app through a context menu or by middle-clicking it.
It doesn't have a built-in search tool but you can combine it with **Synapse** and invoke it with a shortcut or a launcher.

Cheers!

---

### Post by jaithehulk on 2012-09-15
Docky is another dock. It has all the functions you hav mentioned.

---

### Post by Frogs Hair on 2012-09-15
I used dockbarx with Gnome Classic because it is light. I have used GLX and Awn in the past also.   [http://www.noobslab.com/2011/08/dockbarx-046-released-for-ubuntulinux.html](http://www.noobslab.com/2011/08/dockbarx-046-released-for-ubuntulinux.html)

---

### Post by fallenshadow on 2012-09-15
Hmm... I was gonna try dockbarx but the PPA didn't seem to work.

I checked out Cairo-dock but that seems to use Open-GL. I should have mentioned that I don't want any hardware accelerated docks. :D

Now I think its either Docky or AWN.

According to this AWN is more lightweight but I think Docky looks nicer! 

[http://askubuntu.com/questions/40878/how-can-docky-awn-cairo-dock-and-unity-be-compared](http://askubuntu.com/questions/40878/how-can-docky-awn-cairo-dock-and-unity-be-compared)

Hmm... don't know how to make a decision on this. :lolflag:

---

### Post by LewisTM on 2012-09-15
When you install Cairo-dock, it adds two menu items. One for OpenGL mode and one for non-OpenGL. FYI the command for the latter is [FONT="Courier New"]cairo-dock -c[/FONT].

---

### Post by fallenshadow on 2012-09-15
Oh right... silly me! :D

At the moment I am testing AWN and I quite like it however is compositing required for all themes? Its gonna be uninstalled if I can't make it look nice!

Thanks for the tip on Synapse, that is a great launcher! However I tried to set the show key to the windows key (like Unity) but Synapse won't let me use that! o_O

---

### Post by PhilGil on 2012-09-15
> **fallenshadow said:**
> Hmm... I was gonna try dockbarx but the PPA didn't seem to work.

It's still available from the WebUpd8 ppa: [https://launchpad.net/~nilarimogard/+archive/webupd8](https://launchpad.net/~nilarimogard/+archive/webupd8)

I agree on dockbarx. Use the standalone (dockx) mode. You lose a few features (such as window previews) if you don't use a composited desktop, but it's lightweight and looks really nice.

---

### Post by fallenshadow on 2012-09-15
Cairo looked horrible without compositing so I turned compositing on! Then it completely froze. So I uninstalled it. 

Moved onto trying out Docky. Seems the best fit so far although im sure its using compositing which I dont like too much.

I now have a unity look-a-like desktop with pretty much the same functionality. Pretty cool! I should mention it doesn't use much resources either, which makes my netbook quite happy! :)

---

### Post by fallenshadow on 2012-09-15
Here is my finished result so far! :)

[IMG]http://ubuntuone.com/09WlpoXVhHNog2h7HBk7KH[/IMG]

Just getting Docky the way I want it to work... then im fully done on the matter! :)

---

### Post by Frogs Hair on 2012-09-15
when you installed dockbarx did you use the start command ? If not you may want remove the application. or check to see if it is still installed by doing the following.  ```
When installation finished (Press Alt+F2 and type: dockx) to start dock.
That's it.
```

---

### Post by fallenshadow on 2012-09-15
Wow the result is better than when I was using Docky today! :O
It doesn't overlap the top menubar now! Its also more lightweight!

Great suggestions people! Dockbarx and Synapse are great together!

One last question.. how do I know if Dockbarx is using compositing?

---

### Post by black veils on 2012-09-16
```
sudo apt-get install xfce4 synapse
```

you want the xfce desktop because it can be made to look like anything, yet it is lighter than unity or gnome. also if you want the side panel to look less plain, I made some panel backgrounds, search here [http://xfce-look.org/](http://xfce-look.org/)

as mentioned, synapse can be assigned to a  keyboard shortcut, and it will launch any apps etc, it also adjusts to your habits.

---

### Post by zombifier25 on 2012-09-16
Last time I checked Xfce doesn't have global menus or windows buttons in panel yet, while GNOME Classic got all of those covered :P

---

### Post by fallenshadow on 2012-09-17
Looks like im finally done! I have a gnome classic panel up top with the app menu indicator (global menu support) and the complete indicator for items on the right side.

Next I have installed maximus for apps to maximize when opened! (and without titlebar)

Lastly I am using Synapse for launching apps and Dockbarx for the sidepanel!

[IMG]http://ubuntuone.com/3MctlhN17u9AP3JsJtZrRf[/IMG]

Thanks for all the help people! :)

---

### Post by PhilGil on 2012-09-17
Looks nice; good Job.

---

### Post by GeForce 9500GT on 2012-09-17
> Hmm... I was gonna try dockbarx but the PPA didn't seem to work.
 
[This is the correct PPA]("https://launchpad.net/~dockbar-main/+archive/ppa") for Dockbarx. 
[Another link]("http://www.ubuntuupdates.org/ppa/webupd8").

---

