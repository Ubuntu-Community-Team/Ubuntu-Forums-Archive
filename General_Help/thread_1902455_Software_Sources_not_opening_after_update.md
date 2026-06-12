---
title: "Software Sources not opening after update"
date: 2011-12-30
forum: General Help
---

### Post by bluexrider on 2011-12-30
Ubuntu 11.10 

Cannot open software sources to edit or add PPA's

also have 5 Pinned applications in Synaptic.

---

### Post by spacecheck on 2011-12-31
Perhaps you could go to your /etc/apt/sources.list file and examine/edit the available sources listed, to see if you can resolve the problem.  Good luck!

---

### Post by bluexrider on 2011-12-31
> **spacecheck said:**
> Perhaps you could go to your /etc/apt/sources.list file and examine/edit the available sources listed, to see if you can resolve the problem.  Good luck!
Thank you. 

I can edit the sources list however that is not the issue. The GUI for 'software sources' does not work.

---

### Post by spacecheck on 2011-12-31
Do you have "Synaptic" installed? If so, can you open that & then make the desired changes under "Settings, Repositories"? If not, perhaps you could sudo apt-get install synaptic and see if it works either to solve the problem or as a workaround..

---

### Post by bluexrider on 2011-12-31
> **spacecheck said:**
> Do you have "Synaptic" installed? If so, can you open that & then make the desired changes under "Settings, Repositories"? If not, perhaps you could sudo apt-get install synaptic and see if it works either to solve the problem or as a workaround..
Thanks again,

No. It does not work.

---

### Post by spacecheck on 2011-12-31
Can you bypass the gui by using apt-get from the terminal? You could try "sudo apt-get update" to see if you get error messages that might indicate the problem. If apt-get update doesn't give an error, perhaps you could try "sudo apt-get reinstall synaptic". No luck with that? Perhaps try "sudo apt-get purge Synaptic" then reinstall. You could try apt-get options for clean, fix, etc., all without the gui. Good luck!

---

### Post by bluexrider on 2011-12-31
> **spacecheck said:**
> Can you bypass the gui by using apt-get from the terminal? You could try "sudo apt-get update" to see if you get error messages that might indicate the problem. If apt-get update doesn't give an error, perhaps you could try "sudo apt-get reinstall synaptic". No luck with that? Perhaps try "sudo apt-get purge Synaptic" then reinstall. You could try apt-get options for clean, fix, etc., all without the gui. Good luck!

Yes I can use the terminal to "apt-get". No errors there. 
Yes I have reinstalled 'synaptic' and 'software-properties-gtk'.
Yes I have ran 'clean, fix, purge, and autoremove' from apt-get.

I think it may be a bug

---

### Post by bluexrider on 2012-01-07
closed without resolution by OP

---

