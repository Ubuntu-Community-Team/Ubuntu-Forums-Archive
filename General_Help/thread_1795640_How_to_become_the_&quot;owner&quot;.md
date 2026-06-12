---
title: "How to become the &quot;owner&quot;?"
date: 2011-07-03
forum: General Help
---

### Post by ssreddy555 on 2011-07-03
When I want to copy Themes folders from usr > share > themes. it says "permission denied - you are not the owner". Mine is the only one user account on this computer. 

How to make the system recognize this fact?

I know from Terminal, I can use sudo to get root privileges. Is there a way to "become root" without using the Terminal?

---

### Post by Wim Sturkenboom on 2011-07-03
Never used it, but I think this will do the trick in a terminal
```

gksudo nautilus

```
Be very carefull, you can screw up your system if you fiddle with the wrong stuff. Close nautilus as soon as you're done.

---

### Post by ssreddy555 on 2011-07-03
Thank u. I will try this. But now that u have warned, I'm really afraid to fiddle with it.

---

### Post by sam_delta on 2011-07-03
> **ssreddy555 said:**
> 
Mine is the only one user account on this computer. 
How to make the system recognize this fact?


most (if not all) of the system files (outside your home directory) are owned by root, not by your user.
root is an actual user, but its login is disabled by default in ubuntu for security reasons.

sam

---

### Post by Wim Sturkenboom on 2011-07-03
I tried it in crunchbang (another Linux distro) and did not experience the permissions issue.

But you can do the following from a terminal
```

wim@aa0:~$ pwd
/home/wim
wim@aa0:~$ **sudo cp -R /usr/share/themes/Misted .**
wim@aa0:~$ ls -l Misted/
total 8
drwxr-xr-x 2 root root 4096 Jul  3 11:32 gtk-2.0
drwxr-xr-x 2 root root 4096 Jul  3 11:32 openbox-3
wim@aa0:~$ **sudo chown -R wim:wim Misted/**
wim@aa0:~$ ls -l Misted/
total 8
drwxr-xr-x 2 wim wim 4096 Jul  3 11:32 gtk-2.0
drwxr-xr-x 2 wim wim 4096 Jul  3 11:32 openbox-3
wim@aa0:~$ 

```
The first command in bold copies the theme directory 'Misted' to the current working directory; after starting a terminal, that is your home directory. Replace 'Misted' by the name of the theme that you want to copy.
Because sudo was used, the permissions will still be a problem as the files are still owned by root.
The second command in bold changes the owner and group to wim and wim; replace 'wim:wim' by your username and the group that you are a member of.

The other commands used in the above example:
*pwd* shows the current working directory
*ls -l Misted* shows the owner/group/permissions for the files in the directory Misted

You should now be able to find  the theme in Nautilus and do whatever you want to do with it.

---

### Post by steveneddy on 2011-07-03
No need to be root all the time - security and all that.

Just get used to sudo-ing (is that a word?) when you need to perform administrative tasks.

For graphical purposes,

```
gksudo nautilus
```

opens a root window to copy files where you need them - then just close it and go about your business.

Being root all the time is not safe if you are connected to the internet - in that case you may as well use Windows.

Just get yourself accustomed to the security in Linux - accept the fact that this is why Linux is more secure than Windows - and you will be just fine. Don't try and impose Windows world rules on your Linux machine - everyone is an administrator - this is why Windows has a problem with virus protection.

Enjoy.

---

### Post by ssreddy555 on 2011-07-03
gksudo nautilus works for me without being too complicated & for a one time use.

Thanks for all.

---

### Post by CatKiller on 2011-07-03
> **ssreddy555 said:**
> gksudo nautilus works for me without being too complicated & for a one time use.

Thanks for all.

Don't forget to mark the thread as Solved.

One thing that's useful is to have windows with root permissions colour-coded, so that you know which is which. If you run ```
gksudo nautilus
``` and then Edit -> Backgrounds and Emblems you can make it look really ugly so that you aren't tempted to use it for anything other than what you really have to.

---

### Post by deserthowler on 2011-07-03
If you install [COLOR="Red"]nautilus-gksu[/COLOR] from Synaptic an 'open as administrator' bar will appear on your right click menu.  When you click that,it will ask for your password and allow you to act as root on that file, directory, what ever.  When you close the the item, the permission is gone.

Earl

---

