---
title: "can't seem to delete HP LIP folder from desktop.."
date: 2010-08-24
forum: General Help
---

### Post by lue42x on 2010-08-24
I get these messages when I try to delete a folder left by the HP LIP (Hewlett Packard Linux Imaging and Printing program) driver/program ... is it possible to get rid of it or move it elsewhere?

pic of folder
[http://img827.imageshack.us/img827/4076/screenshot2vc.png](http://img827.imageshack.us/img827/4076/screenshot2vc.png)

attempt to delete:
[http://img827.imageshack.us/img827/4076/screenshot2vc.png](http://img827.imageshack.us/img827/4076/screenshot2vc.png)

after clicking "delete":
[http://img821.imageshack.us/img821/7426/screenshot3ex.png](http://img821.imageshack.us/img821/7426/screenshot3ex.png)

---

### Post by Silent Warrior on 2010-08-24
The problem is permissions. My guess is that the folder has been assigned to your root - right-click and opening Properties and checking the Permissions-tab will tell you more - and you're trying to delete it as your normal user. Which obviously isn't working because this is Linux and not Windows. :)

What I do when I get into these situations: *SNIP*, navigate to the problem folder, go into Properties and change, in Permissions, the folder's owner to my normal user. Apply, exit Nautilus, delete the folder. Or I just bypass all that and use Shift-delete, but since this risks leaving a root-owned folder in your Trash, I suggest you go to the trouble of monkeying around with Permissions.

---

### Post by Irony on 2010-08-24
No! Do;

```
gksudo nautilus
```

Then shift-delete the offending folder - use gksudo for graphical applications.

---

### Post by lue42x on 2010-08-24
Hi guys

I tried the gksudo nautilus first, and held shift when i pressed the "Del" button and the same thing happened (error message stating that I do not have permissions required to delete that folder).  

I also tried the sudo nautlus to navigate to the folder to try to delete it that way, but when i did sudo nautilus, my desktop folder appeared completely empty (it is not actually empty at this time) and I could not see the hplip-3.10.6 folder

Any advice?

---

### Post by Chris1274 on 2010-08-24
Close your current X session and open up a new one as root. You'll be able to manage any and all files.

---

### Post by lue42x on 2010-08-24
I'm glad to hear there is a way to fix this!  I'm not sure of how to close the current X session and open a new one as Root ... could you please describe the process?

---

### Post by Silent Warrior on 2010-08-26
It's possible he/she/it meant logging in as root, in which case you log out normally, then log in with root as username (and using the password you enter for sudo/gksu/gksudo).
As for the Desktop appearing empty when using sudo nautilus, I have a feeling you're actually looking at root's Desktop, not your own. If you get the urge to try it again (against Irony's recommendation), navigate to /home/your-name-here/Desktop, manually-like, and you should have more to look at.

---

### Post by Irony on 2010-08-26
> **lue42x said:**
> my desktop folder appeared completely empty (it is not actually empty at this time) and I could not see the hplip-3.10.6 folder.
```
gksudo nautilus
```
Then shift-delete the offending folder - use gksudo for graphical applications.

Make sure you navigate to home > your desktop - not to root > desktop.

---

### Post by lue42x on 2010-08-26
you guys were right!  I was looking at the desktop in the Root folder - when I navigated to Home it was all there.  Thanks for your help I really appreciate it!

---

### Post by Bramkaandorp on 2011-03-23
At risk of being reprimanded for necromancing:

I have the folder on the desktop, which was put there by the installation.

Is it at all safe to remove the folder, or are some programs dependent on the folder being there?

It wasn't all that clear to me.

Cheers

---

### Post by Silent Warrior on 2011-03-23
It SHOULD be safe to remove. Just put it in the Trash first, see if everything still works (i.e. find something to print). If so, you're free to delete it permanently, as far as I understand.

---

### Post by Bramkaandorp on 2011-03-24
I'll if it has any effect.

Thans for the reply.

Cheers

---

### Post by Bramkaandorp on 2011-03-27
I had some problems with the scanner after removing the folder from the desktop.

I don't know whether the one caused the other though.

I also configured the HP Device Manager would only show in the notification area when it's active. Could this be the cause, rather than removing the folder from the desktop?

Cheers

---

### Post by Silent Warrior on 2011-03-27
That depends. What problems are you having? As for the 'show only when active'-option, the way to find out if that's the cause is, of course, to turn off this option and see if that helps.

---

### Post by Bramkaandorp on 2011-03-28
> **Silent Warrior said:**
> That depends. What problems are you having? As for the 'show only when active'-option, the way to find out if that's the cause is, of course, to turn off this option and see if that helps.

Well, I couldn't start the program, so I couldn't undo my action.

I have simply reinstalled everything (there was an update in the intervening time, so I installed that), and everything works fine.

I'll try removing the folder from the desktop one more time now (the second time), and if that screws everything up, I will know that I must keep the folder there.

Of course, I will put the folder on an external drive, just in case.

---

### Post by Bramkaandorp on 2011-03-29
Well, everything is running great!

So to anyone doubting whether they should remove the folder: I can't see a reason for keeping it.

Cheers

---

