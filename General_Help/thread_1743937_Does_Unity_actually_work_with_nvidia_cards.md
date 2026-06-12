---
title: "Does Unity actually work with nvidia cards?"
date: 2011-04-29
forum: General Help
---

### Post by jnthornh on 2011-04-29
Did an upgrade to Natty - on first boot, when I log in, it tells me I don't have the hardware to run Unity (not likely - it's an NVidia GTX460, not even a year old). I assume it's a driver problem, so I install the restricted NVidia binary drivers through jockey. That's the ubuntu way, I figure, let it do its thing.

So with those enabled, I have 3d acceleration (hi, World of Warcraft!) but still no Unity. I blow away .gconf* and .gnome* (as I'm used to doing whenever something gnome-related goes wonky which, in Ubuntu, seems to be every single Ubuntu release) and absolutely no love. I log in and again, it tells me I don't have the hardware. I scoff at this dialog box as I fire up WoW and frag some orcs in glorious 3d. No, Mr. Dialog box, you're a filthy liar.

So tell me, how do I coax Unity into running on this thing? Or does it just... not? Switching to Nouveau isn't an option, as I need my games (and anyway, I don't think it was even in use originally).

---

### Post by jnthornh on 2011-04-29
Oh hey, forgot to mention, I can actually enable compiz manually (even though I guess all the GUI options for it are absent) by running compiz --replace. And I can configure crap using ccsm.

So what's up with this janky unity stuff, anyway? Where's it getting the crazy idea that my hardware sucks?

---

### Post by caecusum on 2011-04-29
I had this problem, too, and don't know what caused it. I resolved it by uninstalling the binary drivers, rebooting, and reinstalling the binary drivers.

---

### Post by wojox on 2011-04-29
Did you try this and reboot:

```
sudo nvidia-xconfig
```

---

### Post by jnthornh on 2011-04-29
> **wojox said:**
> Did you try this and reboot:

```
sudo nvidia-xconfig
```

Yes, and the nvidia binary drivers are in use, hence having usable 3d acceleration in WoW and other games.

I mean, it's not a huge deal, I guess a lot of people hate Unity anyway and would've been immensely thankful had it never actually worked for them. I just kind of wish it actually worked so I could judge it for myself.

---

### Post by prshah on 2011-04-30
> **jnthornh said:**
> I don't have the hardware to run Unity (not likely - it's an NVidia GTX460, not even a year old). I assume it's a driver problem, so I install the restricted NVidia binary drivers through jockey. 

I suggest you install Unity2D (it's in the repos - No OpenGL unity), then disable Unity (Uses OpenGL) and re-enable it.

---

### Post by jnthornh on 2011-04-30
> **caecusum said:**
> I had this problem, too, and don't know what caused it. I resolved it by uninstalling the binary drivers, rebooting, and reinstalling the binary drivers.

You know, I have absolutely no idea why, but after doing this it randomly started working. Thanks for the hint.

---

### Post by auwally on 2011-04-30
I had problems after upgrading to 11.04 - all blank screens  except in safe mode.  Checked drivers and uploaded nvidia accelerated  graphics driver (version 173).  Went to system - administration -  additional drivers.  No problems now all screens up and running.

---

### Post by damnhappy on 2011-05-07
I had problems with Unity working with my Nvidia card, and what worked for me was installing the Unity-2d, logging in with that, rebooting then logging in with the default Unity and it worked fine. Thanks for the tip!

Edit: whoops! I guess I am still in unity 2d even though I log into the default, which I thought was unity 3d; so the problem not fixed for me. I have the latest Nvidia 270.41.06 installed with a geforce go 7400 gpu on a Dell XPS M1210 notebook.

---

### Post by ffeingol on 2011-05-07
I had a similar issue.  I disabled version in 'additional drivers' and just installed the latest from the Nvidia site.  All is good now.

---

### Post by Frogs Hair on 2011-05-07
No problem with 270.41.06 recommended driver installed via additional drivers.

---

### Post by spikoley on 2011-05-07
There is a [bug report]("https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/771788") on this issue.

---

### Post by NewAuthority on 2011-05-07
Hey relatively new ubuntu user here. Not sure where to put this question
I also am having resolution issues when booting into 11.4 and I cant even try to resolve it using unity, so I was able to figure out that I could boot into ubuntu classic (which i kinda considered a small victory ;) )

I was able to set up 10.10 with my laptop the week it came out, with an external monitor hooked up into it.
I have since built a new computer and that is what the external monitor is now being used for.  But for some reason my workspaces still think I am hooked up to one, and I can not figure out why.

The laptop is a Dell XPS 1550
and the video card is an Nvidia 8600M GT

---

