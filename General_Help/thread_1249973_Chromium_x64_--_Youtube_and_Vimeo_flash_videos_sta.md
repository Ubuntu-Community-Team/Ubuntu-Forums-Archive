---
title: "Chromium x64 -- Youtube and Vimeo flash videos stalling on latest alphas?"
date: 2009-08-26
forum: General Help
---

### Post by martini1179 on 2009-08-26
During the last few days, when running Chromium I've noticed that Youtube and Vimeo videos will stop playing after several seconds, sometimes after more than a minute. This had happened with both the 32 bit and 64 bit flash players. Anyone else having this problem? Anyone have a workaround, or do we have to play wait-and-see? 

I'm running Chromium 4.0.230.0 build 24230.

---

### Post by mybunche on 2009-08-26
Running the same build (24230), and happens to me too. 
And some links I have to click on twice, elso Resolving host... is constantly displayed.
And, with the GTK them set, the non-active tabs are blue. Doesn't look good with the brown theme. :(
The previous two builds I didn't have these issues.

---

### Post by themtx on 2009-08-26
Ditto.  I installed chromium from PPA just yesterday, linked libflashplayer.so, ran w/--enable-plugins, and all was fine.  Then later in the day ran an update and it was borked.

---

### Post by martini1179 on 2009-08-26
Well, Youtube and Vimeo videos seem to work again, albeit with the usual bugs that have been cropping up lately.

---

### Post by mybunche on 2009-08-28
Now running 4.0.204.0 Ubuntu build 24607 and videos all working fine. Very nice.

Does anyone know that with this build that it's possible to use the bookmark sync feature? How do you add it?

---

### Post by martini1179 on 2009-08-28
> **mybunche said:**
> Now running 4.0.204.0 Ubuntu build 24607 and videos all working fine. Very nice.

Does anyone know that with this build that it's possible to use the bookmark sync feature? How do you add it?

I could be wrong, but I think that's only currently going on in the Windows beta of Chrome, not Chromium. Still, it doesn't hurt to try with a new Chromium build once in a while. Type add " --enable-extensions" (with a space between the application name and the string, but without the commas) to your shortcut. I had tried it last night and it didn't work. Get the very latest build first.

---

### Post by mybunche on 2009-08-29
Thanks martini1179.

The latest build, 24734, fixed up some things that i wanted, so just in case I'll wait a little longer until they introduce the bookmark syncing feature.

This is getting better each day. 

Still can't view attached thumbnails on these forums yet, the page goes black.

---

### Post by martini1179 on 2009-08-29
> **mybunche said:**
> Thanks martini1179.

The latest build, 24734, fixed up some things that i wanted, so just in case I'll wait a little longer until they introduce the bookmark syncing feature.

This is getting better each day. 

I know what you mean about things better better and better with Chromium. A month or so ago, Flash still didn't work without crashing every 5 minutes, having an open Gmail tab would prevent other tabs from loading, etc. I was frustrated because Firefox was also crashing on me on a daily basis.  

Fast-forward a month, and Flash works well, Gmail is problem-free, and there are almost no crashes. I'm actually excited about using Chromium as my daily browser and watching it mature week by week.

---

### Post by marc66thomas on 2009-09-11
Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.1.2) Gecko/20090803 Ubuntu/9.04 (jaunty) Shiretoko/3.5.2

Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.0.14) Gecko/2009090217 Ubuntu/9.04 (jaunty) Firefox/3.0.14

Is this the build (Vimeo problem here too) but same in 3.0 & 3.5 on 64 bit

---

### Post by martini1179 on 2009-09-11
I currently have: 

Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.1.2) Gecko/20090803 Ubuntu/9.04 (jaunty) Shiretoko/3.5.2

Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.0.14) Gecko/2009090217 Ubuntu/9.04 (jaunty) Firefox/3.0.14

but I use Chromium primarily. Current build: 

Chromium 4.0.207.0 (Ubuntu build 25615)

I'm using the latest Flash 10 alpha from Adobe Labs.

---

