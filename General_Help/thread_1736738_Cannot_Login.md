---
title: "Cannot Login"
date: 2011-04-22
forum: General Help
---

### Post by zdeuyo on 2011-04-22
Hello Forum,

_1st Problem:_

The problem that I am having is for Ubuntu 10.10. When logging in for some reason it will:

1. Login and play the Ubuntu login sound.
2. Will start loading the desktop and panels.

Right after #2 it goes black and kicks back to the login screen. I am not sure what to do since it constantly does this. It renders the computer useless if I cannot get passed the login page. Yes the username and password are correct.

_2nd Problem:_

Before this 1st problem occurred this has also been a problem that has **not** went away.

When I used to be able to login to the desktop I have just the panel on the top of the screen with the traditional Ubuntu "start menu", "system", etc. For some reason the right side which is the other half of the panel will not load. The only solution which fixes it while I am on the current session is to right click the panel and click Minimize/Expand button which toggles to center the panel on the top of the screen. Now when I click Expand its like the problem never happend, but this only fixes it for that session.

**

Any help on these two problems is much appreciated.


Thanks,


zdeuyo

---

### Post by sanguinoso on 2011-04-22
Does the problem occur if you log in to a terminal session? Click on your username on the login screen and before you enter your password select terminal or xterm (I can't remember which) and then type your password. You should be dropped to a terminal prompt and post back here if you get kicked to the login screen again.

---

### Post by zdeuyo on 2011-04-22
Hello,

Thanks for you expedited reply.

Here are the results for the following modes.

_Editions within Ubuntu OS_

1. **Ubuntu Desktop Edition:**

A: This one defaults to login screen.

2. R**ecovery Console**

A: Have not tried

3. **Ubuntu Desktop Edition (Safe Mode)**

A: On this edition it does not kick me back to login and it also allows me to surf the web.

4. **User defined session**

A: Have not tried

**

Any suggestions?

---

### Post by sanguinoso on 2011-04-22
I mean on the login screen. When you click on your user name there should be a dropdown menu at the bottom that says Sessions: next to it. Select xterm from that menu and try to login.

---

### Post by zdeuyo on 2011-04-22
Hello,

I am looking at it as I am writing this from another computer and I see an arrow the points left and on the right of the arrow the drop down shows the following items I bolded on the previous post.

---

### Post by sanguinoso on 2011-04-22
Try the recovery console.

---

### Post by zdeuyo on 2011-04-22
Hey,

"Recovery Console"

A: This goes straight to just a terminal when I login.

"Ubuntu Desktop: Recovery Mode"

A: Logs in no problem and I can surf the web. Also this fixes the panel problem.

"Ubuntu Desktop"

A: Keeps kicking me back to login screen.

**

I just tried all three.

---

### Post by sanguinoso on 2011-04-22
What video card do you have and what drivers are you using?

---

### Post by zdeuyo on 2011-04-22
Hey,

Video Card: Not sure(how do I look this up without opening tower?)
Drivers: (whatever Ubuntu install auto selected)
Ram: 1GB
CPU: AMD Athlon(TM) XP 2000+

---

### Post by BertN45 on 2011-04-22
Sometimes the problem is caused by a full disk,

---

### Post by zdeuyo on 2011-04-22
Hey,

This is true but the harddisk is not even close to full as of yet.

---

### Post by Dutch70 on 2011-04-22
To find your video card open terminal and run...
```
lspci | grep VGA
```

---

### Post by zdeuyo on 2011-04-22
Video Card: Matrox Graphics INC. MGA G550 AGP (rev 01)

---

### Post by Dutch70 on 2011-04-22
I'm not familiar with that card, but I did a google search for "Matrox Graphics INC. MGA G550 AGP ubuntu" & found this among other things that may be helpful.
[[COLOR="RoyalBlue"]https://bugzilla.redhat.com/show_bug.cgi?id=466318[/COLOR]]("https://bugzilla.redhat.com/show_bug.cgi?id=466318")

Not sure if that is helpful or not, I didn't read it.

---

### Post by zdeuyo on 2011-04-22
Hey,

Looks like they are trying to find a solution. Thanks for the information hopefully I will find a solution soon.

---

