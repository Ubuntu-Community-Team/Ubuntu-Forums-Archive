---
title: "ubuntu just killed itself"
date: 2011-11-14
forum: General Help
---

### Post by orrymr on 2011-11-14
I really have no other way to explain this.
I upgraded 11.04 to 11.10. I decided to give unity a shot and instill compiz, to enable all the fanciness.
After I did, everything just went wrong. The dash disappeared, and I couldn't even launch it with a keyboard shortcut. I couldn't open/close windows, since the close window option only appears at the top of the screen on unity, which was no longer there. All the stuff on my desktop disappeared. I had to manually reboot, and when I did, everything was still, well, screwed. So I manually rebooted again, changed back to Gnome, but now things are just weird. My mouse jerks, things sometimes take long to open, and all the stuff on my desktop is still gone :(. The stuff in my home folder is still there though. Thankfully I backed up not too long ago. I never had compiz on 11.04, mainly because I didn't care, but when I had it with 10.10, it worked just fine.

Oh yeah, and the <snip> cube doesn't work. Anyway, not really looking for any help, just sort of having a mini-rant. I'm probably going to move to another distro or go back to 10.10 (which is the only version of Ubuntu I've never had problems with) or just start using my (sigh) proprietary operating system partition more. 

:frown:

---

### Post by linuxuser12345 on 2011-11-14
I had the same problem. What you are going to have to do is log into a different GUI then create yourself a new account and transfer everything over. Once I did that, your problem should be fixed.

---

### Post by orrymr on 2011-11-14
You mean, transfer my entire home folder?

---

### Post by whitethorn on 2011-11-14
> **linuxuser12345 said:**
> I had the same problem. What you are going to have to do is log into a different GUI then create yourself a new account and transfer everything over. Once I did that, your problem should be fixed.

Not really much of a fix, with transfer everything over did you mean all the /home/$USER/.* files as well or just the normal folders?  Creating an new user is kindof overkill. I think the better way would be to find what's wrong and just fix that instead of setting up a new user. 

I think it's just a settings problem, and according to the author seems like it has something to do with compiz. I would suggest moving the .compiz folder to .compiz.bak and then restart compiz and set it up again and see what happens.

---

### Post by mastablasta on 2011-11-14
the problem is that compiz and unity don't mix. you could try to uninstall compiz and install unity

---

### Post by Hylas de Niall on 2011-11-14
Unity is just a compiz plugin anyway, isn't it?

---

### Post by orrymr on 2011-11-16
Any ideas as to what happened to the stuff on my desktop though?
Also, how would I undo all the changes that have been made?

---

