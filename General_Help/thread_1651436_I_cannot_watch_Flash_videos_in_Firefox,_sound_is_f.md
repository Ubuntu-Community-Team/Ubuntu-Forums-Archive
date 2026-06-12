---
title: "I cannot watch Flash videos in Firefox, sound is fine. Other browsers fine."
date: 2010-12-23
forum: General Help
---

### Post by Rytron on 2010-12-23
Hi.

Firefox was working perfectly until a few days ago. I think it may be caused by something I installed like [this]("http://ubuntuguide.net/enable-transparent-gnome-panelsmenuswindows-in-ubuntu-10-10")?

I cannot watch Flash videos (YouTube, etc.) in Firefox. I can have sound for the videos though. IceCat & Liferea have the same problem. All other browsers fine.

I also removed *[COLOR="Purple"].mozilla[/COLOR]* but that did not solve the problem. Reinstalling Firefox did not help either. ::-k

---

### Post by Rytron on 2010-12-27
```
sudo apt-get install flashplugin-nonfree-extrasound flashplugin-installer

sudo apt-get update; sudo apt-get upgrade
```

I may have done a few other things to help but these are the things I remember. 

Update: The odd thing is that videos fully buffered do not appear in the /tmp folder any longer. Although fully buffered videos do appear in the /tmp when using other web browsers. :roll:

---

### Post by Rytron on 2011-01-09
In synaptic, remove all 'gnash' ~ this makes all videos available in tmp dir when they were played in FF and Liferea. Some videos still do not show in FF and Liferea though.

---

### Post by Rytron on 2011-01-23
This is what I see. [http://i.imgur.com/Ridbg.gif](http://i.imgur.com/Ridbg.gif)

Update: A solution found: Thanks to [TechWiz2100]("http://ubuntuforums.org/showpost.php?p=10317206&postcount=9")

---

