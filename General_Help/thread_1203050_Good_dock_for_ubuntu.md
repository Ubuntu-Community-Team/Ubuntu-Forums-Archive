---
title: "Good dock for ubuntu?"
date: 2009-07-02
forum: General Help
---

### Post by Cam42 on 2009-07-02
I installed the Mac4Lin theme, and I'm looking for a dock application. What options are available? also, I'm trying to find a mac theme for firefox that'll work in Linux

---

### Post by internalkernel on 2009-07-02
I liked AWN - Avant Window Navigator for my dock... seems to have quite a bit of community support going for it right now. Doesn't it come with Mac4Lin? It seemed to be a default setting when I installed it on my girl's computer... 

As far as Firefox... I usually just install the gnome support packages for my version of Firefox and Xulrunner - seems to fit seemlessly into my current theme that way...

---

### Post by ~sHyLoCk~ on 2009-07-02
I use both cairo dock and awn..

Might seem a bit messy though:
[[img]http://omploader.org/tMXd3Mg[/img]](http://omploader.org/vMXd3Mg)

---

### Post by fabounet on 2009-07-03
Cairo-Dock is the one you want for a Mac theme ;-)

---

### Post by Jose Catre-Vandis on 2009-07-03
wbar

nice and easy does it :)

---

### Post by credobyte on 2009-07-03
Awn ;)

---

### Post by Cam42 on 2009-07-03
The problem,and I should've mentioned earlier, is that Compiz does not work on my computer

---

### Post by fabounet on 2009-07-04
Cairo-Dock can work with fake transparency, but try to activate transparency with Metacity or xcmpmgr before

---

### Post by TeoBigusGeekus on 2009-07-04
gnome-do eliminated all the other docks IMO.

---

### Post by fabounet on 2009-07-04
Gnome-Do is a nice file/app finder, but a very poor dock IMHO ^_^

it's a non-sense to build a dock on Gnome-Do, better would be to build an interface (using DBus for instance) and let other docks/panels integrate it through an applet.
This way, everybody could have the best of the two worlds.

---

### Post by Tipped OuT on 2009-07-04
If you want a nice dock, with nice i-candy, that simply works. Then use AWN (Avant Window Manager).

Cairo Dock doesn't work too well with ATI cards and is some what buggy.

GNOME-DO is not even an actual dock, it just has an option to make it look like a dock. It's in fact more of a search tool.


Click on the thumbnail below to see how AWN looks.

[[IMG]http://img199.imageshack.us/img199/6112/screenshotscp.th.png[/IMG]](http://img199.imageshack.us/i/screenshotscp.png/)

It's fully customizable, that's just a my own little custom theme, to match my current GTK theme.

---

### Post by fabounet on 2009-07-04
I must say that Cairo-Dock works perfectly with ATI cards, except if you launch it with the openGL (at the moment).
so launch it with the command "cairo-dock -c" or just from the App menu.

as usual, try and see, it's your desktop after all ;-)

---

### Post by Genius314 on 2009-07-04
If you're going for a true Mac experience, use Awn... it's so much less customizable! :p

I like Cairo-Dock better just because it can do more. Awn can't even change what side of the screen it's on. Awn does look a lot cleaner by default, though.

...Although I'm still forced to use at least one panel, until a dock can integrate the notification icons into it, and actually make them look nice.

---

### Post by michaelzap on 2009-07-04
Gnome Do's "Docky" interface is by far the nicest dock that I know of (and in addition you get all the other Gnome Do benefits).

---

### Post by TeoBigusGeekus on 2009-07-04
> **michaelzap said:**
> Gnome Do's "Docky" interface is by far the nicest dock that I know of (and in addition you get all the other Gnome Do benefits).
+1
And after the recent update (0.8.2) and the addition of intellihide and docklets, gnome-do just does the job.

---

### Post by Cam42 on 2009-07-04
okay, how do I get docky? I've installed Do, but I can't find any option for a dock.

---

### Post by earthpigg on 2009-07-04
> **Cam42 said:**
> okay, how do I get docky? I've installed Do, but I can't find any option for a dock.

open the gnome-do preferences (super+space by default, then start typing 'preferences'

appearance -> docky

then quit gnome-do (start typing 'quit')

restart it (it lives in applications -> accessories)

and start dragging/dropping things into it

---

### Post by michaelzap on 2009-07-04
You probably want to get the latest version from their PPA:
[http://do.davebsd.com/download.shtml](http://do.davebsd.com/download.shtml)

---

### Post by Cam42 on 2009-07-04
It tells me that I don't have compositing. I'm assuming that's compiz? it doesn't work with my graphics card.

---

### Post by michaelzap on 2009-07-04
> **Cam42 said:**
> It tells me that I don't have compositing. I'm assuming that's compiz? it doesn't work with my graphics card.

I don't think that you need to run Compiz to have compositing. You can enable it in Metacity, and I think there are other packages that will do this for you as well. Check out this link:
[http://tombuntu.com/index.php/2008/03/31/enable-metacity-compositing-in-gnome-222/](http://tombuntu.com/index.php/2008/03/31/enable-metacity-compositing-in-gnome-222/)

---

### Post by Cam42 on 2009-07-04
Sweet! that worked! thanks!

---

### Post by earthpigg on 2009-07-04
wow, i didn't know about metacity and compositing.

imo, that definately needs to be an option under system -> preferences -> appearance -> visual effects:

```

none
basic <-- the new entry
normal
extra

```

---

### Post by earthpigg on 2009-07-04
> **Cam42 said:**
> Sweet! that worked! thanks!

i reported the fact that you needed to jump through hoops in order to enable compositing as a bug, and linked it to this thread:

[https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/395641](https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/395641)

in my opinion, the attached is what you _**should**_ have had to do.

[ATTACH]119978[/ATTACH]

---

### Post by Cam42 on 2009-07-04
What GNOME theme are you using?

---

### Post by earthpigg on 2009-07-04
> **Cam42 said:**
> What GNOME theme are you using?

emerald theme manager with compiz

the emerald theme is called "Adonis_Mod"

---

