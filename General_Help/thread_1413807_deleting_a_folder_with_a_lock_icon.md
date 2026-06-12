---
title: "deleting a folder with a lock icon"
date: 2010-02-22
forum: General Help
---

### Post by sincerelyydavid on 2010-02-22
how do i delete a folder with a lock icon on it? and how did it get there?

---

### Post by crlang13 on 2010-02-22
I assume it's probably locked for a reason... Where is the folder located?  It's probably owned by the root user.

---

### Post by gymophett on 2010-02-22
You will have to delete it as root.

Open up the file manager with ```
sudo nautilus
```..
Then delete it.

---

### Post by tacantara on 2010-02-22
If you're sure that it's safe to delete the folder, you will need to override the permission setting that is locking the folder.  Open a terminal, and type ```
gksudo nautilus
```

When prompted, enter your password.  A file browser window will open up.  Navigate to the location where the file is.  The lock icon should not be visible.  You can then delete the folder.  When you're done, close the Nautilus browser window, and close the terminal.  You will receive a warning that a process is still running in the Terminal, but you can safely close it out.

---

### Post by jflaker on 2010-02-22
once you are sudo, you are on your own...make absolutely sure you should be deleting that folder or things will stop working, including the OS

---

### Post by sincerelyydavid on 2010-02-22
the folder is in my home folder and is called lexmark. i think that's the driver i tried to install for my printer.
i tried the sudo thing, but i couldn't find the folder under nautilus o_o

---

### Post by jflaker on 2010-02-22
> **sincerelyydavid said:**
> the folder is in my home folder and is called lexmark. i think that's the driver i tried to install for my printer.
i tried the sudo thing, but i couldn't find the folder under nautilus o_o

go into terminal and type 
```
ls -al 
```

(list - Similar to dir in windows) and post the output

---

### Post by Yellow Pasque on 2010-02-22
When you start nautilus as sudo/root user, then your home folder is /root, which is probably confusing you.
Also, you can install nautilus-gksu package and that will put an option in nautilus to right-click something and open it in another window with gksudo privileges.

---

### Post by sincerelyydavid on 2010-02-23
> **Temüjin said:**
> When you start nautilus as sudo/root user, then your home folder is /root, which is probably confusing you.
Also, you can install nautilus-gksu package and that will put an option in nautilus to right-click something and open it in another window with gksudo privileges.
i installed nautilus-gksu, but when i right-clicked the folder, nothing happens in nautilus.
all i see in the /root folder is Desktop. nothing else. and then when i double-click Desktop, there's nothing in there.

---

### Post by gmjs on 2010-02-23
A folder appears with a 'lock' emblem if you only have read (and 'execute' to be technically correct) permissions to it and therefore can't write to or delete it.

In this case it probably means that a program or command executed using 'sudo' (run as root) created it.

By default, nautilus opens at the home folder of the user that ran it.  Running **gksudo nautilus** runs it as the root user.  The root user's home folder is located at **/root** (rather than /home/root as you might be expecting).

Press the '**UP**' button on the toolbar to return to the root of the filesystem '**/**' (a bit like '**drive C:\**' on a Windows operating system) and navigate to your home folder (if that's where the 'lexmark' folder is that you no longer want) by double-clicking the '**home**' directory in the list.  Your folder should be in there with folders for any other users of your system.

If you'd prefer to get straight there, you would type this instead:

```
gksudo nautilus $HOME
```or (even quicker ;-))

```
gksudo nautilus ~
```(Both do the same thing.)

Hope that helps.

---

### Post by sincerelyydavid on 2010-02-23
wow thanks, that was helpful=)

---

