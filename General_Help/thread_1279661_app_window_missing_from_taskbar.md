---
title: "app window missing from taskbar"
date: 2009-10-01
forum: General Help
---

### Post by makaveli789 on 2009-10-01
Hi guys,

I am running 9.04 and every now and then I notice that an application window has disappeared from my Ubuntu taskbar (at the bottom of my screen). If it is relevant, I have compiz effects turned, have a dual monitor setup, and in total two virtual screens.

Any info on why this happens, how to prevent it, or how to make the windows reappear would definitely help.

---

### Post by credobyte on 2009-10-01
Right click on your panel / Add to panel / Window list

---

### Post by sabre2th on 2009-10-01
Are you switching back and forth between the workspaces (I assume this is what you mean by virtual screens)?  By default, the window list only shows apps on your current workspace.

I'm not sure what else would make them disappear unless they're being closed.

---

### Post by makaveli789 on 2009-10-01
> **credobyte said:**
> Right click on your panel / Add to panel / Window list
Not only did that add an additional window list into that panel, it made a number of other windows disappear from the panel too!

---

### Post by makaveli789 on 2009-10-01
> **sabre2th said:**
> Are you switching back and forth between the workspaces (I assume this is what you mean by virtual screens)?  By default, the window list only shows apps on your current workspace.

I'm not sure what else would make them disappear unless they're being closed.

Yes, I do switch back and forth between the workspaces (was using the Windows term of 'virtual' desktop :)). I'm not certain if this is what could be causing it as I just tried **credobyte**'s suggestion and it made it worse - a bunch of my other windows have just disappeared.

However, after a bit of experimenting I notice that they come back into the window list panel if I drag the window from my second screen into my first screen; this is whilst inside my dual monitor setup and not from the 2nd workspace. 

Does this provide any clues as to what could be causing it?

 (BTW, I know about each workspace only showing windows that belong to it).

---

### Post by sabre2th on 2009-10-01
Oh... I didn't realize you had two monitors.  It seems logical that the dual monitor setup would be the culprit.  How are they configured?

I've used dual monitors for years and I've never seen anything like what you're describing.  Ever since the nvidia control panel has worked correctly, I've used that without issue.  Before that, configuring things was sometimes hairy, but windows never disappeared on me  :confused:

Edit: I didn't mean to imply you didn't know what you were talking about.  I've just found it's better to ask and double check terminology than to potentially spend hours trying solutions that are unrelated to the problem  :)

---

### Post by makaveli789 on 2009-10-01
> **sabre2th said:**
> Edit: I didn't mean to imply you didn't know what you were talking about.  I've just found it's better to ask and double check terminology than to potentially spend hours trying solutions that are unrelated to the problem  :)
Apologies, rereading my 'BTW' bit of my last message implies that i took offence - I can assure you that wasnt the case. I realised you wanted to rule that out right from the get-go and I just wanted to assure you that part is ok - just was a bit hastey to respond to it :).

I'll check my dual monitor config now for anything unusual and/or try to describe the setup. Is there anything in particular yuo need me to check?

---

### Post by sabre2th on 2009-10-01
> **makaveli789 said:**
>  Apologies, rereading my 'BTW' bit of my last message implies that i took offence - I can assure you that wasnt the case. I realised you wanted to rule that out right from the get-go and I just wanted to assure you that part is ok - just was a bit hastey to respond to it :).
No need to apologize.  Just me being overly cautious again  :)


> I'll check my dual monitor config now for anything unusual and/or try to describe the setup. Is there anything in particular yuo need me to check?I just wanted to know how you configured your dual monitor setup. Did you use the nvidia controls or some other utility? Manual edit of config, etc?

To be honest, I'm not sure what I'm looking for beyond that.  It's a new problem to me and it seems like the place to start.

---

### Post by makaveli789 on 2009-10-01
I have an nvidia card and using nvidia driver version 185.18.36. In the 'X Server Display Configuration' I've got my "Configuration" parameter set to 'TwinView'. Left screen has position set to Absolute +0+0. Right screen has position Absolute +1280+0.

EDIT: Should the configuration be set to 'Separate X screen' or do you think I have it set right? Don't want to try it right now as it requires a restart of X.

---

### Post by makaveli789 on 2009-10-01
I was playing around with the Window List panel thing and I think I fixed it. It seems that if you have more than one Window List panel added to your taskbar panel thing, then the windows on your second screen disappear.

Now here is the dodgey bit... what I thought was a separator in the taskbar was actually an extra Window List panel resized to the absolute minimum. Therefore, I could only see the separator like anchor, and I thoguht this was placed by default by Ubuntu to separate the workspaces view from the Window List panel item. I removed this and now all the windows are back.

Hope thats clear and that I've managed to not get myself mixed up lol.

I'll see how this goes now. If I don't get anymore windows disappearing then this was the problem. Otherwise I will come back to continue this thread.

---

### Post by sabre2th on 2009-10-01
That's odd... I'll have to look at that when I get home.

As for the configuration... If it looks and acts the way you want it to, then you have it right.  The nvidia control panel is pretty good nowadays.

Anyway, I'm glad to see you figured it out.

---

### Post by makaveli789 on 2009-10-02
Actually, the problem is still there. But I think it may be isolated to one particular app - IntelliJ. The window was on the main (primary) display but it went missing for some reason. Couldn't reproduce it for now. But in the past I always noticed that it was IntelliJ disappearing from my taskbar.


I'll try to observe it more to see what I can find. But so far I think the IntelliJ port on Linux is a bit crappy, so if it is just that I won't care to find a fix.

---

### Post by makaveli789 on 2009-10-07
So far it has been the IntelliJ windows that are disappearing. Seems to be related to switching between my Workspaces (virtual desktops). Will report it to IntelliJ as a bug but is no longer a big issue as it is just isolated to this application and I can bring it back by minimising the window and restoring it.

---

### Post by eyrieowl on 2010-12-13
Did you ever figure out what causes this?  I also notice it with IntelliJ, but I'm not at all certain it's their fault...seems more likely that it's either a Java/WindowList interaction, or 'single application with multiple windows'/WindowList interaction issue.  Or a combo of the two.

---

