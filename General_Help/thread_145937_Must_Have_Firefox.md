---
title: "Must Have Firefox?"
date: 2006-03-17
forum: General Help
---

### Post by Hangetsu on 2006-03-17
I'd like to replace Firefox with Opera, and Evolution with Thunderbird.  I've gone into Synaptic to remove Firefox, but it shows the ubuntu desktop as being dependent on Firefox -- Is this the case?  

Its not a crisis that I'd have multiple browsers on the machine (Windows pretty much left IE on the box as well), but I was hoping to avoid things like this in Linux.

Thanks!

---

### Post by dpaint4 on 2006-03-17
Yep. You can't remove it, but you can removed it from your Applications list. Go to System Tools > Application Menu Editor, and click on the category, "Internet". Uncheck the box next to things you don't want showing up.

Ubuntu is reliant on the FF rendering engine for certain essential features. It's also the reason it comes with a non-upgradeablec copy of 1.0.7 or whatever that number was. Think that's it.

I was able to make a seperate install of FF 1.5.0.1, set it as my default browser, and remove the 1.0.7 version from my applications menu.

You'll just do the same thing, but with Opera.

---

### Post by aysiu on 2006-03-17
The *ubuntu-desktop* is just a meta-package that points to the default applications that get installed with Ubuntu.

It's safe to uninstall.

Don't believe me? Go ahead and read the description of *ubuntu-desktop* in Synaptic.

---

### Post by Coelocanth on 2006-03-17
aysiu, I've read enough of your posts to accept you know what you're talking about, but are you sure about this? I've seen a number of posts that say you can't uninstall Firefox 1.0.7 or you'll 'break' a number of things. Even the Firefox 1.5 wiki says this. Or am I misunderstanding something (which is not unusual for me)?

---

### Post by aysiu on 2006-03-17
[QUOTE=Coelocanth]aysiu, I've read enough of your posts to accept you know what you're talking about, but are you sure about this?[/quote] Actually, I have a high number of posts, but I'm still a newbie--my first Ubuntu anniversary is in two months, my first Linux anniversary in one month. 

> I've seen a number of posts that say you can't uninstall Firefox 1.0.7 or you'll 'break' a number of things. Even the Firefox 1.5 wiki says this. Or am I misunderstanding something (which is not unusual for me)? It's quite specific about what breaks, actually: > If you use this guide, do not remove the Ubuntu version of Firefox. Doing so will break the following packages: **Yelp** (help viewer), **Epiphany**, **Gnome-app-install** (Add Applications), **Liferea**, **Blam** and any application requiring the gecko rendering engine. So, I guess you're right--if you want any of those applications, it's probably not a good idea to remove Firefox.

My clarification was simply to allay any fears that the *ubuntu-desktop* is a sacred package.

---

### Post by Hangetsu on 2006-03-17
This was an informative discussion -- That you all!

I think my plan will be to leave it on -- I'm still too newbie to know the impact of those apps as I start to use Ubuntu (i.e. may not need it now, may need it in 2 weeks).  However, I'll get the Opera install done and make that my primary browser.

On the Thunderbird side, what I'm really looking for is an email app with a very strong anti-spam filter.  How does Evolution work in that regard?  I'm not a fan of Opera's M3, but maybe I should give Evolution a shot if it has the goods.

---

### Post by Coelocanth on 2006-03-17
Ah, yes, sorry. I was concerned there may be other things broken as well. I bow to you, good sir! And I hope that when my first anniversary with Ubuntu and Linux rolls around (in about 10 1/2 more months), I'll have as wide a knowledge base as yourself. :-D 

Okay folks, carry on! Nothing to see here...

---

### Post by aysiu on 2006-03-17
I honestly don't know that much.

I remember a few months ago, there was some thread about how geeky people are (based on an online quiz). Out of all the forum veterans, I was the lowest-scoring (something like under 30%).

I'm truly a newbie to Linux--just a newbie who reads a lot and tries to figure things out.

A lot of times people talk about the "steep learning curve" of Linux. I'd say that with a couple of weeks of serious dedication, the steepest part is easily overcome. After that, it's little by little up a slight incline.

---

### Post by dcstar on 2006-03-17
[QUOTE=aysiu]
......
 It's quite specific about what breaks, actually:  So, I guess you're right--if you want any of those applications, it's probably not a good idea to remove Firefox.

My clarification was simply to allay any fears that the *ubuntu-desktop* is a sacred package.[/QUOTE]
Removing FF 1.0.7 from Breezy is bordering on insanity - if you believe the people who gave the reasons why FF 1.5 was never backported by them.

Many (many) Ubuntu functions are tied into the FF 1.0.7 install, for the sake of a few MB of disk space you risk breaking your Breezy install in ways that may never become apparent.

Don't do it.

---

### Post by aysiu on 2006-03-17
When you say "Breezy install," I assume you mean a Gnome install, because Kubuntu does not default to having Firefox installed at all, and it's Breezy and works just fine.

---

### Post by rfruth on 2006-03-17
I agree, *leave* Fx, remove it and your flirtn with disaster (that' a good song)

---

### Post by Strike&gt;&gt; on 2006-03-18
Yeah aysiu is right about firefox only being really important to Gnome, because when i installed Dapper flight 5 , Kubuntu version, firefox wasn't included.

---

### Post by akiro.yamamoto on 2006-03-18
I have both 1.0.7 and 1.5 installed on my system (FF 1.5 is my default), having 
both should not cause any adverse effects on a Breezy Gnome install.
So I would recomend that if you want FF 1.5 use the guide on the wiki and leave
FF 1.07 installed on the system.
Just my $0.02 ;)

---

