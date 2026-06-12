---
title: "Lubuntu freezes on youtube"
date: 2011-07-27
forum: General Help
---

### Post by Chiel92 on 2011-07-27
Lubuntu freezes completely every time I watched a video on Youtube. 
Only the mouse can move, nothing else.

It happens both with Chrome and Firefox, so doesnt depend on the browser.

Can anyone provide me some hints to solve this? Thanks in advance.

---

### Post by Chiel92 on 2011-09-17
bump

---

### Post by kerry_s on 2011-09-17
Try uninstalling it in synaptic & reinstalling it.

---

### Post by garvinrick4 on 2011-09-17
#Try playing it at 240 instead of 360 or 720. On lower right of flashplayer box.
#See what your cpu usage is while playing flash video. Could be using all your cpu up. (Think they have a system montitor package in lubuntu) or "top" in terminal without quotes.
#Some sites using flash have HD and SD use SD.
#News papers like New York times even shoot in high def camara's.
#Flashplayer is a glut.

---

### Post by Chiel92 on 2011-09-17
> **garvinrick4 said:**
> #Try playing it at 240 instead of 360 or 720. On lower right of flashplayer box.
#See what your cpu usage is while playing flash video. Could be using all your cpu up. (Think they have a system montitor package in lubuntu)
#Some sites using flash have HD and SD use SD.
#News papers like New York times even shoot in high def camara's.
#Flashplayer is a glut.

Actually the problem does only appear when i'm done watching a video, or when I switch to another video.

---

### Post by Chiel92 on 2011-09-17
> **kerry_s said:**
> Try uninstalling it in synaptic & reinstalling it.

you mean lubuntu, firefox of chromium?

---

### Post by kerry_s on 2011-09-17
> **Chiel92 said:**
> you mean lubuntu, firefox of chromium?

Menu-> system tools-> synaptic package manager

Unless you installed flash some other way?

---

### Post by claracc on 2011-09-18
If your computer has very low specs, it could be a pain to play flash videos.

I mean, in my old pentium III laptop with lubuntu 11.04 and using epiphany browser to watch embedded flash videos from sites as bbc news or youtube, cpu is working 100 % and video is in slow motion ( I think adobe flash is the guilty one, being a so much resources consumption software).

I have fixed partially the problem ( only in youtube flash videos, not in newspapers's embeddeb flash videos) copying the url of video and playing it directly in vlc. Previously you have to copy a lua file ( it is in the vlc forums what you have to do to see youtube videos in vlc) since youtube has recently changed its layout

---

### Post by Chiel92 on 2011-09-18
> **claracc said:**
> If your computer has very low specs, it could be a pain to play flash videos.

I mean, in my old pentium III laptop with lubuntu 11.04 and using epiphany browser to watch embedded flash videos from sites as bbc news or youtube, cpu is working 100 % and video is in slow motion ( I think adobe flash is the guilty one, being a so much resources consumption software).

I have fixed partially the problem ( only in youtube flash videos, not in newspapers's embeddeb flash videos) copying the url of video and playing it directly in vlc. Previously you have to copy a lua file ( it is in the vlc forums what you have to do to see youtube videos in vlc) since youtube has recently changed its layout

My computer should be fast enough. On Ubuntu and windoze everything works fine. I've got a 4 GB RAM and 2,2 GHz dual core.

---

### Post by Chiel92 on 2011-09-18
> **kerry_s said:**
> Menu-> system tools-> synaptic package manager

Unless you installed flash some other way?

Ah, so you mean that I should reinstall flash? Sorry, that wasn't clear to me. I will try that.

---

### Post by Zephilinox on 2011-09-18
> **Chiel92 said:**
> Ah, so you mean that I should reinstall flash? Sorry, that wasn't clear to me. I will try that.

The way I install flash is

```
sudo apt-get install flashplugin-installer
```if that's how you installed your version of flash, try this instead, and vice-versa:

```
sudo apt-get install flashplugin-nonfree
```

make sure you uninstall it first:

```
sudo apt-get purge flashplugin-installer && sudo apt-get purge flashplugin-nonfree
```

---

### Post by whatthefunk on 2011-09-18
You could also try installing the Firefox plugin Flash-Aid.  It will make sure you have the right flash plugins.

---

### Post by garvinrick4 on 2011-09-18
Here is a thread where Flash aid a Firefox addon cured I was working with yesterday,
give flash aid a whirl it has cured many a flashplayer woes.
[http://ubuntuforums.org/showthread.php?t=1845908](http://ubuntuforums.org/showthread.php?t=1845908)

---

### Post by wildmanne39 on 2011-09-18
+1 for flashaid it fixes most flash related issues.

---

### Post by Chiel92 on 2011-09-19
Thanx guys!!
This is useful information!

---

### Post by wildmanne39 on 2011-09-19
Hi, your welcome!

---

### Post by amjjawad on 2011-09-20
Chiel92, could you please confirm what release of Lubuntu are you using?


Wildmanne my friend, is Flash-Aid compatible with the latest Firefox?

---

### Post by wildmanne39 on 2011-09-20
Hi amjjawad, yes it is.

You should fill out an application for ubuntu membership.

---

### Post by amjjawad on 2011-09-20
> **wildmanne39 said:**
> Hi amjjawad, yes it is.
Few days ago I checked it and it wasn't. Good to know it's now :)
Will give it a try when I'm on Test PC.

> 
You should fill out an application for ubuntu membership.
Too early for me, my friend :) have many things in mind right now. I'm already a member in Lubuntu and LXDE Team but there are few steps I must do before it's 100% official :)

