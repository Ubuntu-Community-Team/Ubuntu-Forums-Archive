---
title: "NCAA live games for free - can't watch it linux..."
date: 2006-03-17
forum: General Help
---

### Post by KCMiller3 on 2006-03-17
I am able to watch other videos but not the live NCAA games.  I am using the embedded mplayer plugin in Mozilla.  here is the site: 

[http://www.ncaasports.com/mmod/welcome](http://www.ncaasports.com/mmod/welcome)
(its free but you have to get a free login account)

Please help!

~Kevin

---

### Post by thelazzyone on 2006-03-17
That is strange because it works for me and I using the mplayer plugin.

---

### Post by bjweeks on 2006-03-17
It looks like it is useing WMV and you can't play this with out installing win32codecs(which is illegal)/

---

### Post by AndrewCaul on 2006-03-17
So you can't legally watch WMV videos in Linux?

---

### Post by Jason_25 on 2006-03-17
Not legal in the U.S. because of licensing/DMCA.  Bill gates will not be coming to knock down your door though, if you use it.

---

### Post by pataphysician on 2006-03-17
[QUOTE=AndrewCaul]So you can't legally watch WMA videos in Linux?[/QUOTE]

it depends on where you live. i have no idea where it's legal and where it's not. it's pretty grey all over and, really, who cares? The Feds aren't going to kick down your door for installing some codecs. check here for instructions on how to get various media formats working:

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by bjweeks on 2006-03-17
[QUOTE=AndrewCaul]So you can't legally watch WMA videos in Linux?[/QUOTE]

No, Microsoft has the pantent on WMV...

---

### Post by abstracthumor on 2007-03-16
The codecs didn't solve the problem that I was experiencing as well.  I've still got a black screen and no indication as to the problem other than that.  The only other thing I could think of to help assess the situation is that I only have one video controlling button available and it changes from a pause button to a stop button.

Suggestions?

---

### Post by drpaul on 2007-03-16
I think your problem may be in the FF plugin. I have 2 installations: Dapper where I removed totem and installed mplayer and Edgy where I have left totem as the default.

The Dapper plays the video and the Edgy doesn't.

HTH

Paul

---

### Post by nelio2k on 2007-03-16
Once you've installed the WMPlugins, make sure other players' plugins are disabled. One way that I did it to get Mplayer to work with my firefox is to uninstall all other plugins.

Go to System ->Admin->Synaptic Package Manager
Search for Mozilla and make sure the totem player plugins for mozilla and other plugins are removed. 

Try watching March Madness again after that.

Good luck!



UCLA FIGHT FIGHT FIGHT! :)

---

### Post by drFUNK on 2007-03-16
> **drpaul said:**
> I think your problem may be in the FF plugin. I have 2 installations: Dapper where I removed totem and installed mplayer and Edgy where I have left totem as the default.

The Dapper plays the video and the Edgy doesn't.

HTH

Paul

Thanks!
\\:D/ Now back to the games.

---

### Post by gnychis on 2008-03-22
I'm also getting a black screen, I tried to follow everyones suggestions

I uninstalled totem, the mozilla totem plugin, and I installed mplayer, the mplayer mozilla plugin, and then install w32codecs from medibuntu.  But, I still get the black screen.  I restarted firefox, of course.

I'd greatly appreciate any help.

Thanks!
George

---

### Post by gnychis on 2008-03-23
quick bump before the games today

---

### Post by gnychis on 2008-03-24
bump

---

### Post by gnychis on 2008-03-24
yessss, i got it

i uninstalled the mplayer plug in, and installed the totem-mozilla package... is this the same as the xine plugin? regardless, it works now!

the only thing that doesn't work is that I don't see all of the video controls, only the stop button

---

