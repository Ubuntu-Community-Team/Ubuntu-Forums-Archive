---
title: "Undo a custom command for media insersion"
date: 2010-09-07
forum: General Help
---

### Post by jrd on 2010-09-07
Hey, I made a custom command to run when a cd gets mounted but now I need to change it.....how do I do that? I tried going to file management but the option wasn't there. I'm using 10.10 btw..

Thanks

---

### Post by jrd on 2010-09-07
Bump

---

### Post by mc4man on 2010-09-07
If you want to change to something else then insert a cd and hold down the shift button for a bit - you may get a pop up

If you wish to edit the Exec= then go to ~/.local/share/applications, find the userapp.desktop for this action and open it in a text editor

The userapp will be in the form of something like this, X are #'s or letters
userapp-<1st.word of com.>-XXXXXX.desktop

---

### Post by jrd on 2010-09-07
Thanks for your help. I think it may be a issue with docky somehow...I have everything set to open banshee when a cd is inserted (and it does) but if I click on the cd icon (for a mounted cd) in docky I get an error saying it cant find sound-juicer. I uninstalled sound-juicer a while back. Every setting I can find is set to banshee including config files. If I enable showing of mounted drives on the desktop and click it everything does fine, but if I click on the one on docky I get an error saying it cant find sound-juicer. 


Thanks for your help.

---

### Post by mc4man on 2010-09-07
> I think it may be a issue with docky somehow
It certainly is - unless that 'mounter' can be reconfigured then it's coded to only use sound-juicer on audio cd's
(seems a bit worthless if it can't be configured, also sound-juicer may or may not even work in 10.10...


edit:
(you could 'hack' around that by creating a link in /usr/bin or /usr/local/bin named sound-juicer that linked to whatever would  cause the intended result
probably a link to a script would work best or just a script named sound-juicer instead of a link - a trial and error deal

---

### Post by jrd on 2010-09-07
> **mc4man said:**
>  also sound-juicer may or may not even work in 10.10...

It works but I got rid of it because I use banshee to rip my cd's. I hate having duplicate apps.
> **mc4man said:**
> 
edit:
(you could 'hack' around that by creating a link in /usr/bin or /usr/local/bin named sound-juicer that linked to whatever would  cause the intended result
probably a link to a script would work best or just a script named sound-juicer instead of a link - a trial and error deal

This is what I ended up doing right after my last post. It works but I just wish I could reconfigure the mounter thing like you said. Oh well.

I'll mark this as solved even though it is a hack fix :)


Thanks for you help

---

### Post by mc4man on 2010-09-07
> (you could 'hack' around that by creating a link ...
Quite easy if you work out what you want.

Ex.
I wanted the icon to autostart and autoplay an audio cd from any of my drives (2 internal, 1 external) with pana (amarok 1.4 clone

I use a ~/bin ( bin folder in home dir.

i simply put this little script in ~/bin and named it sound-juicer
Now the docky audio cd icon starts up pana and it autoplays the cd.

```

#!/bin/bash
CD=/dev/`echo $1|sed -e "s/.*\(sr[0-9]\).*/\\1/"`
pana --cdplay //$CD
```

You could pretty much set anything to happen from the icon..

Edit: was posting  - didn't see your last post

---

### Post by mc4man on 2010-09-07
> I just wish I could reconfigure the mounter thing
just as followup  - 
It appears docky may just do (use) the same as the audio cd icon you'll see in Places which has been tied to sound-juicer for some time.

Why it hasn't been changed in 10.10 is not clear, maybe that's just what gnome uses.

So you'll notice whatever you 'adjusted' sound-juicer to do will also now occur from the icon in Places.

---

### Post by jrd on 2010-09-07
I just confirmed what you said.....you are exactly right. So basically gnome expects sound-juicer to always be installed, that's silly. So in the end it's not an issue with Docky but with Gnome. Oh well, my little hack will have to do I guess. lol

---

### Post by mc4man on 2010-09-28
don't now if it will make any difference but did locate where sound-juicer is defined for the places -> audio cd icon
Look in gconf-editor -> Desktop -> gnome -> uri handlers -> cdda

(may not be much different than diverting "sound-juicer"

---

### Post by jrd on 2010-09-28
> **mc4man said:**
> don't now if it will make any difference but did locate where sound-juicer is defined for the places -> audio cd icon
Look in gconf-editor -> Desktop -> gnome -> uri handlers -> cdda

(may not be much different than diverting "sound-juicer"


This is what I was looking for! Thank you. Now I can undo my hack.

---

