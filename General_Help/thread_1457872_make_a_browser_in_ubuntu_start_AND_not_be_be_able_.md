---
title: "make a browser in ubuntu start AND not be be able to be closed by the user"
date: 2010-04-19
forum: General Help
---

### Post by youaremoo on 2010-04-19
make a program in ubuntu start AND not be be able to be closed by the user

I wanna have  browser window always open at all times that cannot be closed by the user is that possible?

---

### Post by loell on 2010-04-19
that would be a browser in kiosk mode

[http://www.google.com.ph/search?sourceid=chrome&ie=UTF-8&q=firefox+kiosk+mode](http://www.google.com.ph/search?sourceid=chrome&ie=UTF-8&q=firefox+kiosk+mode)

---

### Post by youaremoo on 2010-04-19
> **loell said:**
> that would a browser in kiosk mode

[http://www.google.com.ph/search?sourceid=chrome&ie=UTF-8&q=firefox+kiosk+mode](http://www.google.com.ph/search?sourceid=chrome&ie=UTF-8&q=firefox+kiosk+mode)

but it would make firfox fullscreen ?, I just want it to be open but the user cannot close the browser window.

---

### Post by akakingess on 2010-04-19
Yeah, it looks like the Kiosk option would keep it full screen, could you possibly use a cron job script to start it up in a different "workspace" that maybe the user couldn't access or wouldn't notice. Other than that, i am not aware of anything off of the top of my head, but if I were you, I would try the Firefox help support site and post that same question, someone there may know of some custom built plug-in that we may not know of. I am pretty sure their response time is pretty quick. Good luck and sorry I couldn't be of more assistance ;)

Just thought of something, I guess you could use the 'kiosk' option, but just make it open into a different workspace, that way the user could use workspace 1 while Firefox is open fullscreen in workspace 2? Just a thought I had at the last minute, not quite sure how to do it though, I will try to look into it.

---

### Post by cong06 on 2010-04-19
Another (complex) solution would be to have your computer check to see if the browser is closed every... minute? and if it is, then it could open it.

Though I'm not quite sure how you'd send a cron task to a X interface, someone else might know.

---

### Post by Jguy on 2010-04-19
Couldn't you set a cronjob to start firefox on login under the root user? Thoeretically, the user (assuming they are not in sudoers) wouldn't be able to close a program opened under the root users (of course, you'd probably lose the ability to run java or flash applications in the firefox session).

---

### Post by blur xc on 2010-04-19
> **Jguy said:**
> Couldn't you set a cronjob to start firefox on login under the root user? Thoeretically, the user (assuming they are not in sudoers) wouldn't be able to close a program opened under the root users (of course, you'd probably lose the ability to run java or flash applications in the firefox session).

Running a browser as root sounds like a bad idea to me-  I don't know much about browsers or security- but it just sounds bad...

BM

---

### Post by cong06 on 2010-04-20
> **blur xc said:**
> Running a browser as root sounds like a bad idea to me-  I don't know much about browsers or security- but it just sounds bad...

I agree.

Also, what you (Jguy) are suggesting is a "/etc/rc.local" change.
I'm fairly certain that /etc/rc.local gets loaded before X, which means firefox would fail since there's no graphics to load it into.

If you want to make a "startup" (via system > preferences > startup) and added "gksudo firefox" I think it still wouldn't work. Just like you can close nautlius when it's run as root, I imagine that any one who can click the "x" is interpreted by firefox as being root. *shrug*

However, if you managed to figure out how to open up programs as a specific user, into a specific X session, I would like to know (out of curiosity).

---

### Post by prodigy_ on 2010-04-20
> **youaremoo said:**
> just want it to be open but the user cannot close the browser window.
May I inquire as to what you are trying to achieve? Because this is a very peculiar wish. (FF remembers all its tabs anyway, so how closing it could be a problem?)

---

### Post by d3v1150m471c on 2010-04-20
unclosable until someone opens tty

---

### Post by Portmanteaufu on 2010-04-20
> **prodigy_ said:**
> May I inquire as to what you are trying to achieve? Because this is a very peculiar wish. (FF remembers all its tabs anyway, so how closing it could be a problem?)

+1. Could you describe what you want as an end result? It's possible that we could help you think of a simpler alternate approach.

---