Thanks a lot :)

---

### Post by Chiel92 on 2011-09-21
> **amjjawad said:**
> Chiel92, could you please confirm what release of Lubuntu are you using?


How can I check? 
```

cat /etc/lsb-release

```
says:

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"

---

### Post by Chiel92 on 2011-09-21
> **Zephilinox said:**
> The way I install flash is

```
sudo apt-get install flashplugin-installer
```if that's how you installed your version of flash, try this instead, and vice-versa:

```
sudo apt-get install flashplugin-nonfree
```

make sure you uninstall it first:

```
sudo apt-get purge flashplugin-installer && sudo apt-get purge flashplugin-nonfree
```

I ran an update, purge and reinstalled the packages you described. First results are hopeful :):)

---

### Post by amjjawad on 2011-09-21
> **Chiel92 said:**
> How can I check? 
```

cat /etc/lsb-release

```says:

DISTRIB_ID=Ubuntu
** DISTRIB_RELEASE=11.04**
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"

Thanks a lot, that's what I need to know.

I don't have that issue with Youtube but I do have it with a game on Facebook but since I have no time for games and stuff anymore, I didn't bother to fix it.

My guess that you need to update Flash Player or re-install it.

Are you using the latest Browser Version?

> **Chiel92 said:**
> I ran an update, purge and reinstalled the packages you described. First results are hopeful :smile::smile:

Keep us updated :)

---

### Post by Chiel92 on 2011-09-21
Most of the time I do not get problems with youtube anymore. But Lubuntu still hangs sometimes. I will try to get more specific information about when Lubuntu will hang. I will try to install flash aid also, after I found out how to reproduce a crash.

---

### Post by amjjawad on 2011-09-21
> **Chiel92 said:**
> Most of the time I do not get problems with youtube anymore. But Lubuntu still hangs sometimes. I will try to get more specific information about when Lubuntu will hang. I will try to install flash aid also, after I found out how to reproduce a crash.

What do you mean by "still hangs"? are you talking about Youtube and Flash or in general?

Please, let me know if there is any other issues that you have and we'll help each other to fix it. I'm a new member of LXDE and Lubuntu Team and I'd like to know more about such issues.

:)

---

### Post by Chiel92 on 2011-09-21
> **amjjawad said:**
> What do you mean by "still hangs"? are you talking about Youtube and Flash or in general?


Still talking about youtube.

> **amjjawad said:**
> 
Please, let me know if there is any other issues that you have and we'll help each other to fix it. I'm a new member of LXDE and Lubuntu Team and I'd like to know more about such issues.

:)

I will do that :) I like the concept of Lubuntu, because its smaller and faster than ubuntu. 

Right now i'm starting a new thread about other graphical issues.

---

### Post by amjjawad on 2011-09-21
> **Chiel92 said:**
> Still talking about youtube.
Ok then, I'll wait for some updates from your side :)


>  I will do that :) I like the concept of Lubuntu, because its smaller and faster than ubuntu. 
Glad to know that and if you're interested, please check this link: [https://wiki.ubuntu.com/Lubuntu/GettingInvolved](https://wiki.ubuntu.com/Lubuntu/GettingInvolved)
Same link on my signature.

> Right now i'm starting a new thread about other graphical issues.Please send me the link once you're ready.

---

