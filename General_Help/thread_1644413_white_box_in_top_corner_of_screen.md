---
title: "white box in top corner of screen"
date: 2010-12-13
forum: General Help
---

### Post by mattman85 on 2010-12-13
I just installed 10.04.1 a couple of weeks ago, and have been having some issues with it. A couple I already know the "answers" to, but there's one that I'm currently trying to figure out..

1. Empathy not starting automatically when I log in
2. Keyring constantly locking
3. A white box appearing in the top left corner of screen after any display event

"Answers" thus far:
1. It's because Empathy starts before the wifi connection is established. Empathy doesn't have a 'retry in 30 sec if connection failed' featuer. I wish it did...

2. I dunno. When I was using 8.04, I never had the issue of having to put in my password after just having logged in, just to unlock my keyring.. Is this default now? Is there a way to keep it unlocked, as it's annoying.

3. If the screen goes dim, white box appears in the upper left hand corner. If the screen comes back from being asleep, white box appears. If I manually adjust the brightness, the box appears. On login, it appears. Very awkward. This happens in 10.10, also.. Anyone know why this is happening? I can't find any information anywhere. I'm attaching a picture just to show what I mean.


EDIT:
I also notice that Firefox is really slow in 10.04.1 and 10.10. On the LiveCDs for each version, Firefox is fast, but after installing to the HDD, I do all the updates, and that's when Firefox gets really slow.. So is it a dependancy issue, or the latest version of FF?

---

### Post by mattman85 on 2010-12-14
just an update on the issues...

Firefox:
so, it turns out that Firefox being slow is [partly] due to IPv6. if I go to FF, and go to about:config, filter for only ipv6, I can set 'disable ipv6' to true, and restart firefox. Afterwards, it runs significantly faster. Unfortunately, this doesn't fully solve the issue because after about an hour, it was slow again, to the point that I'm on the 10.10 liveCD right now.. Even Chromium was slow.. They both stopped going to websites, too. I get 'page cannot be displayed' rather than Google's page or UbuntuForums.org..


White box on anything display related:
It might have to be GNOME related for my little white box, because I loaded a *ssshhh, don't tell anyone* Fedora *gasp!;)* 14 GNOME i686 liveCD and the white box still shows up; allbeit rather than white, its just random lines of colors, but still in the same region and same dimensions.

Could the white box be related in any way to the open source ATI graphics driver? If so, is anyone else having the issue as well? Perhaps that's why it does the same thing in Fedora 14 GNOME? I'll try to load SLAX 6.1.2 LXDE or LUbuntu and see if it does the same thing. I just need to rule everything I can out, because it's one of the bigger annoyances right now.


Keyring:
I think the keyring issue was related to me auto-logging in. I changed to using the GDM screen, and all is fine with the keyring..


Empathy:
Like I said, not much I can do about that, due to it trying to connect to an internet connection that hasn't established yet. That's due to wifi taking a little bit longer to establish than it does for programs to start running.

---

### Post by matt_symes on 2010-12-14
Hi

There is nothing wrong with Fedora. :)

Kind regards

---

### Post by mattman85 on 2010-12-14
I can confirm that the white box doesn't have to do with Ubuntu or GNOME. I am currently on Fedora 14 LXDE liveCD, and if I lower the brightness of the screen, it STILL shows the white box...

At this point, I'm thinking it has to do with the open source ati driver...

---

### Post by hawthornso23 on 2010-12-14
a reasonable conjecture. If you install the proprietary driver does it go away?

---

### Post by mattman85 on 2010-12-14
> **hawthornso23 said:**
> a reasonable conjecture. If you install the proprietary driver does it go away?

Therein lies the problem.. my laptop has an ATI Radeon Xpress 200M (RS482) graphics card, which was added to the legacy driver last year. If I install the fglrx driver, it will cause a lot of issues with the GUI. 

Unless thats not the case anymore, which was the reason I stopped at 8.04 LTS. as of 9.04 Ubuntu wouldn't support the fglrx driver and at that time, the open source ATI driver (from what I heard) wasn't as robust as it is now.

The proprietary driver doesn't even show up in Additional Drivers anymore, so if I am to test that, how should I go about obtaining it so I can try to install it on a liveCD so as not to screw my install over?

---

### Post by mattman85 on 2010-12-16
well, this just stinks... I know what the white box issue is.. The white box is the same dimensions (only reversed - x:y and y:x) as the blue box that would normally be in its place.. Its my laptops brightness box... i don't know the reason why the open source driver causes it to show up white and with inverted dimensions.

I figured it out because I decided "what the hell. its a clean install of ubuntu 10.10. if fglrx screws it up, I reinstall and move on." I installed fglrx and uninstalled the radeon driver.. once I did that, I restarted. lo and behold, the brightness box shows up, and not the white box. The issue was that I didn't have the Catalyst Control Center and my 1280x800 (16:10) laptop screen was set to 1024x768 (4:3) which was horrible looking. So I guess I'm stuck seeing a white box until the open source driver comes a long more! But I'm grateful the dev team working on it has made the progress they did, because I love Ubuntu.

---

