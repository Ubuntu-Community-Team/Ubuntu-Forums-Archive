---
title: "installed dependencies"
date: 2006-05-29
forum: General Help
---

### Post by bobanshirl on 2006-05-29
Can someone tell me where and how to find what dependencies are installed and how do I install them and where do I get them from,this is B.Badger I am referring to.

---

### Post by frodon on 2006-05-29
If you use apt-get commands or synaptic the dependencies are automatically solved/installed and you can see their name in the log.
Do you know how to use synaptic and repositories ? If not this may help you :
[http://ubuntuforums.org/showthread.php?t=153118](http://ubuntuforums.org/showthread.php?t=153118)

---

### Post by bobanshirl on 2006-05-29
I am on a PC with Internet connection and CD burner and I booted with the Live cd in.Then you say Quote,Install whatever the Wiki wants you to install (sudo apt-get install blabla)using the live cd.
Burn the packages etc etc I am afraid I am floundering in deep water here
can you explain those 4 items what will the Wiki want me to install I printed off all the pages of your thread another thing is when I got my sources list up do you want me to edit it by copying the file you put in the thread,and also how do I install `checkinstall`

---

### Post by frodon on 2006-05-29
Edit your source.list file like the one i gave in the thread then open synaptic and press the reload button.
To install "checkinstall" use the search button in synaptic to find it then use the right click to select the installation of the software then click the "apply" button in synaptic.

BTW did you install ubuntu or do you only use the live CD ?

---

### Post by bobanshirl on 2006-05-29
Can you explain this verbatim   An easier way to go about would be: 
1. Find a computer with internet access and a CD burner and boot using the live CD. 
2. Install whatever the wiki wants you to install (sudo apt-get install blabla) using the live cd
3. burn the packages under /var/cache/apt/archive to the CD
4. go home, boot your ubuntu, put in cd and mount it, copy all the packages in that cd to /var/cache/apt/archive
5. go back to the wiki and sudo apt-get install wahtever it wants. 

/var/cache/apt/archive is the temporary file directory of apt-get when it installs stuff from the internet repos.

---

### Post by bobanshirl on 2006-05-29
[QUOTE=frodon]Edit your source.list file like the one i gave in the thread then open synaptic and press the reload button.
To install "checkinstall" use the search button in synaptic to find it then use the right click to select the installation of the software then click the "apply" button in synaptic.

BTW did you install ubuntu or do you only use the live CD ?[/QUOTE]
Ihave UBUNTU installed

---

