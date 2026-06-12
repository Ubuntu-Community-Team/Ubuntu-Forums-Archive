---
title: "Syndaemon startup under karmic"
date: 2009-10-31
forum: General Help
---

### Post by bhupsi on 2009-10-31
How is syndaemon started under karmic?  I want to change the default settings.  

Thanks.

---

### Post by cariboo on 2009-10-31
It is a regular application so you can start it like a normal program. For info on switches check man syndaemon.

---

### Post by bhupsi on 2009-10-31
> **cariboo907 said:**
> It is a regular application so you can start it like a normal program. For info on switches check man syndaemon.

Ok, so I want to change the switches.  How do I do that now that syndaemon has been incorporated into karmic.  I use to use "startup applications" to start syndaemon with my customized settings.  Now I see that syndaemon is started by default under karmic with it's own standard settings that I don't like.  So how do I properly change the switches to syndaemon under karmic.  I wish the man page gave some idea of how syndaemon gets initalized under karmic.

---

### Post by lunch on 2009-11-01
[http://ubuntuforums.org/showthread.php?t=1309104#post8214973](http://ubuntuforums.org/showthread.php?t=1309104#post8214973)

---

### Post by bhupsi on 2009-11-01
> **lunch said:**
> [http://ubuntuforums.org/showthread.php?t=1309104#post8214973](http://ubuntuforums.org/showthread.php?t=1309104#post8214973)

Well thats a big fat Duh! on my part.  I didn't think about turning off the gnome startup of syndaemon under preferences-mouse-touchpad and then going back to using my startup of syndaemon under "startup applications".  That works for me.  Thanks.

---

### Post by frprovis on 2009-11-01
So far at least 2 people have had this issue, me plus the guy who started this thread. Let's assume they spent an hour or so researching syndaemon before posting. Assume the people replying spent 15 minutes each * 2 such people * 2 posts = another hour. Let's assume another 100 people will have the same problem over the next week or so as people start upgrading from 9.04 to 9.10. Then there are the newbies who don't know what is going on, but are frustrated with the .5sec timeout time (didn't work for me, probably won't work for a lot of other people either). We're talking a lot of wasted time here compared to the cost of

[SIZE=7]making the touchpad timeout time user-specifiable in the Preferences'Mouse dialog!!!!![/SIZE]

---

### Post by bhupsi on 2009-11-02
> **frprovis said:**
> So far at least 2 people have had this issue, me plus the guy who started this thread. Let's assume they spent an hour or so researching syndaemon before posting. Assume the people replying spent 15 minutes each * 2 such people * 2 posts = another hour. Let's assume another 100 people will have the same problem over the next week or so as people start upgrading from 9.04 to 9.10. Then there are the newbies who don't know what is going on, but are frustrated with the .5sec timeout time (didn't work for me, probably won't work for a lot of other people either). We're talking a lot of wasted time here compared to the cost of

[SIZE=7]making the touchpad timeout time user-specifiable in the Preferences'Mouse dialog!!!!![/SIZE]

I agree that it was very short sited of the ubuntu developers to start syndaemon by default and not give a clear way to alter the default timeout vaule.  I guarantee that most people who were already running syndaemon are not going to be happy with the startup value that they chose.

---

### Post by romwell on 2011-03-18
Bump. I am an Ubuntu newb. 

"Disable touchpad while typing" is not an option that I would ever need. Moreover, it is broken in 10.10, and unchecking it in Mouse preferences does not kill syndaemon.

It took me about a week to figure out what was going on, from my perspective the mouse was freezing after any key press. Shortcuts like Shift+Click were unusable.

In short, I don't see why this option needs to be on by default, and why the timeout setting is not there. This is a serious usability issue, and it seems like it's been ignored for at least a year now.

---

