---
title: "Need help setting up raw1394 and Kino"
date: 2006-02-02
forum: General Help
---

### Post by drmcclure on 2006-02-02
I am not able to get Kino to work for one reason or another.  Under the preferences, it reads that there is no permission for raw1394 or it cannot load the module.  How can I solve this problem so I can get Kino to work?  Thanks!

---

### Post by MacMan on 2006-02-03
Try starting Kino as superuser:
```
sudo kino
```
If that doesn't work, try loading the raw1394 module first:
```
sudo modprobe raw1394
```
Then start Kino as superuser. It worked for me.
When you're done down/uploading video from your cam you can edit it using kino as a normal user.

I hope this helps.
Ciao.
-- 
Marcello

---

### Post by curtisdf on 2007-11-08
I just encountered this issue.  I found that any user doing stuff with raw1394, which Kino does, must be a member of the "disk" group.  I'm sure there are graphical ways of doing this, but I'm a command-line buff, and I'm also using KDE, so here's what I did:

First, to see which groups you belong to, you can type the following on the command line:

```
# groups
```

If "disk" isn't there, your username will need to be added.  You can do this:

```
# sudo nano /etc/group
```

I then changed line 7 of the file from:

```
disk:x:6:
```

to:

```
disk:x:6:curtis
```

(My username is "curtis".  Substitute your username as appropriate.)  I then typed "groups" again, but it didn't register the change.  So I logged out and logged back in, ran "groups" again, and there it was!  And capturing in Kino worked just fine.

-Curtis

---

### Post by steve allen on 2008-05-11
Do you just type the change into disk:x:6 or does it require a command. When I just typed it in nothing happened.

The change in the first reply worked I can capture if I load using  #: sudo kino but not by just opening from applications.

regards

steve

---

