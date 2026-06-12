---
title: "Back up all chat history in Pidgin? How..?"
date: 2009-11-09
forum: General Help
---

### Post by Kdar on 2009-11-09
I plan to do a fresh install of Ubuntu 9.10 today or tomorrow.
However. how do I save/backup all chat history from Pidgin? I want to import it to new chat-software in Ubuntu 9.10 (Emphyty or whatever it is called).

How do I do it? Is there a way to save all chat history in Pidgin?

---

### Post by jbrown96 on 2009-11-09
you can defiantly save it, but I'm not sure about importing it into empathy. The configuration files for all of your programs are stored in "dot" files. If you open the file browser and show hidden files (ctrl+h), you will see a lot of folders/files. These are where your configurations are stored. Find the pidgin folder. It may be in .gnome. Copy that and you should be set. you can backup any other configurations that you want. 


when you reinstall it would be a good idea to put /home on a separate partition. If you need to reinstall in the future, you can choose to NOT format /home, and then you won't have to mess with moving anything around.

---

### Post by Kdar on 2009-11-09
Thanks for help. I found it in .purple

I plan to do that this time around. How much do you think I should give to Home partition? Most of the hard disk space?

---

### Post by jbrown96 on 2009-11-09
I don't have any swap (2GB of ram), so I only have have two partitions (not completely true, I have a third for Fedora). / is ~6.5GB, and I have most of that full, which surprises me. I have a lot of software development stuff that most people would never have. If you plan to keep this installation for a few years, then you should make it bigger. I'd say that anything over 10GB is overkill. /home is going to be where all your stuff is. Music and Videos quickly dwarf the size of any programs. 

Give around 10GB to /
You probably don't need swap at all
rest for /home

If you ever want to play around with other distros, you may want to create another 5-6GB partition, so you don't need to remove Ubuntu if you want to try another.

It really depends on how much hard drive space you have.

---

