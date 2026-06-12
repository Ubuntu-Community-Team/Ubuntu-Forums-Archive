---
title: "Empathy balloons difficult to read all of a sudden"
date: 2012-07-25
forum: General Help
---

### Post by digitalattorney on 2012-07-25
A couple of days ago I did a system update. Prior to whatever various update(s) took place, my **Empathy pop up balloons** looked great **They [COLOR="Red"]use to look[/COLOR] like this all the time:**

[IMG]http://ubuntuone.com/2hX5FoD56Tlcyb0pILjBXr[/IMG]

**Now when there is a light background beneath them (whenever they pop up), it now looks like this:**

[IMG]http://ubuntuone.com/3WE8VCmwTS2wOljiD3at24[/IMG]

**Here's an example when the screen background is half darker shades and half lighter:**

[IMG]http://ubuntuone.com/6Ok0cS1DCS0ysUoPIGpA6g[/IMG]


[SIZE="3"]QUESTION: How can I get my balloons back to the way they **[COLOR="Red"]use to look[/COLOR] like this all the time:**[/SIZE]

---

### Post by BoogeyOfTheMan on 2012-07-25
What did you use to change the color?

---

### Post by digitalattorney on 2012-07-25
> **BoogeyOfTheMan said:**
> What did you use to change the color?

Well, that's the problem. I didn't change the color. They take on background colors now or something.

---

### Post by BoogeyOfTheMan on 2012-07-25
Theres an app called notifyosdconfig

```

sudo add-apt-repository ppa:leolik/leolik
sudo apt-get update
sudo apt-get install notifyosdconfig

```

That should allow you to change stuff.

---

### Post by digitalattorney on 2012-07-25
> **BoogeyOfTheMan said:**
> Theres an app called notifyosdconfig That should allow you to change stuff.

Thanks for the tip on the app! I finally got it installed, but it didn't solve the problem though. With that installed now though, I guess we can at least rule-out a normal situation. Here's more info to go on.

I didn't mention this in the first post, but this also happened even before I installed NotifyOSD. **When I hover the mouse pointer near the bubble**, it begins to take on the color it should have:

[IMG]http://ubuntuone.com/7QvaRaNWwsAT9gCG5Y7kRV[/IMG]

Please note though that the mouse has to be in a very special nearness to the bubble even to get it to be rendered correctly... Too close to the bubble and I have the same problem as follows

When the **mouse pointer is not close to the bubble**,is when the bubble is not being rendered as it should:

[IMG]http://ubuntuone.com/3c4ogLQXSVZNP0z54iXdqG[/IMG]

And **here's how the balloon still appears one a white background** (no matter the NotifyOSD settings as well):

[IMG]http://ubuntuone.com/5MEv2QANQ2x69xZ8EUyfSN[/IMG]

NotifyOSD Install Note: [I]I followed your code instructions, but the install didn't work.  I did manage to get it installed though by going [here]("http://www.webupd8.org/2011/05/configurable-notifyosd-bubbles-for.html") though, for anyone interested in installing NotifyOSD.

---

### Post by digitalattorney on 2012-07-25
UPDATE:** If I use Ubuntu 2D it works perfectly**, just as it should. I don't believe that remaining in Ubuntu 2D is the option I want to stay with though...

In general, I hear there have been a lot of issues with nVidia graphics cards I hear...I have a GeForce 7150M / nForce 630M/integrated/SSE2/3DNOW!, being used in a HP DV9620us laptop.

[B]AND

I don't have the problem in the Gnome Classic shell![/B] (which I think I may like even better, having now tried it since this issue.)

---

### Post by BoogeyOfTheMan on 2012-07-26
I wasnt sure if that would fix it, but it was worth a shot. 

It appears as though your top panel is semi-transparent, I wonder if that is effecting  the NOSD. I too am having odd NOSD issues at the moment, except mine is just white with black text and nothing I do seems to change it. I had used NOSDconfig to change the color to match my theme a little better, then all of the sudden after a few days of working perfectly, the NOSD is white, no transperancy, with black text.

