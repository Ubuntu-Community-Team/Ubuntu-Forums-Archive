---
title: "Should I Upgrade to Breezy and Will It Correct MY Screen Resolution Problem?"
date: 2006-02-19
forum: General Help
---

### Post by lakelovers on 2006-02-19
I'm finding that I love Ubuntu except for one thing: My screen resolution is stuck on 640X480, and I've tried everything I can find on how to correct it. Nothing works. I'm running 5.04. So, I'm wondering if I upgrade to Breezy will it recognize my screen better than 5.04. I've been around Linux for a long time but I'm new to Ubuntu and I'm clueless most of the time. What I'm afraid of is that in the process of upgrading I'll screw something up and lose verything. I've read some of the upgrade how-to's and it seems a bit complicated to me. I'm open to all suggestions. By the way my monitor is an Envision EN-710e, and the graphics card is an integrated, Intel 3D AGP Graphics.

---

### Post by bluevoodoo1 on 2006-02-19
Why not try a Breezy Live CD and see if that helps recognize your monitor (or at least, give you a more suitable resolution) ??

---

### Post by Strev_123 on 2006-02-19
I use Breezy and have an integrated Intel 82810 AGP chipset, It has worked correctly right 'out of the box', gives any resolution my monitor can take with minimum of, or no fuss. I can only assume yours will be the same... but I'm not really sure without knowing the model of your chipset tho, probably be best to try the live cd as 'blue' said above.

---

### Post by evilgold on 2006-02-19
You could probably correct your resoultion problem by editing /etc/X11/xorg.conf and adding the resoultions that you want to use.

---

### Post by lakelovers on 2006-02-19
I'm downloading Breezy live right now. I've tried repeated configurations of /etc/X11/xorg.conf, and so far nothing has worked. I've also tried sudo dpkg-reconfigure /etc/X11/xorg.conf, I've changed the default color dept, I've tried different drivers. The monitor specs call for vesa but is compatilable with other drivers which I have tried. The only other Linux OS, I've used is various versions of Mandrake including Mandriva 2006 and they  have all recognized my monitor and graphics card. My monitor and graphics card are pretty plain vanilla. I'm surprized that I'm having so much trouble with it. I don't have any specs on the Intel 3D AGP Graphics card so I don't know what chip set I'm dealing with. I've tried looking it up on Google but there are some many cards of that general description that I've not be able to zero in on this one.

---

### Post by dcstar on 2006-02-20
[QUOTE=lakelovers]I'm downloading Breezy live right now. I've tried repeated configurations of /etc/X11/xorg.conf, and so far nothing has worked. I've also tried sudo dpkg-reconfigure /etc/X11/xorg.conf, I've changed the default color dept, I've tried different drivers. The monitor specs call for vesa but is compatilable with other drivers which I have tried. The only other Linux OS, I've used is various versions of Mandrake including Mandriva 2006 and they  have all recognized my monitor and graphics card. My monitor and graphics card are pretty plain vanilla. I'm surprized that I'm having so much trouble with it. I don't have any specs on the Intel 3D AGP Graphics card so I don't know what chip set I'm dealing with. I've tried looking it up on Google but there are some many cards of that general description that I've not be able to zero in on this one.[/QUOTE]
lshw will show you what hardware Ubuntu detects.

---

### Post by lakelovers on 2006-02-20
I just tried Breezy Live, and it detected my monitor and graphis card fine. It looks great. Interestingly it detected all the screen resolutions but one (1024x768). That's okay, I can add that or do without. Don't really need it.

That means I'll upgrade to Breezy. My next question is would it be better to make a fresh install of Breezy or do an upgrade. I don't have many files in 5.04; not much to reload into Breezy. What's your thoughts? As I mentioned I'm a little uneasy with an upgrade. It seems if I don't do everything just right I may have a problem.

---

### Post by Kagey on 2006-02-20
in your xorg.conf, if you do not have the correct horizontal and verticle sync ranges the available resolutions will be limited. Look up the horz and vert sync rates in your monitor's specs and change the xorg.conf and see if that helps.

---

### Post by lakelovers on 2006-02-20
I do have the vertical and horizontal refresh rates set according to my monitor specs. One question I have is should those entries by in quotes (" x ")? I copied the form from "FixSreenResolutionsHow-to" and refresh rates were not in quotes. I inserted my correct refresh rates but xorg would not load. I put the rates in quotes and it worked, however, I made another change so I'm not sure whether the quotes were correct. The other thing is should entries be in lower case, uppercase or does it make a difference? For, instance my monitor specs call for "VESA," but that didn't work. I made it "vesa" and xorg loaded. I guess I'm answering my own question but it seems that case makes a difference.

---

### Post by lakelovers on 2006-02-20
Thanks, David,
I ran lshw as you suggested. This item shows up. Does this mean it does not see my monitor? What does "UNCLAIMED" mean?
l
*-display UNCLAIMED
             physical id: 2
             bus info: pci@00:02.0
             version: 01
             size: 128MB
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: irq=5

---

### Post by cotcot on 2006-02-20
I suggest to clone your hoary (see partimage which is an open source alternative to Ghost) to a backup device before you upgrade your hoary.
You can partimage to CDs or DVDs too. 
You can also backup your home files and do a fresh install of breezy. At that moment you could use automatix (there is no risk as it is a fresh install.

---

### Post by lakelovers on 2006-02-21
CotCot. . .

Well, I did a fresh install of Breezy before I read your post. It looks terrific. I have a couple of issues with updated files that don't want to load and I've posted a new post to that affect. No response, yet. I'm trying to download Quanta through Synapatic, and it doesn't want to load. Maybe I have to have Kubuntu setup, although Quanta loaded in Hoary. Thanks for your help and suggestion.

---

