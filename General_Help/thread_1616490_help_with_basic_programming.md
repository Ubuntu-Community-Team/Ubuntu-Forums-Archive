---
title: "help with basic programming"
date: 2010-11-08
forum: General Help
---

### Post by System_92 on 2010-11-08
Hi,

I have very little knowledge in programming, scripting and everything (only 1 semester of Python two semesters ago in college) but I would still like to bring a small modification to the Indicator Applet on the top panel in Ubuntu.

I'm using Empathy to chat, and when a new message arrives, the indicator applet (I believe it to be the source) makes a pop-up appear on the top-right of the screen. 

What I would like to do is to make it so that I can click on that pop-up to make the chat window show-up.

Can someone please guide me into how I can do this?

Thanks!

System_92

---

### Post by ean5533 on 2010-11-08
> **System_92 said:**
> Hi,

I have very little knowledge in programming, scripting and everything (only 1 semester of Python two semesters ago in college) but I would still like to bring a small modification to the Indicator Applet on the top panel in Ubuntu.

I'm using Empathy to chat, and when a new message arrives, the indicator applet (I believe it to be the source) makes a pop-up appear on the top-right of the screen. 

What I would like to do is to make it so that I can click on that pop-up to make the chat window show-up.

Can someone please guide me into how I can do this?

Thanks!

System_92

Well, I have some bad news and some worse news. First: starting with Ubuntu 9.10, a new messaging system called NotifyOSD was added. NotifyOSD has the goal of matching the philosophy of OS X's "Growl" notifications. One of the design points of NotifyOSD notifications is that they **cannot be clicked** or interacted with. The philosophy there is that notifications should be notifications only, not dialog boxes that can be interacted with. There has been plenty of reasonable debate about this philosophy, so you aren't alone if you don't agree. Anyway, the point is that if your system uses NotifyOSD (Ubuntu 9.10 and higher all use it), then you won't be able to make the change you're suggesting.

And now for the worse news. Even if you're using the older notification system from 9.04 and earlier, the change you're suggesting *still* wouldn't be that easy. I'm not saying it couldn't be done, but it would take more than just a couple minutes to code up that feature and create a patch. It could be an interesting way to get more involved in programming (if that is your goal) but no one is going to be able to pound out a quick patch on their lunch break.

**But wait, there could be good news.** The functionality you're looking for may already exist in another notification system. Unfortunately, I just don't know if it does. I also don't know how hard it would be to swap in notification systems, though my gut instinct says "not easy".

I'm not trying to kill your hopes and dreams here, I'm just telling you that I don't think it will be an easy change. **I will be very happy if someone tells me that I'm wrong.**

---

### Post by System_92 on 2010-11-08
Thank you ean5533 for your response.  I am currently running the 10.10 release so I guess I will cross my fingers for a modification of the use of NotifyOSD in future releases.  

Would posting it in the Brainstorm section of Ubuntu's website have a possible impact?

---

### Post by jesuisbenjamin on 2010-11-08
One alternative is to use something like Cairo-Dock which will provide you with a notification for your chat program. This notification being bound to the launcher icon of your chat program will function both as launcher and notification area.
It's not really what you are asking for but eventually it comes down to the same.

Hope this helps.
B.

---

### Post by ean5533 on 2010-11-09
> **System_92 said:**
> Would posting it in the Brainstorm section of Ubuntu's website have a possible impact?

Possibly, but you might want to think about exactly what idea you're going to propose. If you simply propose "make notifications clickable" or something similar, the response is (likely) going to be a resounding **NO**. This argument happened for months back when NotifyOSD was implemented, and no one wants to argue it again.

However, you might be able to propose an alternative solution. Perhaps something like, "Make it easy to swap out the active notification system", and explain that it would allow users to pick a different system that allows interactivity, etc.

---