I may have to try giving classic gnome a shot. And Unity was actually starting to grow on me :(

Keep the thread updated if you discover a fix for your issue please. Maybe one of use will figure something out that helps the other.

---

### Post by digitalattorney on 2012-07-26
> **BoogeyOfTheMan said:**
> Maybe one of use will figure something out that helps the other.

Like

---

### Post by digitalattorney on 2012-07-26
My workaround *for now*:

1. I'm logged into and using the Gnome Classic shell.

2. I enabled Unity features in the CompizConfig

[http://screencloud.net/v/ipdJ](http://screencloud.net/v/ipdJ)

3. So I'm using the Gnome Classic shell with Unity features. The notofications work great... **ADDED BONUS (at least for me)**: I also like the open applications at the bottom of my screen, which the new Unity interface does not incorporate. It allows me to see what apps are open on my desktop with a single look (no mouse movement, key como, etc.)... Invaluable.

[http://screencloud.net/v/sKtn](http://screencloud.net/v/sKtn)

- All the best.

P.S. Screencloud is a pretty cool little screen capture program that I used to take those screenshots. The screen capturing is a bit different in Gnome or I haven't figured it out, but one of my apps (Shutter) doesn't work in it, so it seems.... Anyway,  Screencloud is really simple and offers online storage.

---

### Post by BoogeyOfTheMan on 2012-07-26
That looks great. I'm currently using Cario-dock to keep track of my open windows at the bottom, but its kind of buggy.

I just use the screenshot tool that comes with gnome. I have to scrub out my IP address before I share, so I might as well keep it local.

Heres a pic of mine with the cairo-dock. I think I'm gonna see if I cant get the classic gnome look back now.

---

### Post by Grenage on 2012-07-26
> **BoogeyOfTheMan said:**
> Heres a pic of mine with the cairo-dock.

Ooh, which wallpaper is that?

---

### Post by BoogeyOfTheMan on 2012-07-26
Its this one mirrored.

EDIT: Its normally 1900x1200 but I cant seem to figure out how to upload it at its native res.

---

### Post by Grenage on 2012-07-26
> **BoogeyOfTheMan said:**
> EDIT: Its normally 1900x1200 but I cant seem to figure out how to upload it at its native res.

Curses, but thank you regardless. :)

---

### Post by BoogeyOfTheMan on 2012-07-26
I think Dropbox might let me share it: [http://dl.dropbox.com/u/26008390/-1253800767996.jpg](http://dl.dropbox.com/u/26008390/-1253800767996.jpg)

I tried installing classic gnome and started running into some weird unfortunate problems... internet quit working and on reboot, internet worked but mouse quit working... so I'm going to try and sort those issues out.

---

### Post by digitalattorney on 2012-07-27
> **BoogeyOfTheMan said:**
> I tried installing classic gnome and started running into some weird unfortunate problems... internet quit working and on reboot, internet worked but mouse quit working... so I'm going to try and sort those issues out.

Yeah I started running into problems with Gnome Classic as well. I also find it to be a bit laggy in response time when compared to Ubuntu. So no... It's not an alternative. I get the feeling 12.10 might solve little issues like this... That might be our solution when the time is right.

So I too am back in Ubuntu & still greatly appreciating it, regardless of the quirky notification system for now. If you find a solution though, please remember us here :)

- All the best.

---

### Post by Grenage on 2012-07-27
> **BoogeyOfTheMan said:**
> I think Dropbox might let me share it: [http://dl.dropbox.com/u/26008390/-1253800767996.jpg](http://dl.dropbox.com/u/26008390/-1253800767996.jpg)

Thank you. ^^

---

### Post by BoogeyOfTheMan on 2012-07-27
> **digitalattorney said:**
> Yeah I started running into problems with Gnome Classic as well. I also find it to be a bit laggy in response time when compared to Ubuntu. So no... It's not an alternative. I get the feeling 12.10 might solve little issues like this... That might be our solution when the time is right.

So I too am back in Ubuntu & still greatly appreciating it, regardless of the quirky notification system for now. If you find a solution though, please remember us here :)

- All the best.

I started playing around with a few different themes and like you said, the window color will cause the notifications to change color. I'm having a difficult time finding a theme that doesnt look look funky though.

> **Grenage said:**
> Thank you. ^^
You're welcome :)

---

### Post by BoogeyOfTheMan on 2012-07-28
Well, I discovered what my issue was, I have xcfe4-notifyd delivering the notifications instead of notifyosd. Now I just need to figure out if it will divert back if I remove the xfce one.

---

### Post by digitalattorney on 2012-07-28
> **BoogeyOfTheMan said:**
> Well, I discovered what my issue was, I have xcfe4-notifyd delivering the notifications instead of notifyosd. Now I just need to figure out if it will divert back if I remove the xfce one.

I checked in Synaptic Packet Manager and I don't have xcfe4-notifyd delivering notifications. It's at the bottom of my list, but not active or installed:

[IMG]http://ubuntuone.com/4GN6BLP29IcZvF9EUT8N78[/IMG]


**What gives you belief that xcfe4-notifyd is the cause of your issue?**

---

### Post by digitalattorney on 2012-07-29
I've reported this transparency issue as a bug:

["balloon notifications - transparency malfunctioning"]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1030444")

---

### Post by BoogeyOfTheMan on 2012-07-29
Have you opened up the system-monitor to see if notify-osd is what is delivering the notices? Thats how I figured it out, one of the fixes I found said to restart it, I saw that it wasnt even running.

---

### Post by digitalattorney on 2012-07-29
I hope that worked for you and your issue, as will be seen by those that see the last screenshot I uploaded though, that's not my issue. notify-osd has always been running. I've escalated this so if you find a real solution, feel free to report it. In the meantime, I'll hang in there.

---

### Post by BoogeyOfTheMan on 2012-07-29
Have you tried uninstalling it and reinstalling it? Or reverting to an older version?

---

### Post by digitalattorney on 2012-07-29
I did try uninstalling and reinstalling it. I don't believe I ever saw a screenshot of your issue. Are you saying you no longer have the problem?


SIGNATURE
*Follow this thread for possible bug resolution: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1030444](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1030444)*

---

### Post by BoogeyOfTheMan on 2012-07-29
Yeah, I got it fixed last night. But it wasnt the same problem that you were having. Mine was that the notifications were suddenly white and no matter what I did they wouldnt change. 

I'm just spewing out ideas from the many threads and articles I read trying to fix my problem.

---

### Post by digitalattorney on 2012-07-29
I understand. Well, my issue doesn't seem to be a user oversight of any sort. I'll see if I can get something going with the ticket and let you know.

SIGNATURE
*Follow this thread for possible bug resolution: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1030444](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1030444)*

---

### Post by digitalattorney on 2012-08-01
Beautiful news... Starting yesterday my balloons began to take their correct shades. I wanted to wait a day before I reported the good news... As of today, they still work.

There were some Ubuntu updates that I was automatically notified of yesterday and then proceeded to download. I'm not sure which one fixed the problem, but here's the list of changes:

[IMG]http://ubuntuone.com/6QJnAeVL8ntPIzIlRr3l4W[/IMG]

God bless,
DA

---

