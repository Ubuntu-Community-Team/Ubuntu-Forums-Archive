---
title: "Open with ?"
date: 2011-12-28
forum: General Help
---

### Post by randiroo76073 on 2011-12-28
Did a search as I figured someone had already asked. What program do I use to open a shell script w/o invoking the run dialog box ? As in "Open with" dialog. 

Thanks for any help.

---

### Post by TroN-0074 on 2011-12-28
right click on the file and select open with gedit if it is a text script

---

### Post by randiroo76073 on 2011-12-28
> **TroN-0074 said:**
> right click on the file and select open with gedit if it is a text script
Thanks TroN-0074
Guess I wasn't to clear, I want the program to open not edit the file

---

### Post by VCoolio on 2011-12-28
first check if it's marked as executable, then tell nautilus (the file manager) to run executable files instead of opening them: in your file browser, edit > preferences > behavior tab.

---

### Post by F.G. on 2011-12-28
i think you may need to run 'sudo chmod -x filename.sh' or something to get it to be executable. then './filename.sh' to run it. (both of these from the command line).

---

### Post by VCoolio on 2011-12-29
> **F.G. said:**
> i think you may need to run 'sudo chmod -x filename.sh' or something to get it to be executable. then './filename.sh' to run it. (both of these from the command line).

chmod +x filename that is, and sudo not necessary unless you lack the permissions to the file.

---

