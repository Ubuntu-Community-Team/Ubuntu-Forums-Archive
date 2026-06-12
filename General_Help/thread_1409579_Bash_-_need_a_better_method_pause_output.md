---
title: "Bash - need a better method pause output"
date: 2010-02-17
forum: General Help
---

### Post by bakegoodz on 2010-02-17
I have a script that I use: read -p "Press Enter to continue", to show the output of a program that takes hours to run.
 The problem is that I use this script on a workbench that has a KVM that logs out after about 30 min, and to get the screen back I have to select the computer on the on screen menu and press enter. Often enter gets input into the script before I can read the output. This script runs menu functions so it clears the screen after one function is done. Anybody have a better method for me to freeze the output?

---

### Post by dcstar on 2010-02-17
> **bakegoodz said:**
> I have a script that I use: read -p "Press Enter to continue", to show the output of a program that takes hours to run.
 The problem is that I use this script on a workbench that has a KVM that logs out after about 30 min, and to get the screen back I have to select the computer on the on screen menu and press enter. Often enter gets input into the script before I can read the output. This script runs menu functions so it clears the screen after one function is done. Anybody have a better method for me to freeze the output?

Put two read lines in there.

---

### Post by rnerwein on 2010-02-18
hi 
to be sure you'll get your messages try this in your script:

while :
do
read -p "do wan't to see the output ( y/n): " answ
[ "$answ" == 'y' && break
done

this will be continued until you type in "y"

ciao

---

