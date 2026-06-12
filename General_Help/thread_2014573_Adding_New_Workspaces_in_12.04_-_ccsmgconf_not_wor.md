---
title: "Adding New Workspaces in 12.04 - ccsm/gconf not working"
date: 2012-07-02
forum: General Help
---

### Post by DiagonalArg on 2012-07-02
Hi all!

I've read around and see that using ccsm>>general>>desktop size should allow  me to set the number of desktops (workspaces).  I have changed horizontal to "3" and left vertical at "2".  I then checked in gconf editor >> apps >> compiz-1 >> general  >> screen0 >> options, and I see that after some time, hsize changed to 3 and vsize stayed at 2.  Despite this, I still only have a 2x2 matrix of screens.  Rebooting doesn't help.  

Does anyone have thoughts? 

Thanks!
/DA

---

### Post by ajgreeny on 2012-07-02
Excuse the question, but is compiz actually running, or are you using unity2D?

---

### Post by DiagonalArg on 2012-07-02
Don't excuse the question, it's entirely appropriate ... 

I don't know!

ps ux | grep compiz doesn't produce anything, so maybe not.

I'm running a server as a desktop, and it has a very old PCI graphics card, so if 3D takes a great deal in graphics resources, then I probably can't run it.  If that is the case, is there some way to get more workspaces without it?  That used to be the case.

Thanks for your input -
/DA

---

### Post by DiagonalArg on 2012-07-02
Ok, I found the answer!  Here it is:
[http://askubuntu.com/questions/21755/how-to-add-multiple-workspaces-in-unity-2d](http://askubuntu.com/questions/21755/how-to-add-multiple-workspaces-in-unity-2d)

Thanks for the help!
/DA

---

### Post by DiagonalArg on 2012-07-02
[Delete Repeat Post]

---

