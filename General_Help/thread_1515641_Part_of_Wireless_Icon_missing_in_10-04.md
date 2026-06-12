---
title: "Part of Wireless Icon missing in 10-04"
date: 2010-06-22
forum: General Help
---

### Post by oxf on 2010-06-22
Has anyone else else experienced this in Lucid?

A chunk of the wireless icon on the top panel is missing, i.e a black square is there (see screenshot). The Wireless sill works fine and the missing part wasn't there on install. But after a few boot ups it's appeared and now wont go away. I've installed twice now and with the same result. Doesn't seem to affect functionality but looks funny. 

I'm not sure if its a bug with the wireless icon or the notification applet? Any ideas on how to find  a fix?

Thanks

---

### Post by ajgreeny on 2010-06-22
This is probably related to the theme you have chosen to use.  Try a different theme and you will get a totally different icon, and the black block may also disappear.

---

### Post by oxf on 2010-06-22
> **ajgreeny said:**
> This is probably related to the theme you have chosen to use.  Try a different theme and you will get a totally different icon, and the black block may also disappear.

Thanks
Maybe... Right now I'm just got the default theme. If I right click and remove it from panel and then add it back to panel again it restores the complete icon. However, previously the problem returned after a couple of boots.

---

### Post by oxf on 2010-06-22
I think you might be right. It does seem to be associated with the default theme. I've tried a couple of custom themes and so far the problem hasnt appeared.

---

### Post by dondiego2 on 2010-06-22
Here is mine - it's fine.  Must be a different theme but I thought it was standard.





[IMG]http://picasaweb.google.com/crshuby/DropBox?authkey=Gv1sRgCOqv18KDwIjbCQ#5485740831109183890[/IMG]

---

### Post by oxf on 2010-06-23
> **ajgreeny said:**
> This is probably related to the theme you have chosen to use.  Try a different theme and you will get a totally different icon, and the black block may also disappear.

This is very interesting! It may be related to the theme and I also wonder if there isn't a graphics issue component as well. Along with the black block in the wireless icon I also noticed when  launched Firefox immediately after boot up there was a small block (maybe an inch and a half square on my screen)  on the upper left corner right below the toolbar that loaded slightly after the rest of the page creating a bigger black block for  a fraction of a second. Subsequent FF launches still had this effect but the lag was much reduced.

The theme I was using was the default one with the mod described in the Lucid bugs/workarounds at the top of this page to move the minimise/maximise from the left to top right of the page

So I created a new theme, almost the same, but with a minor variation  and so far not noticing any of these issue (fingers crossed) I have to wonder if there isn't  a graphics part to this as I have the ATI Radeon Express 200  which seems to be problematic for some people?

---

### Post by oxf on 2010-06-23
Well I spoke too soon! I not convinced that it's linked to a theme since it seemed to be happening to several themes. But right now its not happening to any. So still suspect graphics drivers..

---

### Post by coldraven on 2010-06-23
Nope, it must be a bug!
I have a fresh install of 10.04 with the default theme and I have had the same problem.
I have also had an all black icon but it vanished after reboot.
I'm hoping that an upgrade to the Network Manager will sort it out.
My Wi-Fi worked throughout.
No Compiz on this installation.
ATI X1250 card and Turion x2 (2GHz) running 32bit 10.04

---

### Post by oxf on 2010-06-23
> **coldraven said:**
> Nope, it must be a bug!
I have a fresh install of 10.04 with the default theme and I have had the same problem.
I have also had an all black icon but it vanished after reboot.
I'm hoping that an upgrade to the Network Manager will sort it out.
My Wi-Fi worked throughout.
No Compiz on this installation.
ATI X1250 card and Turion x2 (2GHz) running 32bit 10.04
  
OK well some comfort that I'm not alone. Funny thing is right now, like the last couple of hours, the problems not occurring. So will monitor...

No Compiz here either
ATI Radeon Xpress 200M
AMD Turion 64 
10.04 32 bit

---

### Post by ajgreeny on 2010-06-24
I am interested to hear you talk of the un-rendered square at top left of your screen in Firefox, which I also see, not only in FF but also in Thunderbird.  I think it must be related to mozilla applications, perhaps, but as it quickly disappears, I have not worried about it too much.

It could be a symptom of the poor ati driver, however, as I run an ati 9200SE, which was brilliant up to ubuntu 9.04, terrible in 9.10, needing to run at 16 bit colour to have any desktop effects at resolutions above 1024x768, hopeless on my larger screen, and is similarly problematical in 10.04, still needing 16 bit colour, but so much slower a refresh rate than all previous ubuntu versions.

I will watch this space for future posts and info.

---

### Post by oxf on 2010-06-24
> **ajgreeny said:**
> I am interested to hear you talk of the un-rendered square at top left of your screen in Firefox, which I also see, not only in FF but also in Thunderbird.  I think it must be related to mozilla applications, perhaps, but as it quickly disappears, I have not worried about it too much.

It could be a symptom of the poor ati driver, however, as I run an ati 9200SE, which was brilliant up to ubuntu 9.04, terrible in 9.10, needing to run at 16 bit colour to have any desktop effects at resolutions above 1024x768, hopeless on my larger screen, and is similarly problematical in 10.04, still needing 16 bit colour, but so much slower a refresh rate than all previous ubuntu versions.

I will watch this space for future posts and info.

