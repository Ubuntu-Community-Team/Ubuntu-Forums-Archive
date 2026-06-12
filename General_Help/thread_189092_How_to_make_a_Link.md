---
title: "How to make a Link"
date: 2006-06-04
forum: General Help
---

### Post by cobbweb on 2006-06-04
Hey, 
  I want to make an Icon link on one of my starters for a game called Americas Army. I have normally been just going in my terminall to the file location and typing sh armyops to run the program but I play it enough I feel like I need an Icon on my desktop. However, I tried to open it using the command  

sh /home/thenetduck/Installed_Programs/Americas\ Army/armyops

but this didn't seem to work. I know you can make some type of link to my home where i can just type in sh armyops? Is that what i need to do? I have never had very much luck with links or using them. How can I make an Icon to just click on? 

 Mahalo, 

 Cobbweb

---

### Post by jpkotta on 2006-06-04
It sounds like the program only works correctly if it is run from its directory.  It's easy to work around this.

```
#!/bin/sh
cd /home/thenetduck/Installed_Programs/Americas\ Army/
sh armyops

```

Put the above into a file, say, launch_armyops.  Then make it executable with ```
chmod +x launch_armyops
```.  You can move the file to ~/Desktop, and it should be a clickable icon on the desktop.

Extra bonus hint: If you like the terminal, you can add the following to your ~/.bashrc:

```
alias armyops='(cd /home/thenetduck/Installed_Programs/Americas\ Army/ ; sh armyops)'
```, and you can launch it from any terminal with just "armyops".  The () create a subshell, so that the cd doesn't affect the shell you're typing in.

---

### Post by cobbweb on 2006-06-05
Wow, You were so much help. Thanks a whole lot. The examples really help me understand some things about linux that I just wasn't quite getting before. Thanks a bunch. 

 Mahalo, 

 Cobbweb

---

### Post by jpkotta on 2006-06-05
I'm glad to have been some help, even with the typo (cdmod -> chmod).

---

