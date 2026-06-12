---
title: "Gnome Shell Becoming Processor Intensive -bug?"
date: 2011-10-28
forum: General Help
---

### Post by airspoon on 2011-10-28
Since installing 11.10, I have run into numerous problems, though as I tackle each one (with the help of this great community) I'm finding this version of Ubuntu better and better.

With that being said, I'm running into a major problem where gnome-shell becomes processor intensive and stays that way, even if I close all open programs. This is leading to my desktop being choppy and everything severely lagging. According to my Conky readout, Gnome-shell seems the be the culprit.

For instance, yesterday I had a lot of applications running and my processor was pretty active. It was causing some serious lag. So instead of restarting Gnome-shell, I decided to run a little experiment where I would close all running applications (browser, GIMP, Terminal, etc...) and see how long it takes for my machine to settle back down. 

I wound up going to bed, only to wake up this morning with my processor still going wild and Gnome-shell still having some serious lag, if not more. In fact, the lag was so bad that it was almost impossible to do anything.

A quick 'alt+F2-r' fixed the problem as expected.

Is this a known bug or something? I have searched for the problem, though I'm not sure exactly what is going on so I don't know exactly what to query.

Could the problem be with my video-card? I don't know why I'm thinking that it could be.

The only way that I'm able to over-come this problem is to 'alt+F2 -r' or log out and then log back in, which is becoming a hassle.

For whatever it's worth, I'm running 11.10 with Gnome-shell on a Gateway FX510x Core 2 Duo (E6600) 2.4 GHz, 4G RAM and a Nvidia GTX-7950 w/ 512mb.

Thanks for any and all help!

---

### Post by Bobhuber on 2011-10-28
Ok
If your gong to run Gnome 3 shell and  don"t want to have the ability of running Unity,2D or Gnome Classic.
BACK THE SYSTEM UP FIRST !!!
Proceed at your own risk.
Install Synaptic Package manager.
Remove all the packages that START with the word Unity EXCEPT the following.
unity-services
unity-assets
unity-greeter
unity-common
Do Not Remove Any of the libunity-- files or anything else associated with the word unity..
Optional (but will speed things up a bunch )> Remove Zeitgeist and associated files.
Install gnome-tweak and extensions
Disable auto-login (login manually)
Almost like buying a new computer for me and I use a high end system to start with.

---

### Post by airspoon on 2011-11-09
Thanks for the reply. 

However, When I go to mark those packages for removal, I get a dialog box that tells me it will remove other packages. The reoccurring package is Ubuntu-Desktop. I haven't yet started removing files because I wasn't sure if that's safe to remove.

Should I just assume that its okay to remove those 'required' packages as well, which don't have Unity in the name?

Thanks.

---

### Post by cbowman57 on 2011-11-09
Yeah, if you remove ubuntu-desktop it's going to take most of Unity with it.

---

### Post by airspoon on 2011-11-09
Thanks for the quick reply. So, it's okay to remove it if I'm using Gnome shell, right?

---

### Post by cbowman57 on 2011-11-09
Well I took a look in synaptic, and it might take out a bunch of other apps that you want, but I'm pretty sure you can add them back, or unselect them in synaptic.

---

### Post by ndaneau on 2011-11-15
Hi,

I'm facing the same problem and have to restart gnome-shell (alt-F2 -> r ) 2 or 3 times a day.
did the uninstall of ubuntu-desktop solved the issue?

Thanks,

---

### Post by Bobhuber on 2011-11-15
> **ndaneau said:**
> Hi,

I'm facing the same problem and have to restart gnome-shell (alt-F2 -> r ) 2 or 3 times a day.
did the uninstall of ubuntu-desktop solved the issue?

Thanks,
Realy need to know what your hardware is but it won't hurt anything if done correctly.

I'm running gnome3. 

No Unity
No Ubuntu-Desktop
No Zeitgeist
Compiz removed (not used in Gnome3)
Gnome-Tweak installed with all of the extensions (not all activated but all functional)
Custom themes along with Cairo-Dock and some Screenlets
The desktop is extremely stable and I have had no problem with updates.

Things I've found Not To Do.

Do not use the rictotz/testing  PPA for gnome3 (use the web8 PPA)
Do not use gnome3-team/gnome3 PPA (very unstable and tends to break other things associated with video)

---

### Post by ndaneau on 2011-11-16
Hi,

Sorry, did the post too quickly... ;)
Hardware :
[INDENT]Motherboard : Intel DH67BL
Proc : Intel i3-2100
Ram : 4Gb
SSD : OCZ agility3 60Gb
Integrated graphic card[/INDENT]
Ubuntu 11.10 x64

I don't use processor intensive task: most of the time Firefox + Chromium + banshee + AWN.
I just switch from unity to gnome shell about 1 week ago and didn't had the problem under unity. Now after a few time (let say 3-4 hours) even scrolling a simple webpage become slow. After a gnome-shell restart everything is fine again for a few times.
I checked cpu activity and gnome shell was taking about 93% of one cpu core.

Nico

---

### Post by Bobhuber on 2011-11-16
> **ndaneau said:**
> Hi,

Sorry, did the post too quickly... ;)
Hardware :[INDENT]Motherboard : Intel DH67BL
Proc : Intel i3-2100
Ram : 4Gb
SSD : OCZ agility3 60Gb
Integrated graphic card[/INDENT]Ubuntu 11.10 x64

I don't use processor intensive task: most of the time Firefox + Chromium + banshee + AWN.
I just switch from unity to gnome shell about 1 week ago and didn't had the problem under unity. Now after a few time (let say 3-4 hours) even scrolling a simple webpage become slow. After a gnome-shell restart everything is fine again for a few times.
I checked cpu activity and gnome shell was taking about 93% of one cpu core.

Nico
Thats a fairly high end MB but I'm not familiar with the intel graphics or drivers. If you have a backup and aren't worried about screwing something up try offloading everything not needed for your gnome3 environment.If the problem persists the first thing I would look at would be the graphics especially since you are using the integrated  graphics. I would also recommend you use the latest JRE Java version (Sun) and the most recent version of Flash . Instructions to load Java  found here > 
[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java) 
You can use the Flash aid plugin if needed in Firefox for that update.
Hope some of this helps.

---

### Post by Lord_JABA on 2012-03-22
Same here. gnome shell eats 100% cpu after some time and stays that way till I reset it - very annoying.
my hardware 
i3 2100
4GB ram
geforce440GT.
Can it be caused by shell extension? I have few installed.
Any idea how to debug the problem?
I understand that removing unity isn't helping?
EDIT:
please submit to this bug at launchpad- let developers know that it affects you:
[Gnome-shell high CPU load](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/880374)

---

