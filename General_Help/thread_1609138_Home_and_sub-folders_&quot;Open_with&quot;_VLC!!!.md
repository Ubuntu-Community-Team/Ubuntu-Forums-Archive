---
title: "Home and sub-folders &quot;Open with&quot; VLC!!!??"
date: 2010-10-30
forum: General Help
---

### Post by Wolfie Lee on 2010-10-30
This is a truly STRANGE problem. My dad took some video he wanted me to convert to a DVD ISO so he could burn it. They are .mov files. I'm not sure it has anything to do with the problem or not, but this started happening when I transferred the first .mov file from the DVD he gave me to the "videos" folder. I first opened it with VLC before the transfer to be sure it could handle the codec. It played, but roughly (most likely because, to use an optical drive in my sisters Dell Optiplex GX280, I'm using an old raid card [@ ATA100] to replace the ONLY IDE connector on the MB, which had burned out). I shut VLC down and went ahead with the file transfer. The next time I tried to open the Home folder with the Quick launch on the panel, instead of opening a file browser, it tried to open it with VLC. So I clicked Places>Home with the same results. All of the sub folders (Desktop, Documents, Music, Pictures, Videos and Downloads) were similarly affected, and the ONLY way to get to an actual File browser in those folders is to Open "Computer" and "File System", then go from there. I have restarted the Computer several times, and the problem persists. I figured that would clear the glitch, the first time, but, no such luck. And some "unknown program" is always running and I have to "Shut down anyway" to shut down since this has happened. Also, VLC opens in administrative mode when I click any file I have set to be associated with it.


W   T   F   !?!?!?!?????????

---

### Post by mc4man on 2010-10-30
> W T F !?!?!?!?????????

Simply an ignored bug in 10.10 and 10.04 

One way to fix (there are several ways

r.click on any folder you can find -> Open With -> Other Application
scroll down and pick 'Open Folder' -> open

This will return the default folder handler back to nautilus.
(if no folders around on desktop then just create one to use w/ r. click -> Create Folder

If curious bug report - [a bit of a joke]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/603833")

and way to [minimise this happening ]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/662194") - could use confirming, though probably won't matter

(I've re-built nautilus here so I don't need to uncheck the box when using 'other application' dialogue - works fine

---

### Post by Wolfie Lee on 2010-10-30
Thanks, got it changed back, and thanks for the extra info...:P

---

### Post by jivana on 2011-03-23
Had the same problem under 10.10 today, thanks for your tip!

---

