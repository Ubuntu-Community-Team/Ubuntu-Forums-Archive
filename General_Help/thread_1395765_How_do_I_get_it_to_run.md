---
title: "How do I get it to run?"
date: 2010-02-01
forum: General Help
---

### Post by buckeyefan1 on 2010-02-01
Hey guys. I'm new to the Ubuntu experience and I have a problem. I had an older version of Kubuntu and it asked me to upgrade to 9.10 which I did. After a while gathering files and installing it was ready to try it out. It came to a dos prompt and asked for my login information which I gave it. Now it is just sitting at a prompt that reads: jeff@JeffPC:~$ What do I do know? 
 
Thanks for any help.

---

### Post by lykwydchykyn on 2010-02-01
It means that X11 hasn't started.

Some part of the upgrade has messed up your graphical system.

Try logging in at the terminal and running "startx".  If you get errors, post them here.

---

### Post by buckeyefan1 on 2010-02-01
I got fatal errors. It says that: "no screens found" "xinit: No such file or directory (errno 2): unable to connect to X server" xinit: No such process (errno #): Server error."
 
Should I scrap this version and just go download the newest version?

---

### Post by buckeyefan1 on 2010-02-01
Oh and thanks so much for your quick and helpful reply.

---

### Post by lykwydchykyn on 2010-02-01
> **buckeyefan1 said:**
> I got fatal errors. It says that: "no screens found" "xinit: No such file or directory (errno 2): unable to connect to X server" xinit: No such process (errno #): Server error."
 
Should I scrap this version and just go download the newest version?

9.10 is the newest (stable) version.

The problem is probably fixable, it's a question of how much you have invested in the install and how much you're willing to do the legwork to find the problem and fix it.

What graphics card do you have?

---

### Post by buckeyefan1 on 2010-02-01
I don't have alot of time, it just takes so long to download. Verizon DSL isn't very fast or consistant here. I am running a ATI HD 2600 graphics card. Its a Gateway laptop. Here are the specs: 
 
Gateway M6864fx
Intel T5750
4gb ram
200 HD 7200
Windows 7
ATI HD 2600
 
I can't think of anything else. Thanks again.

---

### Post by lykwydchykyn on 2010-02-01
Try these commands, and let's see if this works; my suspicion is that you had the proprietary ATI driver enabled, and now it's not working for some reason.

This will default it.
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf-old
startx

```

That will start you with the default (opensource) ATI driver; if that works, you can experiment with installing the proprietary driver from the GUI.

---

### Post by buckeyefan1 on 2010-02-01
That seemed to do something that is working. I wish I understood, but thats a whole other issue. Will I have to do it everytime? thanks again for all your help.
 
Jeff the noob

---

### Post by lykwydchykyn on 2010-02-01
> **buckeyefan1 said:**
> That seemed to do something that is working. I wish I understood, but thats a whole other issue. Will I have to do it everytime? thanks again for all your help.
 
Jeff the noob

If you mean everytime you restart, no; if that got your GUI working it should work normally on reboot now.  It'll be using the open source driver, and I'm not sure where that's at with regard to 3D, hardware acceleration, etc.

If the performance seems bad you'll want to reinstall the proprietary driver.  If reinstalling the proprietary driver messes it up again, the above commands should straighten you out again.

---

### Post by buckeyefan1 on 2010-02-01
Thanks so much for all your help. Your advice did the trick. I really appreciate that.
 
Jeff

---

