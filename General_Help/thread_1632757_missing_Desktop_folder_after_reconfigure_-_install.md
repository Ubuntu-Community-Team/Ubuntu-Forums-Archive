---
title: "missing Desktop folder after reconfigure - install"
date: 2010-11-28
forum: General Help
---

### Post by candtalan on 2010-11-28
I upgraded a friends PC to 10.10 after reconfiguring his HD so that his /home is now on a separate partition. This meant some work of course, but it all seemed to go ok,  and the new install was done under a new username.

I think I have the permissions sorted..... however -

I see that when logged in as him (normal user), the Places Home folder does not open, I just see a waiting circle.

Looking more closely now I notice that the normaluser account does not appear to include a Desktop folder. A bit strange, but even with a gksu nautilus function , I see no Desktop folder for normaluser. I can create a tempuser ok, and sure enough, I then can see a desktop folder for tempuser.

So maybe somehow in my clever work here, I have gone wrong somehow.

When logging in to normaluser, the view of the desktop, icons etc, all look normal though.

This may be something to do with permissions or ownership maybe?

From the tempuser account, I have used
sudo chown -R normaluser:normaluser /home/normaluser
but of course, I guess it will not create a missing desktop folder...

Could it be that a Desktop exists but some how the /home/normaluser/Desktop folder cannot be seen?
I would be grateful for some comments here..
tia

---

### Post by candtalan on 2010-11-28
Although nautilus will not start from the top menu
Places>Home folder
it will start ok from a terminal as user, with simply
nautilus
and I actually see the several items listed which do also appear on the user desktop display.

So I conclude thus far that the nautilus side pane contains the Desktop folder and current contents, but this folder is not shown in the main display pane. And of course, the obvious  problem of Places>Home folder
not starting nautilus.... 
Any ideas please?
tia

edit:
Looking at the backups of the home contents taken before upgrading, I see that the Desktop folder seems to be missing there anyway. Although I am sure nautilus links worked ok. So my upgrade work did not apparently cause this problem  (?) but what did? and how do I recover the situation??

---

### Post by candtalan on 2010-11-28
I have noticed something significant.
The Desktop folder is seen in the side pane, as mentioned above. However, when viewed, its location is shown as being inside the Documents folder!
I believe that a careless sweep of the mouse could relocate the folder, I have just tried this on a test user account I have here. And it can also be dragged back into place. But in my test here, it did not prevent the 
Places>Home folder
opening up when requested.
So I am still looking and wondering....

---

