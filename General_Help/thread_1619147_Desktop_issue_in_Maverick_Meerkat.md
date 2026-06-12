---
title: "Desktop issue in Maverick Meerkat"
date: 2010-11-11
forum: General Help
---

### Post by Nautron on 2010-11-11
Well, this is my first post here. I'm a relatively good troubleshooter, and I've been running Linux for a while now, and I can usually use my good friend Google and some intuition to solve most problems, but I haven't really seen anybody with my specific problem, only similar ones, and seeing as I previously bricked an ancient computer (completely by my own actions) playing around with Ubuntu, I want to make sure I get this right.

I'm dual booting Windows and Maverick, and I've been doing so rather peacefully since the release, but now (after installing Mugen64plus and XWii, and trying to get my display to HDMI out to my TV unsuccessfully, and trying to apply an Emerald theme while using Compiz) I can't do anything with my desktop. No effects from compiz work anymore, not wobbly windows, not opening and closing animations, no desktop cube, no ring switcher, nothing. On top of that, I can't interact with the actual desktop in any way, I can't right click, nor can I highlight, and even when I add folders to the actual desktop folder, they don't show up on the "home screen" as some like to call it.

I know it's probably a problem with the config files, but I don't quite know which ones and I don't know if I should delete them, rename them, create new ones or what. Also, if you know the source of the problem, lemme know for future reference so I don't mess it up again.

tl;dr Desktop is unresponsive to clicking, rest of programs work fine, compiz effects enabled but not working, need help.

---

### Post by realzippy on 2010-11-11
Welcome to UF!
Which graphics card/driver do you use?

Does it run when disabling compiz or emerald?

Deleting the config files or reinstalling compiz/emerald might be worth a test;they will recreate themselves to vanilla.

---

### Post by Nautron on 2010-11-11
Right, that might be important.

I've got an NVIDIA GTX285M, and I just checked the available drivers, and they were updated today, so I've got an outdated driver. I'm at school right now though, so I'll have to update the drivers when I get home, and see if that fixes the issue.

I tried clicking on System>Preferences>Windows (I believe... Either windows or monitor or something of that sort) and it gave an error message and wouldn't open.

And I think it's worth noting that Compiz worked to perfection before this problem, and I was never actually able to apply the emerald theme, I tried clicking on the tropical theme and when I did, nothing happened. I tried clicking save theme, thinking I might be able to apply it from the default Ubuntu themes editor, and then when I went to right click on the desktop, this is when I discovered the issue, which is why I think it's a .conf issue. That being said, I'm not positive that's exactly when the issue arose, as I don't use my desktop all that often, but I'm positive it happened after I installed all those programs I previously stated.

---

### Post by realzippy on 2010-11-11
You have a link to that failing emerald theme?

---

### Post by Nautron on 2010-11-11
Well it was just the first theme that comes preloaded with emerald, like when you click on the compiz icon and then click on emerald themes, it opens a two tabbed window with pictures of themes, and for some reason none of them would apply.

---

### Post by realzippy on 2010-11-11
Have you set ccsm to emerald?

---

### Post by Nautron on 2010-11-11
Never mind! Thank you so much for your help, but I figured it out myself.

If anybody else thinks they have a similar problem as me, I'll let you know how I fixed it.

Well the issue arose from me trying to HDMI out to my TV, I created a new desktop for my TV using System>Administration>NVIDIA X Server Settings, then I saved the xorg.conf file. That was the issue. So I went back into the Server Settings, removed the secondary desktop, and saved the xorg.conf file again, and rebooted, lo and behold, things are working perfectly now!!!


So if you lost access to your desktop or window effects after plugging in an external monitor, this is how you can fix it :KS

---

