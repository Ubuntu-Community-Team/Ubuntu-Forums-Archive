---
title: "login as root"
date: 2009-10-31
forum: General Help
---

### Post by dvdljns on 2009-10-31
How do i get a root login. I changed it in system/admin/login but I get an error about no gdm home dir using /home insead 
Anybody know how to fix this.

---

### Post by sisco311 on 2009-10-31
You shouldn't log in as root in the GUI. Use sudo/gksu and policykit.  

Anyway, why are you trying to login as root?

See: [uhelp]community/RootSudo[/uhelp]

and [thread=716201]Forum policy on log-in-as-root tutorials[/thread]

---

### Post by yester64 on 2009-10-31
> **sisco311 said:**
> You shouldn't log in as root in the GUI. Use sudo/gksu and policykit.  

Anyway, why are you trying to login as root?

See: [uhelp]community/RootSudo[/uhelp]

and [thread=716201]Forum policy on log-in-as-root tutorials[/thread]

lol, i like your avatar.

well, i solved it because i found the site which wasnt even ubuntu forum.
The main thing was to do certain steps as root without using the shell. I had problem with my drives which i wasnt able to mount.
But i solved it.

Here, just if you interessted, is the link of that what i was seeking.
[http://www.psychocats.net/ubuntucat/rootlauncher/](http://www.psychocats.net/ubuntucat/rootlauncher/)

i appreciate your reply. :popcorn:

---

### Post by dvdljns on 2009-11-01
> **sisco311 said:**
> You shouldn't log in as root in the GUI. Use sudo/gksu and policykit.  


That is a useless feature. It turns a gui system into a command line. At one time everyone was up in arms over the claim microsoft microsoft was trying to tell them they could not uninstall there ie browser and now I have ubuntu telling me I can not login as root.

Anyway, why are you trying to login as root?

Now Users need permission from you to admin their system. The implication of that question is that you will not help unless their answer meets your beliefs.

There are a lot of reasons to login as root. Unless you are a linux expert you need the xwindow system. More and more I see this happening not only this forum but in the linux community.
Instead of answering the users question I see people telling them why they should not do that. Or to upgrade to the newest version. I have a version of ubuntu loaded now on a computor that does not meet minimal specs because thats my best chance of getting help. Their is more doc pages wrote on just about any linux flavor you want to run, Yet it is the poorest documented os out there. I can find answers to OS2 problems easier than I can linux. Sorry about the rant and the admins will probly remove it but I needed to put in my 2 cents.

See: [uhelp]community/RootSudo[/uhelp]

and [thread=716201]Forum policy on log-in-as-root tutorials[/thread][/QUOTE]

---

### Post by WorLord on 2009-11-01
> **dvdljns said:**
> and now I have ubuntu telling me I can not login as root.

No one is telling you you "can't".  Just that you really, really shouldn't... and that we can't tell you how to do so here anyway.


> **dvdljns said:**
> Now Users need permission from you to admin their system.

More like, you don't need to *be* root to admin an Ubuntu system.


> **dvdljns said:**
> The implication of that question is that you will not help unless their answer meets your beliefs.  There are a lot of reasons to login as root. 

Enlighten me, please: exactly which task were you thinking of that simply cannot be accomplished without logging in as root?


> **dvdljns said:**
> Instead of answering the users question I see people telling them why they should not do that.

People have that perogative.  If I believe you are trying to so something that can more easily and safely be accomplished another way, I'm going to tell you so.  Further, I likely won't know how to do it the other way if I'm using alternate methods.  


> **dvdljns said:**
> Or to upgrade to the newest version.

Also a very legitimate response.  If there was a bug, and its been fixed in a newer version of the software, then the only *real* answer is to upgrade.  I cannot possibly imagine why this is a problematic statement for you.

---

### Post by sisco311 on 2009-11-01
> **dvdljns said:**
> That is a useless feature. It turns a gui system into a command line.

I disagree.

> **dvdljns said:**
> ... and now I have ubuntu telling me I can not login as root.

I disagree, you can do whatever you want. 

> **dvdljns said:**
> 
Now Users need permission from you to admin their system. The implication of that question is that you will not help unless their answer meets your beliefs.

I've tried to help you.

> **dvdljns said:**
> 
There are a lot of reasons to login as root. 


I disagree.

> **dvdljns said:**
> 
Unless you are a linux expert you need the xwindow system. 


I agree, but you don't need to run your web browser as root, just few applications.


> **dvdljns said:**
> 
More and more I see this happening not only this forum but in the linux community.
Instead of answering the users question I see people telling them why they should not do that. 


We just try to help you to understand and administer your OS. 


> **dvdljns said:**
> 
Sorry about the rant and the admins will probly remove it but I needed to put in my 2 cents.


They probably will not delete your post. This is a support forum,  we try to help you.

---

### Post by yester64 on 2009-11-01
If i may join this discussion.
My aim was simply to change my graphicsdriver which i still can't change. For some reason the privileges have changed between the two versions and now i am not able to tell the system that i am the owner.
The sad thing is, that i still can't do it and i haven't found any solution to this problem.
So, personally i do not need root but i would like to adjust the system. Right now i have a Gforce GT8800 card and i am not able to use 3D features, at least not in ubuntu.
The other problem with the harddrive i solved differently without root.
For someone who worked with linux for a long time this might seem an easy problem to solve. To me it is a hurdle which i want to overcome and i am still learning.
And i do see the point of not exposing the system to much. But i wish if i select the program Admin>Hardware Drivers the system to offer me at least a validation to change the driver without working around and digging into the shell.
Perhaps i am just frustrated a little.

And, this is important, i do not complain since it is a free system and a lot of people put a lot of effort in it without pay.
Also i still have learn more about the philosophy on ubuntus part to understand why it works the way it does.

Anyway, if someone would help me to enable the other nvidia driver, that would solve already a lot.
In 9.04 i was able to that over the menu, just not anymore in 9.10. mmmm

---

