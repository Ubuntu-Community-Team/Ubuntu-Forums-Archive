---
title: "My External Drives Won't Show in VLC?"
date: 2009-07-23
forum: General Help
---

### Post by Anonymous Rain on 2009-07-23
Hey guys, can you help me out? When I select "open file" in VLC, it only recognises two locations to explore. As you can see however, I have two external hard drive, which is where I keep all my media. I would like to be able to explore these locations through VLC. Picture is related.
[[IMG]http://i137.photobucket.com/albums/q230/LukeNeoSkywalker/th_Screenshot.png[/IMG]]("http://i137.photobucket.com/albums/q230/LukeNeoSkywalker/Screenshot.png")

---

### Post by Anonymous Rain on 2009-07-23
Anyone?

---

### Post by michy99 on 2009-07-23
You should be able to find your disks under /media.

---

### Post by Anonymous Rain on 2009-07-23
> **michy99 said:**
> You should be able to find your disks under /media.

... Yes. Then you click "open file", and the drives don't show. Check my post again.

---

### Post by michy99 on 2009-07-23
What version of VLC are you using? My Open File dialog looks like this:

---

### Post by SonicSteve on 2009-07-23
So just to clarify you've clicked;
Computer
Filesystem
and then checked the /media folder? 

Normally you should have a folder for each drive in the /media folder.

---

### Post by SonicSteve on 2009-07-23
> **michy99 said:**
> What version of VLC are you using? My Open File dialog looks like this:

I'm using 9.9a and mine looks nothing like that when I click "media" then open file. I get a tabbed browser with 
File
Disc
Network
Capture device

Actually mine looks exactly like the one pictured in the first post. I would then click computer, then on the little drive icon in the right pane, which would then show me the root of the Ubuntu filesystem, where I would then click on media, and find my external drives. I think the reason that the external drives don't show up in the beginning of the dialogue box is that VLC doesn't have much Gnome integration function. IE. it doesn't really blend with it's operating system and things end up a bit more tricky then they ought to be.

---

### Post by michy99 on 2009-07-23
I assume you mean 0.9.9a. I am on 1.0.1-pre so that might explain the difference. Still, if you double click on the / it should put you in the main file system and then /media should show you your disks.

---

### Post by michy99 on 2009-07-23
What is under the Disc tab?

---

### Post by Anonymous Rain on 2009-07-23
> **SonicSteve said:**
> I'm using 9.9a and mine looks nothing like that when I click "media" then open file. I get a tabbed browser with 
File
Disc
Network
Capture device

Actually mine looks exactly like the one pictured in the first post. I would then click computer, then on the little drive icon in the right pane, which would then show me the root of the Ubuntu filesystem, where I would then click on media, and find my external drives. I think the reason that the external drives don't show up in the beginning of the dialogue box is that VLC doesn't have much Gnome integration function. IE. it doesn't really blend with it's operating system and things end up a bit more tricky then they ought to be.

Yeah that was it, I went to computer > / > media. Thanks.

---

### Post by RjNeLLY on 2010-01-23
hey guys! total noob here...just installed 9.10 and i also couldnt access my external hdd...i tried the my computer>file system> media  and its still not showing...is it different on karmic koala edition??or is there a software or driver that i need to install first???appreciate all the inputs...thanks

---

### Post by jamesisin on 2010-01-23
Anonymous Rain - Please mark the thread as SOLVED if that's true (under Thread Tools above).

RjNeLLY - What do you see under /media ?

ls /media

---

