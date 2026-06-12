---
title: "Gwibber FAIL!! (with facebook)"
date: 2010-06-08
forum: General Help
---

### Post by gnomeout on 2010-06-08
Hi, I have a clean installation of Lucid Lynx, and I have reinstalled it several times (for different, unrelated reasons). And no matter what Gwibber NEVER works properly. 

I only use it for the facebook service since that's all I have, I cannot speculate how it works with other services. But facebook is the most popular anyway so it seems a tad ridiculous that it is the least compatible. 

there are 2 main issues I have and I realize that at least one, or maybe both of these are nothing new. But I have yet to find a solution, despite finding tons of bug threads on launchpad. 

Number 1: The text box for updating my status does not appear in my MeMenu (I think thats what its called). It does appear after I select "Broadcast Accounts..." from that MeMenu and the little window appears for adding accounts. It shows my facebook account ALREADY entered and verified. Then I close this window without doing anything inside it and the text box appears in my MeMenu and I can update my facebook status. This is a stupid bug and makes the entire app a complete waste of time since it is faster for me to start my browser and load the full facebook than go through this just for a tiny text box.

Number 2: facebook notifications do not appear on my desktop. I am not even sure facebook is supposed to present notifications, but I am assuming yes since I was asked to select a "notification colour" - a colour I have yet to see actually appear on my desktop. This is a big bug and there are tons of threads reporting this bug on the launchpad bug site(more evidence that it SHOULD send notifications). I have seen some patches and what not proposed but NONE of them work.


SOMEONE MAKE GWIBBER STOP SUCKING SWEATY BALLS!!!!!!!!!

---

### Post by gnomeout on 2010-06-11
bump... any workarounds? anyone?

---

