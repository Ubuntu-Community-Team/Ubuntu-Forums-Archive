---
title: "Change default media player?"
date: 2011-10-16
forum: General Help
---

### Post by TutenStain on 2011-10-16
Hello! Im using Ubuntu 11.10 and have installed Clementine which I want to have as a default media music player. I right click select properties -> Open with but Clementine ain't there. How do I add it and how do I make it the default music player on my Ubuntu with GNOME 3.

---

### Post by papibe on 2011-10-16
'Preferred Applications' works in 10.04. I wonder if it is still on 11.10.

Regards.

---

### Post by TutenStain on 2011-10-16
> **papibe said:**
> 'Preferred Applications' works in 10.04. I wonder if it is still on 11.10.

Regards.

It have been moved to System Info (no idea why?). Its says that Audio is handled by Clementine, but it does not work. If i open a mp3 it just takes me to Banshee.

---

### Post by meho_r on 2011-10-16
Apart from setting Clementine default player, did you try the old method: right click on an .mp3 file > Properties > Open With, and set Clementine there?

Another way might be to uninstall Banshee.

---

### Post by TutenStain on 2011-10-16
> **meho_r said:**
> Apart from setting Clementine default player, did you try the old method: right click on an .mp3 file > Properties > Open With, and set Clementine there?

Another way might be to uninstall Banshee.

Thats what I tried :P

The problem is that Clementine is not listed there. I can open the with Clementine via the right click -> open with Clementine, but thats not what I am after. I want it to open as default, if i dubbelclick on a file.

---

### Post by meho_r on 2011-10-16
But (provided you uninstalled Banshee), which one is default? All I did on my machine is to install Clementine, uninstall Banshee, then reboot.

---

### Post by Simeo on 2011-10-16
> **meho_r said:**
> But (provided you uninstalled Banshee), which one is default? All I did on my machine is to install Clementine, uninstall Banshee, then reboot.

That's what I did. I installed Clementine, changed preferred application in system info, uninstalled Banshee, and restarted.

---

### Post by TutenStain on 2011-10-17
> **Simeo said:**
> That's what I did. I installed Clementine, changed preferred application in system info, uninstalled Banshee, and restarted.

I have now removed Banshee and restarted. But its still my default player. When i try to open a music file it wont start because it cant find Banshee! What is this....drives my mad.

---

### Post by mc4man on 2011-10-17
I don't use clementine, actually can't with nvidia drivers - closing it causes 1 cpu to peg @ 100%

Anyway, like a good mystery - & as you've seen clementine will not show up on the right click > properties list, no matter what except..

Drove me crazy for a bit but the reason it's not showing is because the Exec=  in clementine.desktop just uses "clementine"
It needs a % <somethng> after it. 
The most logical choice would be to use %U so - 


```
gksudo gedit /usr/share/applications/clementine.desktop
```
Find the Exec= line & add a %U to end, leave a space after clementine as in 
```
Exec=clementine %U
```
Then maybe log out/in & it should start showing up, tested in unity, hopefully also works in GS

---

### Post by TutenStain on 2011-10-17
> **mc4man said:**
> I don't use clementine, actually can't with nvidia drivers - closing it causes 1 cpu to peg @ 100%

Anyway, like a good mystery - & as you've seen clementine will not show up on the right click > properties list, no matter what except..

Drove me crazy for a bit but the reason it's not showing is because the Exec=  in clementine.desktop just uses "clementine"
It needs a % <somethng> after it. 
The most logical choice would be to use %U so - 


```
gksudo gedit /usr/share/applications/clementine.desktop
```
Find the Exec= line & add a %U to end, leave a space after clementine as in 
```
Exec=clementine %U
```
Then maybe log out/in & it should start showing up, tested in unity, hopefully also works in GS

Thanks a bunch but sadly that does not work :(

And why the heck is Banshee still there when I have removed it from my system? Still no Clementine on the list.

---

### Post by mc4man on 2011-10-17
A bit surprised - works here, just tried on Gs - screen
Maybe try a restart?

---

### Post by TutenStain on 2011-10-17
> **mc4man said:**
> A bit surprised - works here, just tried on Gs - screen
Maybe try a restart?

Done twice.

It shows up in "System info" but not on right click. Still does not work. It just tries to open up Banshee.

---

### Post by mc4man on 2011-10-17
Edit: Forget system info - totally worthless - you need to set defaults on the files themselves, once per filetype

Well you can do the manual way - 
right click > properties >  open with on 1 example each of all your audio file types
Set a default to anything that's available, doesn't matter what you choose

After that - 
```
gedit ~/.local/share/applications/mimeapps.list
```

In the [Default Applications] section change all the audio lines to clementine.desktop from whatever you choose above - Ex. flac
```
audio/flac=clementine.desktop
```
Should only take you a few min. if that

(confirmed here on another app that would never show in properties - gdebi
gave it a %f & now it shows...

---

### Post by TutenStain on 2011-10-17
> **mc4man said:**
> Edit: Forget system info - totally worthless - you need to set defaults on the files themselves, once per filetype

Well you can do the manual way - 
right click > properties >  open with on 1 example each of all your audio file types
Set a default to anything that's available, doesn't matter what you choose

After that - 
```
gedit ~/.local/share/applications/mimeapps.list
```

In the [Default Applications] section change all the audio lines to clementine.desktop from whatever you choose above - Ex. flac
```
audio/flac=clementine.desktop
```
Should only take you a few min. if that

(confirmed here on another app that would never show in properties - gdebi
gave it a %f & now it shows...


Got it to work. Thanks :D

Hope this "bug" gets fixed.

---

### Post by Klondike on 2011-10-18
Feel moved to create a bug on Launchpad for it? I had the same problem. Editing clementine.desktop fixed it for me - thanks for the help, all.

---

