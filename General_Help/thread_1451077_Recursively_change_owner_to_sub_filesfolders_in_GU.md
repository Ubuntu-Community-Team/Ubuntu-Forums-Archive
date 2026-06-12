---
title: "Recursively change owner to sub files/folders in GUI?"
date: 2010-04-10
forum: General Help
---

### Post by Roasted on 2010-04-10
I was just in "gksudo nautilus" changing ownership of a folder on my external hard drive and I got to thinking if I could change the owner as myself to all files/folder vai GUI. I'm well aware of how to do it in terminal, but this is just a "is it even possible?" type question.

---

### Post by iponeverything on 2010-04-10
There is an option for it in when you right click on a folder to change the permissions.

---

### Post by Roasted on 2010-04-10
> **iponeverything said:**
> There is an option for it in when you right click on a folder to change the permissions.

I know you can set the owner. I want to set the owner recursively, which would change the owner to all files/folders within that parent folder I change.

---

### Post by QLee on 2010-04-10
[QUOTE=Roasted]I was just in "gksudo nautilus" changing ownership of a folder on my external hard drive and I got to thinking if I could change the owner as myself to all files/folder vai GUI. I'm well aware of how to do it in terminal, but this is just a "is it even possible?" type question.[/QUOTE]

I wonder what you mean by "all files/folders", if you mean all on your system, then that would be a bad idea and I doubt that you would really want it.

But, the answer to the question is it possible to change permisions recursively from nautilus is yes. Just as the other posted suggested right click for the context menu, choose properties and select the permissions tab.

If you need more help it might be useful for you to read the section in the Nautilus help [Menu item Help-->Help Contents (F1)] section 6.6.16 about changing permissions.

---

### Post by Roasted on 2010-04-11
> **QLee said:**
> I wonder what you mean by "all files/folders", if you mean all on your system, then that would be a bad idea and I doubt that you would really want it.

But, the answer to the question is it possible to change permisions recursively from nautilus is yes. Just as the other posted suggested right click for the context menu, choose properties and select the permissions tab.

If you need more help it might be useful for you to read the section in the Nautilus help [Menu item Help-->Help Contents (F1)] section 6.6.16 about changing permissions.

I'm not quite sure we're all on the same page here, because upon doing that, it's not fulfilling the answer to my question.

I know it's not wise to change the owner of all files/folders on the system to me. That's not what I'm trying to do. I saved a bunch of files (data recovery) on my external hard drive through an Ubuntu LiveCD. This made the owner of the files to "999" or whatever the LiveCD uses. No big deal, real easy to change. As I was changing them I was wondering if I could do this through the GUI.

The file structure was like this:

X = External Hard Drive Name
Backup Files = Parent folder of all things listed below.
Folders inside = Pictures, Music, Documents, Downloads, Desktop
Then of course in each corresponding folder was either pictures, music, etc.

When I change the ownership of "Backup Files", it DOES NOT change me as the owner of Pictures/Music/Documents/Downloads like I want it to. If I chown -R in terminal, it does. I'm curious if THAT functionality is in the GUI. Simply changing the owner in the GUI does not pass "me" as the owner to Pictures/Music/etc. That's what my question is and what I'm curious about.

---

### Post by measekite on 2010-11-23
> **Roasted said:**
> I'm not quite sure we're all on the same page here, because upon doing that, it's not fulfilling the answer to my question.

I know it's not wise to change the owner of all files/folders on the system to me. That's not what I'm trying to do. I saved a bunch of files (data recovery) on my external hard drive through an Ubuntu LiveCD. This made the owner of the files to "999" or whatever the LiveCD uses. No big deal, real easy to change. As I was changing them I was wondering if I could do this through the GUI.

The file structure was like this:

X = External Hard Drive Name
Backup Files = Parent folder of all things listed below.
Folders inside = Pictures, Music, Documents, Downloads, Desktop
Then of course in each corresponding folder was either pictures, music, etc.

When I change the ownership of "Backup Files", it DOES NOT change me as the owner of Pictures/Music/Documents/Downloads like I want it to. If I chown -R in terminal, it does. I'm curious if THAT functionality is in the GUI. Simply changing the owner in the GUI does not pass "me" as the owner to Pictures/Music/etc. That's what my question is and what I'm curious about.

I solved a similar problem recursively changing the owner and other permissions using a GUI.  I had nested folders with files in each one.  When using Nautilus in 10.10 and clicking 'apply permissions to enclosed files there were no results and there is a bug in Nautilus.  I do like Nautilus because it is easier and quicker to use for most things but not as powerful as the KDE candidate "Dolphin" and it runs find with the Gnome front end.

**Here is what I did:**
Install Dolphin using Synaptic Package manager.
Using terminal type this at the prompt.

```
gksu dolphin
```

type the administrator password.  The user account must be able to use the sudo stuff.

When Dolphin come up root will be home.  goto the home folder of where the target master folder is.  Rt click and then click on the permissions tab.  At the bottom there are two text boxes.  One for the new owner and the other for the new group.  Fill them in.  Then be sure to check the checkbox that says to apply to all sub folders and their contents.  You are now done.

It saved me a few day fo doing is manually or I would have to spend more time with the command line.  Hope this helps.

---

### Post by Roasted on 2010-11-23
> **measekite said:**
> I solved a similar problem recursively changing the owner and other permissions using a GUI.  I had nested folders with files in each one.  When using Nautilus in 10.10 and clicking 'apply permissions to enclosed files there were no results and there is a bug in Nautilus.  I do like Nautilus because it is easier and quicker to use for most things but not as powerful as the KDE candidate "Dolphin" and it runs find with the Gnome front end.

**Here is what I did:**
Install Dolphin using Synaptic Package manager.
Using terminal type this at the prompt.

```
gksu dolphin
```

type the administrator password.  The user account must be able to use the sudo stuff.

When Dolphin come up root will be home.  goto the home folder of where the target master folder is.  Rt click and then click on the permissions tab.  At the bottom there are two text boxes.  One for the new owner and the other for the new group.  Fill them in.  Then be sure to check the checkbox that says to apply to all sub folders and their contents.  You are now done.

It saved me a few day fo doing is manually or I would have to spend more time with the command line.  Hope this helps.

You mean Dolphin... KDE's manager does this whereas Nautilus (which I always have known as mr stability) has a bug regarding it?

Nice... Little bit of a headache though since I'd rather stay pure gnome... 

What's even more baffling is I had this same question back in 2006. And here in 2010, same deal. Did that bug exist the entire time????????

EDIT - I see that now. gksudo dolphin does the job just fine, whereas nautilus does not. Come on, nautilus...

---

