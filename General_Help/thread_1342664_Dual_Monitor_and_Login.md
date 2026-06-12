---
title: "Dual Monitor and Login"
date: 2009-12-01
forum: General Help
---

### Post by dln9 on 2009-12-01
I have 9.10, and I have two monitors set up.  How do I control which monitor the login window appears on?  It always wants to appear in the less desirable monitor - the one we usually leave turned off.  I don't know how to change that.  

dln9

---

### Post by fluffman86 on 2009-12-01
Look for an option to change your primary monitor.  Should just be a checkbox there.

---

### Post by scouser73 on 2009-12-01
You'll need to do this as root, so follow these instructions.

**1** - Paste this command into terminal: **gksudo nvidia-settings**

**2** - Click on **X Server Display Configuration**

**3** - Click on the monitor that you wish the login screen to appear

**4** - Check the box stating **Make This The Primary Display For The X Screen**

**5** - Click **Apply**

**6** - Click **Save To X Configuration File** & press **Quit**

***You have now set the login screen to appear on your desired monitor, this will be your main monitor, to change it, just follow the instructions again but this time choosing the other monitor.***

---

### Post by dln9 on 2009-12-01
Thanks for the replies.  

fluffman86 - I don't understand your suggestion.  I have been searching in vain for such an option - I guess you could say that is precisely what I am asking:  Where do I find that option?  

scouser73 - I had already done exactly what you suggested.  Our "preferred" monitor behaves as the main monitor, based on these settings, which is what we want - EXCEPT in this one situation, which is when we're confronted with the login screen.  Then it always wants to appear in our secondary monitor.  I don't know what else to mess with.

---

### Post by dln9 on 2010-02-24
I'm hoping someone who knows how to fix this problem will see this.  It is very strange that the monitor we have set as our secondary monitor is always the one on which the login stuff appears.  So, we are forced to turn on the second monitor simply so we can log in.  

Any ideas, anyone?

---

