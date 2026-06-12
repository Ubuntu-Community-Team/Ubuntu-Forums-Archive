---
title: "&quot;Open Containing Folder&quot; not working properly"
date: 2011-07-26
forum: General Help
---

### Post by Zhipp on 2011-07-26
I've been using Ubuntu and Linux Mint for a couple years now, but this is the first problem I've had that I wasn't able to find an answer for. I'm not even sure if this is the right forum for this question. :confused:
After I installed Audacious, for some reason when I tried to open the "C:" drive using the search, and when I tried to view a recently downloaded file in it's folder with Chrome or Firefox, it would just open Audacious(wouldn't even play anything). I removed Audacious, but it just opens Banshee now instead. Has anyone else had this problem? If so, what did you do to fix it?

One more thing, I'm not very familiar with the terminal,so you may have to hold my hand a bit.

---

### Post by Miljet on 2011-07-26
What kind of file are you trying to open? You should be able to right-click on the file and choose "Open with Other Application."

---

### Post by Zhipp on 2011-07-26
> **Miljet said:**
> What kind of file are you trying to open? You should be able to right-click on the file and choose "Open with Other Application."
It's not opening the files that's that 's the problem. It's specifically opening the folder containing the files. Sorry if I wasn't clear on that.

---

### Post by Miljet on 2011-07-26
So you can't even see the files?

---

### Post by Zhipp on 2011-07-26
> **Miljet said:**
> So you can't even see the files?
I can see the files fine if I manually navigate the the folder. You know in Firefox when you right click on one of your downloads, the option to "Open Containing Folder" will be on the drop down list. Clicking on it will open Banshee(or whatever music player I have installed) instead of actually taking me to the folder. It's not *that* big of a deal, but it's getting to be pretty annoying. It's not just Firefox either, all my web browsers do the same thing. 
It even happens with Wine when I'm trying to open the "C:" drive, so I have to manually navigate there as well.

---

### Post by mc4man on 2011-07-26
In a terminal copy and paste this in, press enter
Then post the contents of what shows up in gedit

```
gedit ~/.local/share/applications/mimeapps.list
```

What version of ubuntu are you using?

---

### Post by Zhipp on 2011-07-26
> **mc4man said:**
> In a terminal copy and paste this in, press enter
Then post the contents of what shows up in gedit

```
gedit ~/.local/share/applications/mimeapps.list
```What version of ubuntu are you using?
I'm using Natty, but with Gnome Shell instead of Unity.
You just solved my problem, though. Audacious/Banshee was set as the folder handler under [Added Associations], I changed that and now everything's back to normal. Thanks! :)

---

### Post by mc4man on 2011-07-26
If this happens again and or _If you have upgraded to 11.04 from 10.10 _then in the long run it may be better to delete ~/.local/share/applications/mimeapps.list and let a new one be written
11.04 uses 2 sections, Default and Added, 10.10 only the Added

To delete if need be 
```
nautilus ~/.local/share/applications/
```
ect.

---

### Post by Ross Gayler on 2011-10-20
Thanks mc4man!

> **mc4man said:**
> If this happens again and or _If you have upgraded to 11.04 from 10.10 _then in the long run it may be better to delete ~/.local/share/applications/mimeapps.list and let a new one be written.

That worked for me.  I had upgraded from 11.04 to 11.10 and Banshee started launching in contexts where I expected to see a folder.  The most annoying was in Firefox downloads - I would download something, the Firefox downloads list would pop up, I would attempt to "open containing folder" and Banshee would launch.  Really, really irritating.

I deleted  ~/.local/share/applications/mimeapps.list and the problem went away, although interestingly the system has not recreated a new copy of the file.  I presume that means that that information must live somewhere else in 11.10 but that  ~/.local/share/applications/mimeapps.list takes precedence.

---

### Post by rttm on 2012-01-21
This is how i fixed this issue

In a terminal copy and paste this in, press enter
Then post the contents of what shows up in gedit

Code:

sudo gedit ~/.local/share/applications/mimeapps.list

change 

change 
inode/directory=totem.desktop (this was what would open up)

to

inode/directory=nautilus.desktop

---

### Post by vboxu on 2012-02-09
This is what I did to get working open containing folder and opening already downloaded files from the firefox downloads window in ubuntu 11.10 (lubuntu).  I've been doing upgrades since 9.x, so I think that could have caused it to not work before.

vi ~/.local/share/applications/mime-dummy-handler.desktop
 
and put this in there

[Desktop Entry]
Type=Application
Name=Dummy URI Handler
Exec=/usr/bin/xdg-open %f
Terminal=false
StartupNotify=false
X-Ubuntu-Gettext-Domain=gdm

xdg-open will open the folder or file with whatever file manager (pcfman in my case) or app you have associated with that type of thing in gnome.  I'm not sure what one would do with kde, though.

I'm not sure if this will solve anybody else's problem, but I guess it's worth a try.

---

### Post by Noroprils on 2012-02-09
ïî÷òà ïî÷åìó ÿ íå ðîññèóñ õîðîõîðäèí ìîãó ëå÷ü ñïàòü ðàíüøå 2?!

---