### Post by gnomeout on 2010-06-14
Solved one of my problems... turns out I needed to add "gwibber-service" to my session startup applications. Which is kinda stupid that I had to since its supposed to just work by default... :(

Whoever wrote gwibber does not appear to have actually used it....

I dont even use it, but as long as it is permanently on my desktop thanks to the "indicator-applet" it might as bloody well work!!

---

### Post by rrnwexec on 2010-06-15
I see your location is Chicago/Vancouver. If by chance you find yourself in Vancouver, please check out Ubuntu Vancouver. Lots of fun events, tech support, and we even have developers amongst us who can help with issues like these. Here's the link to join: [http://meetup.com/ubuntuvancouver](http://meetup.com/ubuntuvancouver)

Cheers,
Randall
Ubuntu Vancouver Buzz Generator

---

### Post by gnomeout on 2010-06-30
Bump..... turns out it also no longer is able to POST onto facebook, which I distinctly remember it has done in the past....

author of gwibber = moron

---

### Post by uRock on 2010-06-30
Works fine on my system. Have you tried uninstalling, purging, then reinstalling?

---

### Post by gnomeout on 2010-06-30
> **uRock said:**
> Works fine on my system. Have you tried uninstalling, purging, then reinstalling?

I've gone through three clean installations (for separate reasons) since I posted this topic. And on none of them has Gwibber ever worked... I shall try your advice though anyway... will post back if successful.

I should also add that I am talking about gwibber THROUGH the MeMenu. using the full Gwibber program/GUI works fine for me, other than that it is ugly as heck.

---

### Post by uRock on 2010-06-30
> **gnomeout said:**
> I've gone through three clean installations (for separate reasons) since I posted this topic. And on none of them has Gwibber ever worked... I shall try your advice though anyway... will post back if successful.

I hope it works. I stopped using Gwibber a few weeks ago being it shows everyone's tagged photos and such. If I could get text only on it, then I'd probably keep using it.

---

### Post by colorlessprism on 2010-06-30
i quit using gwibber for various facebook reasons, and do not use evolution, so this is what i did:

```
sudo apt-get remove indicator-me indicator-messages
```

this removes the "memenu" and the messaging icon, emapathy gains its own icon in the task bar and i use thunderbird+firetray for email

---

### Post by gnomeout on 2010-06-30
> **colorlessprism said:**
> i quit using gwibber for various facebook reasons, and do not use evolution, so this is what i did:

```
sudo apt-get remove indicator-me indicator-messages
```

this removes the "memenu" and the messaging icon, emapathy gains its own icon in the task bar and i use thunderbird+firetray for email

Yes, that is not a bad workaround and I could probably just do that, but I like the idea that one day in the distant future gwibber will work and I will see facebook notifications on my desktop, so I'd rather keep it around.

Also, after reinstalling gwibber I can now post onto facebook again... very weird. still cant receive notifications though. what a horrible program..... one day, one day... it will work..

I already use the thunderbird tray icon extension as well so I just uninstalled evolution to get rid of the evolution entry in the messaging menu.

---

### Post by Pepe Lebuntu on 2010-07-03
Gwibber is a disaster. I think many of us were incredibly excited about it when we heard about it coming into Lynx. That and the problems internationally with the Ubuntu One store in Rhythmbox make two of the most exciting additions announced with Lynx an epic, epic fail.

Lynx is turning out to be so bad, they should have called it my suggestion below, "Stylish Skunk"... it pretty much stinks.

---

### Post by jamoncillo on 2010-07-29
yeah... i keep finding bugs and bugs in gwibber. From the very moment I upgraded, then performed a clean install several times (just to get gwibber actually working) 'till know. When it still doesn't work properly

---

### Post by gnomeout on 2010-10-17
So today, this morning, it suddenly works... I just saw my first facebook notification pop up on my desktop!

Too bad it was a notification I had already recieved via facebook and was no longer "new" but whatever...

---

### Post by cjwelborn on 2011-01-02
Just wanted to add to this thread... Gwibber has been working fine for Twitter, it was working for facebook but now it isn't. If I post it only posts to twitter, and any incoming msgs only show from tiwtter. My Facebook account has been authorized, it says everything is fine. Sometimes it says I'm unavailable for no reason, other times it says available but still no Facebook posts. I wish someone could get on this and fix it, this is one of the reasons I like ubuntu, because my Email/Twitter/Facebook is all right there on the desktop. The "MeMenu" (I've heard it called this I think) does not work to post. The text that says "Type here to post..." or whatever never automatically clears itself. I' like to just click on it and have it cleared, ready for a msg. I have to manually delete all the text and then enter a msg. And still, it posts to Twitter and not Facebook. I'm a seasoned veteran in Windows, new to Ubuntu, so maybe I'm missing something, but it just seems buggy to me.

---

### Post by gnomeout on 2011-01-02
ya, it stopped working for me too.... still hate whoever is developing this thing..

---

### Post by FishRCynic on 2011-02-19
This is an older thread but this allowed gwibber to work with facebook 
for me.

A new maverick install amd64 would not add facebook account.
 
UNTIL 
i added the packages 
gir1.0-gwibber-0.0 & 
gir1.0-gwibber-gtk-0.0 (which installed a number of dependencies). 
Works great now.

---

### Post by gnomeout on 2011-02-21
> **FishRCynic said:**
> This is an older thread but this allowed gwibber to work with facebook 
for me.

A new maverick install amd64 would not add facebook account.
 
UNTIL 
i added the packages 
gir1.0-gwibber-0.0 & 
gir1.0-gwibber-gtk-0.0 (which installed a number of dependencies). 
Works great now.

I dont have those packages in my repos... are they included in Ubuntu Lucid.

---

### Post by lalitpur on 2011-05-06
Thanks to FishRCynic.

> **FishRCynic said:**
> 
i added the packages 
gir1.0-gwibber-0.0 & 
gir1.0-gwibber-gtk-0.0 (which installed a number of dependencies). 
Works great now.


Adding gir1.2-gwibber-0.1 & gir1.2-gwibber-gtk-0.1 in Synaptic solved the FB notifications for me.  Gwibber had not worked in 10.10 or 11.04.   Now, things seem to be fine (running Ubuntu 11.04 64-bit).

---

### Post by Gary_inNYC on 2011-05-24
I know this is an old thread, but have you considered adding the gwibber daily build from ppa?  I had issues with Gwibber since Lucid's release until I just went with the PPA build.  I haven't had issues with it since.

Check out this link:
[https://launchpad.net/~gwibber-daily/+archive/ppa](https://launchpad.net/~gwibber-daily/+archive/ppa)

from terminal:
sudo add-apt-repository
sudo apt-get update

then update gwibber whichever way you prefer.

Good luck

---

### Post by linuxinstalledfromhdd on 2011-05-24
You need the Gwibber PPA to be enabled to get updates in order to keep this applicaiton working with twitter that constantly is providing changes to their system. Same thing goes with chat applications in Ubuntu. Sometimes it helps to have the PPAs enabled so we are in sync with any changes to their services.

---

