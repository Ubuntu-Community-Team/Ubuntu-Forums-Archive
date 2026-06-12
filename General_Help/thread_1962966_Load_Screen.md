---
title: "Load Screen"
date: 2012-04-21
forum: General Help
---

### Post by xworld on 2012-04-21
I am having an absolutely stupid problem. All I did was to change a setting from ring switcher to shift switcher in ccsm. THATS ALL. Oops I forgot to turn one off before enabling the other one. So I resolve conflicts. Restart, and now every time I try to start ubuntu up it just sits there in the load screen for...well I don't know it never got past it. It just loads and loads. This is absolutely dumb. Has this happened to anyone? Can I resolve this or do I need to completely reinstall ubuntu just because of one tiny little setting change error?  Thanks

---

### Post by xworld on 2012-04-21
Would someone like to help with this problem?

---

### Post by strafe_sawdoffe on 2012-04-21
Never had this particular problem, but try this:

Boot the machine and hold down the left shift key... if left shift doesn't work use Escape. It should get you to the advanced start-up menu... you can then start Ubuntu in failsafe mode. Can you get into the OS that way?

If so, you can take another shot at resolving whatever conflict was created...

---

### Post by xworld on 2012-04-21
Eh I tried but when I started it in safe mode for some reason it automatically took me back to the login screen.

---

### Post by strafe_sawdoffe on 2012-04-21
Ouch.

Can you boot to the command line at least? If so, there's probably some file you can delete from your home folder, but what I'd actually do is create a new user account and try to boot to that. If you can log in graphically as a different user then you could copy the data over, and either continue trying to fix the first account or just scrap it.

I'll be first to admit that's a very Windows-like manner of thinking...

---

### Post by strafe_sawdoffe on 2012-04-21
Again with the boot-to-terminal idea, if it's a non-user level startup process causing the issue, you can troubleshoot that with the commands here: [http://www.upubuntu.com/2011/10/how-to-view-and-disable-hidden-startup.html](http://www.upubuntu.com/2011/10/how-to-view-and-disable-hidden-startup.html)

I'd go for anything Compiz related based on your original post.

---

