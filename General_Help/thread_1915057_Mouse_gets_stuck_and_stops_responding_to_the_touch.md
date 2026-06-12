---
title: "Mouse gets stuck and stops responding to the touchpad randomly"
date: 2012-01-25
forum: General Help
---

### Post by HunterDX77M on 2012-01-25
I think the title says it all. Basically at random times over the past two days, my mouse just locks up and stops responding to the touch pad. My only option is to restart the computer and then it (the problem) comes back again at a random time. What could the issue be? This started yesterday, around the time that I applied a huge batch of updates via the Update Manager.

---

### Post by HunterDX77M on 2012-01-26
bump

---

### Post by HunterDX77M on 2012-01-27
bump

---

### Post by pretty_whistle on 2012-01-27
It could be that it's dirty, even if it doesn't look it.  Same for fingers.  A small amount of dirt can mess it up.

---

### Post by HunterDX77M on 2012-01-27
> **pretty_whistle said:**
> It could be that it's dirty, even if it doesn't look it.  Same for fingers.  A small amount of dirt can mess it up.

Hmm, might be. But I'm a germophobe and a total neat-freak. But I have isolated the issue to the touchpad only. When it froze yesterday, I plugged in my external mouse and it worked with the external mouse, but continued to be unresponsive for the touchpad.

---

### Post by timmc94 on 2012-01-27
I have the same problem. I'm running Ubuntu 11.10 on a Toshiba Satellite Laptop. If you are using 11.10 also, it may just be a glitch in the OS?

---

### Post by GraeW on 2012-01-27
I've had similar issues with my Acer laptop, but recently saw a different thread that talked about disabling the touchpad. do a search for "synclient" in the forum and you'll see the command. I disabled my touchpad completely and just use an external mouse now - no problems for the last week.
 
Yeah, I know it kinda defeats a little bit of the purpose to the laptop/touchpad but it works for me. ;)

---

### Post by HunterDX77M on 2012-01-27
> **GraeW said:**
> I've had similar issues with my Acer laptop, but recently saw a different thread that talked about disabling the touchpad. do a search for "synclient" in the forum and you'll see the command. I disabled my touchpad completely and just use an external mouse now - no problems for the last week.
 
Yeah, I know it kinda defeats a little bit of the purpose to the laptop/touchpad but it works for me. ;)

It's great that it works for you, but I sometimes need to use my laptop on the train ride home and don't have the convenience to use my external mouse.

---

### Post by HunterDX77M on 2012-01-27
> **timmc94 said:**
> I have the same problem. I'm running Ubuntu 11.10 on a Toshiba Satellite Laptop. If you are using 11.10 also, it may just be a glitch in the OS?

Possibly. I've had Oneiric since late December 2011, but have only noticed in the last week. If it was really an OS thing, it should have manifested itself earlier. Like I said in my original post, I noticed this concurrently with a large batch of updates.

---

### Post by HunterDX77M on 2012-02-02
Bump.

Somebody please help with this, it's getting to be a real inconvenience.

---

### Post by HunterDX77M on 2012-02-11
Bump.

Desperate for help here.

---

### Post by sydsverre on 2012-02-11
i think i know your problem. when your on your laptop and you have these occurances do you have something with a battery on you? i ask this because i had the same problem. i discovered that the problem was linked to my e-cigarette (yes i smoke one but lets not miss the point here) whenever it was touching me or near my laptop my mouse would get stuck and respond to my touch randomly. when i plug in an external mouse its fine. simply put electrical interference. this may not be your problem but what the hey. help is help

---

### Post by sydsverre on 2012-02-11
my fix. just put whatever is causing the interference at a safe distance

---

### Post by HunterDX77M on 2012-02-11
> **sydsverre said:**
> my fix. just put whatever is causing the interference at a safe distance

Yes I have stuff that is running on batteries when I run my laptop, but I've had them for quite a while before this problem showed up (Kindle, cell phone). This problems seems to occur anywhere (train, cafeteria, home, in class).

---

### Post by HunterDX77M on 2012-02-17
bump

---

### Post by cov on 2012-02-18
I have been having this issue since the upgrade to 11.10 and I am fed up to the back teeth.

It's alright if I have an external mouse handy and can plug it in, but otherwise repeated reboots are necessary to a working touchpad.

Is this something that is likely to be fixed in 12.04 or is it not regarded as being that important.

I had no problems with the releases prior to 11.10 and it really does burn my butt.

---

### Post by HunterDX77M on 2012-02-18
> **cov said:**
> I have been having this issue since the upgrade to 11.10 and I am fed up to the back teeth.

It's alright if I have an external mouse handy and can plug it in, but otherwise repeated reboots are necessary to a working touchpad.

Is this something that is likely to be fixed in 12.04 or is it not regarded as being that important.

I had no problems with the releases prior to 11.10 and it really does burn my butt.

You've summed up my pain with this issue 100% and word-for-word. It is absolutely unacceptable that I have to reboot at least three times a day just to get my mouse to work.

---

### Post by takeoutweight on 2012-02-22
I have the same problem.

I found just restarting the x server works, as is a bit faster than rebooting the entire machine. eg:

sudo restart lightdm

---

### Post by HunterDX77M on 2012-02-23
> **takeoutweight said:**
> I have the same problem.

I found just restarting the x server works, as is a bit faster than rebooting the entire machine. eg:

sudo restart lightdm

Hey thanks for your reply. I'm not familiar with X server. Could you please explain what that is and what that command you gave does?

Update: It works quicker than restarting . . .

---

