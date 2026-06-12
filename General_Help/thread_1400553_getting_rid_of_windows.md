---
title: "getting rid of windows"
date: 2010-02-07
forum: General Help
---

### Post by crlang13 on 2010-02-07
Hey,

I'm currently duel booting windows XP and ubuntu netbook remix.  I'm thinking of just getting rid of windows.  The only thing I use it for is to sync my ipod.  I haven't checked yet, but I assume there's some program I could use on ubuntu to sync with my ipod?  It seems silly to have a whole OS just for an ipod.

SECONDLY

My netbook is pretty much my primary computer I think I'd rather have to regular version of ubuntu rather than the netbook remix.  How would I go about doing this?  I've got the CD and all that of course.  Is there anyway of just updating the remix so I don't lose all my preferences, favourites, etc?  Or do I have to wipe everything and start again?

Thanks.

---

### Post by thecliff on 2010-02-07
I'm not sure about updating to the full version of Ubuntu from netbook remix, but I was able to install Kubuntu using just the Synaptic package manager in System > Administration > Synaptic Package Manger.  

It looks like this will work for you as well --  


[LIST]
[*]Open Synaptic and then search "ubuntu-desktop"
[*]Right-click and Mark for Installation
[*]Apply changes
[*]Log out and log back in
[/LIST]
**...as far as synching iPod in Linux:**

I have not been able to find a program that will sync my iPod Nano or my iPhone 3G.  :(  You can use [gtkPod]("http://www.gtkpod.org/") for synching other iPods (excluding Nano and Touch).

Best of luck.

---

### Post by Flying caveman on 2010-02-07
This might help. [http://www.liliputing.com/2009/02/how-to-quickly-switch-ubuntu-netbook-remix-interface-on-and-off.html](http://www.liliputing.com/2009/02/how-to-quickly-switch-ubuntu-netbook-remix-interface-on-and-off.html) or I'm pretty sure you can just install the regular desktop through synaptic. you won't lose any of your favorites, and you don't need to re-install the whole system.

I don't have an iPod, so i can't help you there.  Dare I say get a different mp3 player.

---

### Post by thecliff on 2010-02-07
> **Flying caveman said:**
> .  Dare I say get a different mp3 player.

Any recommendations for Linux-based/compatible phones/PDAs?

---

### Post by crlang13 on 2010-02-07
> **Flying caveman said:**
> 

I don't have an iPod, so i can't help you there.  Dare I say get a different mp3 player.

Thanks for that caveman, if you want to supply me with a new mp3 player, I'd appreciate it!;)

The package manager idea didn't work unfortunately...  So, I've just started again.  Have a little configuring to do, but it's ok.

Thanks for the ideas though!

---

### Post by willowave on 2010-02-07
I know this might be alot of work..and I don't have an iPod so I can't try it out...but what about installing Virtualbox and then installing Windows inside there? Then you can install your itunes in windows. I don't know if there would be any quirky things about connecting devices but from what I know about virtual machines I would think everything would work fine.

---

### Post by willowave on 2010-02-07
> **crlang13 said:**
> Hey,
 
 
SECONDLY
 
My netbook is pretty much my primary computer I think I'd rather have to regular version of ubuntu rather than the netbook remix. How would I go about doing this? I've got the CD and all that of course. Is there anyway of just updating the remix so I don't lose all my preferences, favourites, etc? Or do I have to wipe everything and start again?
 
Thanks.
 There is a way to install the regular desktop instead of the UNR desktop. There are several threads that explain how but one particularily good one. I just ran into the same issue trying to tweak the UNR desktop. I'll find it and stick it in a new post.

---

### Post by switch10 on 2010-02-07
If you have one of the older, ipods, not the Iphone/ipod touch/5th gen ipod nano/any of the newer ssd ipods, you will be fine.  I have an ipod video and it syncs great with both rythmbox or banshee, but you will need to install gtkpod from your package manager.  

I have an IPhone, and it is a pain.  You can jailbreak it and ssh songs to it wirelessly, but it does not work very well in my experience.  The only real good way to sync one of the new ipods, is virtualbox with windows installed.  Make sure you install the version from the virtualbox website, not the OSE version so you have USB support.

good luck

Dave

---

### Post by willowave on 2010-02-07
[http://ubuntuforums.org/showthread.php?t=1312335&highlight=unr+classic+desktop](http://ubuntuforums.org/showthread.php?t=1312335&highlight=unr+classic+desktop)
 
Here is the thread you want to look at. Pay attention to post 16 but make sure you read the whole thread as messing with the UNR desktop can be a pain. The first time I did it I ended up with NO desktop and had to reinstall my OS, but only because I didn't read the whole thing first and was impatient. lol If you want more threads like this do a search for UNR and gnome or classic desktop. There are alot of posts out there about it.

---

### Post by qwerty2009 on 2010-02-07
you could just remove the ubuntu-netbook-remix package from symnaptic and add the main menu and windows list to the panel and u will have the orriginal desktop:P

---

### Post by manzdagratiano on 2010-02-08
Doing a fresh install of ubuntu using a flash drive should work. You could save your preferences by copying the appropriate directories in /home - in fact, might as well copy the entire /home folder onto a flash drive and do a clean install, and then restore back the directories you want to retain.

My rhythmbox recognizes my Significant Other's ipod, so I see no reason why yours should not work. More and more players have become ipod compatible now - Songbird can handle that too except that it crashes for large libraries too often (I am talking > 200G here)

EDIT: I am not sure about removing the netbook remix package via synaptic and adding the main menu but you should certainly try that out first - solution is the last line of defence that I have oft employed to save my soul. And yes - getting rid of Windows is one of the most awesome steps ever! I did just that six months ago and I have not regretted it a single day!

---

### Post by crlang13 on 2010-02-08
> **qwerty2009 said:**
> you could just remove the ubuntu-netbook-remix package from symnaptic and add the main menu and windows list to the panel and u will have the orriginal desktop:P

Tried that, but I don't think I was quite savy enough to swap everything around - I think I missed a few remix packages so everything just went haywire.  I had already backed everything up so I ended up starting again.  It took me no time at all to get my preferences and all that back in order though (thank you back ups).

As for the virtual box, I may resort to that if need be, but my iPod is so archaic it sounds like it'll work.

---

