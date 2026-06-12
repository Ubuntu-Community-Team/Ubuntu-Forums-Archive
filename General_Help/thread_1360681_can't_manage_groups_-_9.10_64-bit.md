---
title: "can't manage groups - 9.10 64-bit"
date: 2009-12-21
forum: General Help
---

### Post by reiki on 2009-12-21
I believe this WAS working... but now I go to Users and Groups, click the button to allow changes and I get the password dialogue. enter password, click Authenticate and..... nothing. The dialogue stays and the Authenticate button is still there but no text area to enter password.

If I close the box, the "keys" show up in the notification area indicating I'm authenticated, but clicking on Manage Groups brings up a blank list. No groups in it.

WTF?

Anyone got any ideas? I'm new to 64-bit. New computer (Dell Zino HD) with 8GB of memory so I won't go back to 32-bit at this point. I'd just like Ubuntu to be its old reliable self. :)

---

### Post by Leppie on 2009-12-21
not sure about the symptons you're having, but for me the users and groups applet has never really done what i wanted it to do. i'm managing those things from the cli, it always works ;)

---

### Post by dearingj on 2009-12-21
Try opening a terminal and entering "sudo users-admin". That should, if it works, start Users and Groups with administrative privileges (in other words, already authenticated). If it doesn't work, then please copy & paste any output from the terminal into this thread.

---

### Post by reiki on 2009-12-21
> **dearingj said:**
> Try opening a terminal and entering "sudo users-admin". That should, if it works, start Users and Groups with administrative privileges (in other words, already authenticated). If it doesn't work, then please copy & paste any output from the terminal into this thread.

I'm at work now and not at the Ubuntu machine, but I did try from a terminal running sudo users-admin, also tried gksudo users-admin. Both of those had the same result. I get into the users-admin app and I am apparently authenticated as there were no errors. However when I try to "Manage Groups", it opens, and the list is empty. I don't get a list that's greyed out. I get the dialogue open with no groups in it at all.

This WAS working earlier because I had to add myself to the vboxusers group and it worked for that.

And yes, I can do this stuff from command line, but if the tools are there, they should work :)

---

### Post by reiki on 2009-12-23
bump
If you look through this forum there are several authentication issues in Karmix. I'm wondering if they're all related. 

I still have not solved this.

---

