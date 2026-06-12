---
title: "Keyring password on start up"
date: 2010-01-19
forum: General Help
---

### Post by retro_killa on 2010-01-19
When I start up my laptop that is running Ubuntu 9.10 I get a pop up window that asks me to input my password for Keyring. How can i remove this from the start up or how can I remove from having to put in my password for every time I get prompted ?

---

### Post by retro_killa on 2010-01-19
I did this & I had a problem with step #4 because I did not see a folder called **keyrings** all I was able to see what a folder called **gnoke-vfs**

   1. Open up your Home Folder by clicking Places>Home Folder
   2. Press CTRL-H (or click View>Show Hidden Files)
   3. Find a folder called .gnome2 (it has a period at the beginning of the name) and open it by double clicking on it
   4. In side of the .gnome2 folder, there is another folder called keyrings.  Open it up.
   5. Delete any files you find within the keyrings folder
   6. Restart the computer

...
..
.

Is there away to do this with in the terminal ? I just want to never have to input my password ;)

---

### Post by n0dix on 2010-01-19
See this thread: [http://ubuntuforums.org/showthread.php?t=796410]("http://ubuntuforums.org/showthread.php?t=796410")

Good luck!

---