Interesting about your comments in both FF and Thunderbird.
The un-rendered square only seems to be really noticeable on the first FF launch after boot up. You are right it's very quick and I'm not even sure it was there tonight as I was not looking for it, its that fast. I suspect it's related to the missing part of the wireless icon and is a driver issue too. The icon problem did not seem to be pressent most of today but was back again tonight. Its easily resolved by deleting from the top panel and then adding it again. I'll continue to monitor and research it and report bac if I find anything.

---

### Post by oxf on 2010-06-28
Update.....

I beginning to think that the small un-rendered square in upper left is not worth worrying about, at least for me. It's only there on the first launch of FF and now is so darned quick  that I have to stare at that area of the screen while FF launches to catch it. What caused it to slightly longer initially I dont know but now I wouldn't have noticed it.

The other issue i.e the wireless icon is interesting. The blacked out chunk has now also gone away too so I don't know? However imediately after boot up the field in the top panel that contains the icon is surrounded by dotted line, like its a dotted square around it. Also in the bottom panel there is a dotted line around the field for the Windows List" indicator even though at that point there's nothing minimised to the bottom panel. 

This phenomena only occurs immediately after boot up and as soon as I click somewhere on the desktop they vanish I'll fix it if I can but if not I can cope. Any thoughts???

---

### Post by oxf on 2010-07-02
> **coldraven said:**
> Nope, it must be a bug!
I have a fresh install of 10.04 with the default theme and I have had the same problem.
I have also had an all black icon but it vanished after reboot.
I'm hoping that an upgrade to the Network Manager will sort it out.
My Wi-Fi worked throughout.
No Compiz on this installation.
ATI X1250 card and Turion x2 (2GHz) running 32bit 10.04

I'm beginning to think this problem is related to how the icons, or the Notification Applets from the "add to panel" selection, are loaded into the top/bottom panels on boot up. The dotted squares around the icons are still here.

I just installed 10.04 on another PC and a similar problem is occuring. This time some boot ups result in mutiple copies of the Wireless icon in the  upper panel or no icon at all. Although most times there just one surrounded by the dotted line. Also something strange happening with the icon in the lower panel which has a white bar through it at times.

Anyone else experiencing strange goings on in the panels???

---

### Post by coldraven on 2010-07-27
Well the Wireless icon just completely vanished during this session!
However I am still connected via Wi-Fi and most likely it will re-appear after a re-boot.
No black gaps this time just no icon.
While it does appear it always has a red exclamation mark, what's that about?
I'm 20ft. from the router and in view of it.
And why does it give no information about signal strength or connection speed?
Last week the taskbar showed my login name twice and the Switch User/Shutdown button was squeezed off the screen on the top right.
I am loathe to install 10.04 on friends' PCs if they are going to have trouble networking.

---

### Post by mansourk on 2010-07-27
Hi,
 my graphics is an integrated intel graphics and I have the same problem of wireless icon. there is also a problem of other applets, some times when i login some icons (for example notification area  or clock applet) fail to load correctly, or there are two of them instead of one. i use the default theme.

---

### Post by oxf on 2010-08-02
An update....
I believe this is part of a bigger problem, i.e. a bug!

I installed Lucid onto another mini Laptop I just got.  The first install I got exactly the same problem. Also the battery icon didn't load properly. I reformatted and did a fresh install. Problem  was essentially resolved. I've had occasional issues with the battery icon and maybe once with the Wireless icon but mostly they've gone away. 

Tonight when booting up  got an error message "unable to load notifcation applet... do you want to cancel/delete" I deleted and the re added the applet to the panel and all is OK. So the fact I'm getting this on a separate  PC and the fact that a few others report problems too point a bug loading the notification applets!

---

### Post by kenbuntu75 on 2010-08-04
I noticed this wireless icon issue after a recent fresh install of 10.04. Since I don't use Empathy (I use Pidgin) I removed it using the add/remove software menu. After Empathy was removed the wireless icon has no issues. 

This may be an issue related to the iconography of empathy and the wireless icon placement on that portion of the panel.

If you don't use empathy, remove it from your system. This will likely fix this issue.


======================================
10.04 on HP dv4000, 1.0GHz intel, 1.0Gb ram
Dual boot with Xp using wubi

---

### Post by oxf on 2010-08-07
> **kenbuntu75 said:**
> I noticed this wireless icon issue after a recent fresh install of 10.04. Since I don't use Empathy (I use Pidgin) I removed it using the add/remove software menu. After Empathy was removed the wireless icon has no issues. 

This may be an issue related to the iconography of empathy and the wireless icon placement on that portion of the panel.

If you don't use empathy, remove it from your system. This will likely fix this issue.


====================================== 
10.04 on HP dv4000, 1.0GHz intel, 1.0Gb ram
Dual boot with Xp using wubi

Hmm interesting? I've never used Empathy (yet) and the issue is sporadic and for now mostly non existant. Can you elaborate why you think it's liked to Empathy? I mean it went away after you removed empathy but was that the cause?

---

### Post by suaf on 2010-08-09
> **kenbuntu75 said:**
> I noticed this wireless icon issue after a recent fresh install of 10.04. Since I don't use Empathy (I use Pidgin) I removed it using the add/remove software menu. After Empathy was removed the wireless icon has no issues. 

This may be an issue related to the iconography of empathy and the wireless icon placement on that portion of the panel.

If you don't use empathy, remove it from your system. This will likely fix this issue.


======================================
10.04 on HP dv4000, 1.0GHz intel, 1.0Gb ram
Dual boot with Xp using wubi

Same problem. I removed Emapthy and rebooted. No result. Thanks, though.

---

