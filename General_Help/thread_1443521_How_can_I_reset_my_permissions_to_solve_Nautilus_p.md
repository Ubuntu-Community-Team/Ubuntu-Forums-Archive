---
title: "How can I reset my permissions to solve Nautilus problem?"
date: 2010-03-31
forum: General Help
---

### Post by Steve Francis on 2010-03-31
I am having another go at restating a File Manager problem that I posted a few weeks ago on this board. I can't seem to find a solution and would appreciate any suggestions.

_The problem:_

When I click on a folder under the Places menu or start File Manager, the File Manager window appears. When I then click on any file or folder to open it, File Manager just freezes.

I then have to force quit and receive the error message "File Manager not responding".

When I force quit my desktop items are missing!

_Some additional information:_

(a) GNOME commander works fine.

(b) If I open up Terminal and just type [FONT=Courier New]nautilus[/FONT], I get the error message
[FONT=Courier New]** (nautilus:5550): WARNING **: Unable to add monitor: Not supported[/FONT]
and then I have to force quit the file browser.

(c) I found out that nautilus does _not_ hang when I type
[FONT=Courier New]gksudo nautilus
[/FONT]
 _Solutions already attempted_

(1) I tried reinstalling Nautilus using this code:
[FONT=Courier New]sudo apt-get remove nautilus
sudo apt-get install nautilus[/FONT]
This succeeded in uninstalling and reinstalling Nautilus but the File Browser still hangs when I double click on a file within it.

(2) I thought maybe I should reset the permissions for my home folder.
Typing the following command did not solve the problem.
[FONT=Courier New]sudo chmod 700 /home/me
[/FONT]

Any ideas? Did I reset the permissions properly?

---

### Post by drinkleadsoup on 2010-03-31
Now it is happening on both my 9.1 and 10.04 machines.  Any help, anyone?

---

### Post by drinkleadsoup on 2010-04-01
Bump, anyone?  I am able to use the Thunar workaround, but I need my desktop and file manager back.  Thanks.

---

### Post by Steve Francis on 2010-04-02
drinkleadsoup - I've tried posting on another forum to see if anyone there can help:

[http://www.linuxquestions.org/questions/linux-newbie-8/how-can-i-reset-my-permissions-solve-nautilus-problem-799647/](http://www.linuxquestions.org/questions/linux-newbie-8/how-can-i-reset-my-permissions-solve-nautilus-problem-799647/)

---

### Post by gsgleason on 2010-04-02
I don't know if permissions is your problem, but you can reset the permissions on all you files with chmod -R which is recursive.

See if you have a directory like .nautilus in your home. Maybe it's borked.  Delete it.

---

### Post by Steve Francis on 2010-04-02
> **gsgleason said:**
> I don't know if permissions is your problem, but you can reset the permissions on all you files with chmod -R which is recursive.

See if you have a directory like .nautilus in your home. Maybe it's borked.  Delete it.

I deleted .nautilus and rebooted.

Problem still exists, unfortunately.

.nautilus folder has appeared again (although the permissions have changed to 755)

Perhaps it isn't a permissions issue, though, as you say.

---

### Post by drinkleadsoup on 2010-04-06
I still have no resolve to my file manager not responding.  Does anyone have a clue what might be happening here?

---

### Post by lidex on 2010-04-06
Go to a terminal:
```
 rm -r ~/.local/share/gvfs-metadata
```

---

### Post by drinkleadsoup on 2010-04-06
Thanks, but, still no dice.

---

### Post by lidex on 2010-04-06
Try logging out/in.
Also for troubleshooting run nautilus from a terminal and post output.

---

### Post by drinkleadsoup on 2010-04-06
...still the same.

---

### Post by Steve Francis on 2010-04-09
> **drinkleadsoup said:**
> ...still the same.

drinkleadsoup

Did you try my troubleshooting method? It has got file manager working for me again:
[http://www.linuxquestions.org/questions/linux-newbie-8/how-can-i-reset-my-permissions-to-solve-nautilus-problem-799647/page2.html#post3927461](http://www.linuxquestions.org/questions/linux-newbie-8/how-can-i-reset-my-permissions-to-solve-nautilus-problem-799647/page2.html#post3927461)

Essentially, create a new folder (called "problem_files" or similar) and transfer into it the files currently in your /home/drinkleadsoup/ folder. It may be one of those files that is causing the problem.

---

### Post by lidex on 2010-04-09
Open a terminal. Enter this command:
```
nautilus
```
Post the terminal output in your next post.

---

### Post by alicebtoklas on 2010-04-23
drinkleadsoup,
I had the same problem and could resolve it with the help of  [Steve Francis'post]("http://www.linuxquestions.org/questions/linux-newbie-8/how-can-i-reset-my-permissions-solve-nautilus-problem-799647/").
I moved all files (not the folders) from /home/me/ to a new folder /home/me/oldme/ , nautilus was working well again, then I moved back all these files to /home/me/ , one by one, and nautilus began to freeze again after I moved back a .svg file.
So simply removing this .svg file made nautilus work properly again.
Do you have .svg files in your /home folder? Did you already try this?

---

### Post by warfacegod on 2010-04-23
Have you tested your HDD? I ran into a somewhat similar thread, a few months ago. Turned out that the guys drive was failing. If you do test it, I don't recommend using Palimpest (labeled "Disk Utility" in the menu). It has been known to throw false positives since it was first added to Ubuntu in 9.04. Try this instead:

```
sudo apt-get install gsmartcontrol
```

---

### Post by callmeatoaster on 2010-04-25
alicebtoklas, 
Brilliant! I had the same problem with an SVG that had been saved to my home directory.  Deleted it via the terminal, rebooted and now everything is copacetic.

---

### Post by drinkleadsoup on 2010-04-25
Yep.  Having an SVG on the desktop causes the file manager to not respond.  Very odd.  Is this considered a bug?

---

### Post by alicebtoklas on 2010-05-05
I guess so!
But where should it be reported, I don't know.
A.

---

