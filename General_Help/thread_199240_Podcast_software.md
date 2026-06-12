---
title: "Podcast software?"
date: 2006-06-18
forum: General Help
---

### Post by princemackenzie on 2006-06-18
I just have a general question for podcast listeners out there: what software to do you as an aggregator?

I need something that can easily sync to my iPod with GTKPod.  I have tried three programs:

1. Rhythmbox won't download podcasts at all.  No matter what feed I choose, it just says "failed" and won't D/L them.

2. PenguinTV does a nice job, but it both hides the podcasts in ~/.penguintv, and it also has its own naming scheme for the podcasts which make a mess of things when trying to sync it to an iPod.

3. I'm using gPodder right now which is okay, but also names things strangely and I end up renaming most of the downloaded podcasts by hand before putting them on my iPod.

Any suggestions?  What do you use?

---

### Post by tracyde on 2006-06-18
I have used a lot of various "podcatchers" and still have not found one that does everything just how I want it.

I have currently been using bashpodder to download and then use gnupod to add to iPod.

I am planning on creating a podcatcher written with Perl and either GTK2 or Gnome2 modules.  I am still in the research phase but have created an app to download podcasts with Perl before.

Let me know if you would be interested, I am getting ready to setup a project page for it to help gather ideas for functionality to implement.


-- Ciou

---

### Post by sam hassell on 2006-06-19
I would be interested, although I am a webdev and don't know python. Would definitly like to watch this project grow.

---

### Post by patwack on 2006-06-19
have you tried amarok? i had podcast support and ipod support, i'm not sure how that works though as i dont own an ipod.

just a thought, Paddy

---

### Post by tronica on 2006-06-19
try bashpodder

[http://linc.homeunix.org:8080/scripts/bashpodder/](http://linc.homeunix.org:8080/scripts/bashpodder/)

---

### Post by sbassett on 2006-06-19
[QUOTE=patwack]have you tried amarok? i had podcast support and ipod support, i'm not sure how that works though as i dont own an ipod.

just a thought, Paddy[/QUOTE]


Agreed. Amarok does a great job with podcasts. You can update and drag and drop your podcasts all from the sidewindow. Amarok also integrates with Gnome fairly well.

---

### Post by turbojugend_gr on 2006-06-19
I own an iPod, i never used it with linux still though, I like the automatic update of iTunes so I won't put it in gtkPOD still, anyway I download podcasts with iPodder (then manually add them to iTunes) it is very nice and I believe that apart from the repos you can find it in add/remove programms. Give it a try.

---

### Post by unique on 2006-06-19
You could also try [Cast Podder]("http://dev-1.borgforge.net/castpodder/wiki/Downloads") It's the Linux fork of the ipodder project.

I use Banshee to manage and sync with my IPOD...  the next version of Banshe is gonna have Podcast support.  Give [Banshee]("http://www.banshee-project.org/Main_Page") a shot it rox!

---

### Post by soze on 2006-06-19
[QUOTE=unique]You could also try [Cast Podder]("http://dev-1.borgforge.net/castpodder/wiki/Downloads") It's the Linux fork of the ipodder project.

I use Banshee to manage and sync with my IPOD...  the next version of Banshe is gonna have Podcast support.  Give [Banshee]("http://www.banshee-project.org/Main_Page") a shot it rox![/QUOTE]

I second the vote for Banshee. I'm using the compile-your-own version and it has a working podcast plugin which I've been using for a few weeks without any problems.

---

### Post by Prospero2006 on 2006-06-19
I use amarok to catch all my podcasts. I love it.

Pros

---

### Post by tracyde on 2006-06-21
I have tried Banshee, and like the program but do not like the way it handles podcasts.  I subscribe to a large number of podcasts (about 10) and Banshee keeps wanting to keep all old podcast entries even if they are not downloaded, and get this the entries reappear if you delete them.

---

### Post by tracyde on 2006-06-21
Amarok is great for everything that it does except for Podcast management.  I am sorry but with an application that robust and massive you should just have to click a button and have your podcasts downloaded and added automatically.  You should not have to drag and drop the podcasts into a queue window, that is just annoying.

---

### Post by allenshull on 2006-07-30
Tracyde, I agree about Amarok and it's annoyingly non-automatic podcast updating.  I've tried it, gtkpod, listen, banshee, yamipod, and finally gpodder, and only gpodder works like a program should--it downloads podcasts and updates them on the ipod in very few clicks.

The iTunes standard--One click update podcasts, one click update ipod--seems to be not attained, or even reached for, by most linux music players / podcast software.

Though, again, gpodder seems to be coming closest, while having a wonderfully non-bloated interface.  Maybe by 1.0...

---

### Post by hanzj on 2006-08-05
> **allenshull said:**
> Tonly gpodder works like a program should--it downloads podcasts and updates them on the ipod in very few clicks.


I've installed gpodder (0.8.0) and i've been able to add a channel and download the podcasts. But how do we go about syncing them to the iPod? In the File drop-down menu, "Sync to iPod" is greyed out. It cannot be selected. Please advise.

---

### Post by allenshull on 2006-09-05
Is your iPod mounted before you sync?  gPodder has only had Sync greyed out when my iPod isn't mounted.

---

### Post by hanzj on 2006-09-05
gpodder works now. I forgot what I did to make it work.

---

### Post by morguns on 2006-09-24
> 1. Rhythmbox won't download podcasts at all. No matter what feed I choose, it just says "failed" and won't D/L them.for what it's worth, i had the same problem. the files actually downloaded, but rhythmbox always showed 'failed'. i did the fix to make mp3's playable and now rhythmbox is downloading fine. there's prolly other things broken, but i haven't stumbled on them yet.

---

### Post by jbaerbock on 2008-06-03
Gpodder works perfectly for me, though had to manualy point it to the correct mount point lol.

---

