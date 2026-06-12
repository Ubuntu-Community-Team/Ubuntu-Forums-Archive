---
title: "major problem!!!"
date: 2009-07-14
forum: General Help
---

### Post by becoolpal on 2009-07-14
There wa a routine check up of my files when i started my kubuntu & following error was reported:

"/dev/sda6 : unexpexted inconsistency :run fsck manually(without option -a or -p)

fsck died with exit status 4
 checking drive /dev/sda6 : 64%(stage 1/5 267/288)
 
an automatic file sysytem check(fsck)failed

a mannual fsck must be performed .The root file system is currently mounted in read only mode.A mantainance shell will be started 

bash : no job control in this shell 
bash: groups :command not found
bash : cesspipe :command not found"

I am not able to start my computer.I always need to escape this routine checkup in order to work on the computer.Please tell me how to run file system check manually.

please help!!!

---

### Post by cwbar_1 on 2009-07-14
Which file system are you using?  eg..ext 2, ext 3, or ext 4.
If you are using ext 2, boot using a live cd. Open a terminal and type "sudo e2fsck /dev/sda6".  (without the quotes)  If you are using ext 3 or 4, boot using live cd. Open a terminal and type  "sudo fsck /dev/sda6". (without the quotes)  
Once it is finished you should be able to reboot.

---

### Post by becoolpal on 2009-07-21
hey thanx it really worked!!!!!

---

