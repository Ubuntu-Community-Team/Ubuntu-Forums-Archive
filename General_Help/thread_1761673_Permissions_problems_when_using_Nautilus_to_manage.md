---
title: "Permissions problems when using Nautilus to manage files"
date: 2011-05-18
forum: General Help
---

### Post by stefanaalten on 2011-05-18
Using Ubuntu 10.10 in VirtualBox 4.0.8 on Windows XP host.

I like to use the Nautilus file manager to work with files, but keep running into permissions problems. I guess this because I am not logged in as the "root" user. I do know how to do basic stuff like move/copy at the command line and use the "sudo" command to prefix (e.g. "sudo mv ...") to run a command as the "root" user, but I would much prefer to use a GUI like Nautilus to drag and drop.

What can I do?

a) Log into Ubuntu as "root" - not my preferred option as I would like to log in as "myself" and only use these special privileges when needed.
b) Is there an option in Nautilus to do the equivalent of prefixing a command with "sudo", e.g. hold down a particular key combination when dragging/dropping or a setting somewhere? I couldn't find anything in the help.
c) Something I haven't thought of? ...

Many thanks in advance!

---

### Post by dragonfly41 on 2011-05-18
For file management you might find these useful .. from Synaptic Package Manager

GNOME Commander
or Tux Commander
or File Manager

---

### Post by DanneStrat on 2011-05-18
You can try to start nautilus with "gksudo". Nautilus will then be 

run with elevated privilegies and so will the applications that 

nautilus calls to do file operations.

In a terminal:

```
gksudo nautilus
```

Just be careful when you use nautilus this way

because you will get access to files owned by "root".

Also, don't try to make nautilus run like this by default.

Good luck.

---

### Post by stefanaalten on 2011-05-18
Thanks. I have downloaded & installed Gnome Commander, but am still having permissions problems.

When I try to rename a file "owned" by the root user I get a permission denied error.

I have added myself to the root group, logged out & back in again. My account type is an Administrator, and I am the only user of this system, which runs locally on my laptop.

Couldn't find a setting in Gnome Commander to "do stuff as the root user".

Any help please?
:confused:

(Overlap with second poster's reply - thanks - will invoke the incantation "gksudo" to make magic happen. I feel like an initiate in a world of arcana - all these weird and wonderful commands!)

---

### Post by dragonfly41 on 2011-05-18
GNOME Commander .. navigate to file
permissions are seen in one of the columns 
right click on highlighted file > menu > Properties > Permissions Tab

[EDIT]
To open GNOME Commander in root

sudo gnome-commander

or .. under GUI toolbar > File > Start GNOME Commander as Root

---

