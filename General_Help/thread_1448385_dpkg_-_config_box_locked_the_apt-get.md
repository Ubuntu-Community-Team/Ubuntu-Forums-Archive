---
title: "dpkg - config box locked the apt-get"
date: 2010-04-06
forum: General Help
---

### Post by Eipifi on 2010-04-06
Good day everyone. I just bumped into somewhat embarassing error, and i cannot find any way to get rid of it.

I was installing postgresql-common from the ubuntu repos. The blue configuration box appeared in the terminal i was using (blue configuration tool with the red scrollbar on the right). The thing is, there is nothing i can do with this box (clicking <OK> on the bottom, keybord shortcuts, i tried everything). After a while i just rebooted the terminal and started all over again. I recieved an error "dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem." Running dpkg configure command results in resuming postgresql installation and the blue box of death. 

Now the apt-get is useless for all the users on my machine, and 1st core of my CPU is used in 100% all the time. 

How can i reset the dpkg?

---

### Post by yetiman64 on 2010-04-06
It sounds like to fix postgresql-common, is how you've already tried in terminal with

```
dpkg --configure -a
```when you get to 

> the blue box of death. Instead of trying to click with the mouse use the up and down arrows to scroll (if necessary)- I'm not sure what you mean when you say keyboard shortcuts, the left arrow should send the focus to the ok button. 
Then try either spacebar or enter to continue with the installation _when the ok button is highlighted_.

Sounds as though its worth another try. Hope this helps.

---

### Post by Eipifi on 2010-04-06
God, it was THAT easy...   :shock:  

I'm sorry for taking your time.
And, of course, thank you.

---

### Post by CLEARviewF on 2010-04-06
Of course that will help you. Mouse does not work over the "Blue box of death" (hehe, very funny, I never though It as a black karma) In fact, mouse is almost useless over gnome-terminal, so you have to use the arrows to select "OK" and then click ENTER. It is the same when you install/update Java or Flash (I do not remember clearly).
Try this command on terminal:
sudo apt-get install -f

I think that command lets you reinstall your postgresql-common and then use the arrows to select OK, then ENTER and... done!

Bye.

---

### Post by yetiman64 on 2010-04-06
> **Eipifi said:**
> God, it was THAT easy...   :shock:  

I'm sorry for taking your time.
And, of course, thank you.


You're welcome Eipifi, 

Sounds like you've had a fix to your problem. _If so,_ could you mark your thread as solved with the thread tools drop down menu at the top of your browser window? thanks. If not, just keep on posting. :).

---

