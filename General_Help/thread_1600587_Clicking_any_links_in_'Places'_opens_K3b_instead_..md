---
title: "Clicking any links in 'Places' opens K3b instead ..."
date: 2010-10-19
forum: General Help
---

### Post by David Tomic on 2010-10-19
Hi guys,

This is a bit of a weird one, and it's got me absolutely stumped!

A couple of nights ago - and completely out of the blue - I discovered that every time I click a link in the 'Places' menu, it opens up K3b [which in a CD/DVD burning program for those of you who don't know] instead of launching Nautilus.

That had me scratching my head a little bit, so I uninstalled [and purged] the K3b package, and everything went back to normal again.

The links opened up properly in Nautilus, and everything was doing what it should.

As soon as I reinstalled K3b though, the exact same problem started happening again.

Beyond that, I'm really not sure where to begin with troubleshooting/fixing this problem, so I'm keen to hear if you guys have any ideas/suggestions on how to fix this.

FWIW I'm running Ubuntu 10.10 x64, with all the latest updates applied at time of posting.


EDIT: Just to add that [permanently] uninstalling K3b isn't really a solution for me.  I use it pretty regularly, and - for what I need to do - it's the best DVD burning program that I've found on Ubuntu!

---

### Post by yetiman64 on 2010-10-19
Just to check your default for opening a folder (with k3b installed), in terminal use,
```
cat /usr/share/applications/defaults.list | grep inode
```It should come back as,
> inode/directory=nautilus-folder-handler.desktop, however in your case it may come back as something like k3b.desktop and need to be changed. If it needs to be changed to nautilus use,
```
gksudo gedit /usr/share/applications/defaults.list
``` and replace the k3b entry with the nautilus entry above.

---

### Post by David Tomic on 2010-10-19
> **yetiman64 said:**
> Just to check your default for opening a folder (with k3b installed), in terminal use,
```
cat /usr/share/applications/defaults.list | grep inode
```

That returns the correct output, exactly as you've listed it below.


>  If it needs to be changed to nautilus use,
```
gksudo gedit /usr/share/applications/defaults.list
``` and replace the k3b entry with the nautilus entry above.

Thanks a lot for the suggestion, but it doesn't look like that's the solution to my problem.

Any other ideas?

---

### Post by yetiman64 on 2010-10-19
> **David Tomic said:**
> That returns the correct output, exactly as you've listed it below.




Thanks a lot for the suggestion, but it doesn't look like that's the solution to my problem.

Any other ideas?
Other places to look for similar entries regarding the nautilus entry (which now I remember can override the location I first gave you)  are ~/.local/share/applications/mimeapps.list and  ~/.local/share/applications/mimeinfo.cache. ~ represents your /home/<yourusername> folder.

These locations being in your home folder **don't** need to be edited with sudo (just right click and open with gedit). The period (.) before "local" indicates a hidden folder. Use CTRL + H in your home folder to expose it. Have a look for an entry with "inode" in both those locations. There is a search button on the toolbar if these files have a lot of entries. If there isn't an entry in either that is causing the problem, I too would be baffled. Good luck.

---

### Post by David Tomic on 2010-10-19
Excellent ... that one did the trick!

Just FYI the path was slightly different on my system:

~/.local/share/applications/mimeapps.list

IE: No /usr/ folder.

Thanks a lot for your help!

--David

---

### Post by yetiman64 on 2010-10-19
oops, you're right I was still thinking of the original path while giving the home path. You got it right though (-:
I'll fix those paths in my earlier posts for others viewing, thanks.

---

### Post by mc4man on 2010-10-19
Until it's decided to fix this,(3 months now in Maverick),  when using the r. click 'open with -> other application' on folders one should make sure the "Remember this application for "folder" files" is unchecked or the app chosen will become the new default folder handler.

---

### Post by bouncingwilf on 2010-10-19
Many thanks - You've also solved my Query of 1st August where installing asunder had a similar effect. I searched high and low for the link and even searched the entire HD for the rogue reference to asunder but without success.

---

### Post by ravikaigakar on 2011-01-01
Dear yetiman64 
    Thanks a lot for the suggestion,
   :guitar: WISH YOU HAPPY NEW YEAR 2011 :guitar:
               RAVI

---

