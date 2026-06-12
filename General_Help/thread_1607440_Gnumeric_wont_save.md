---
title: "Gnumeric wont save"
date: 2010-10-27
forum: General Help
---

### Post by tetris11 on 2010-10-27
Gnumeric 1.10.1
Hi there, I tried editing a .xls spreadsheet with gnumeric and I came across the message "operation not supported". 
I tried running Gnumeric from terminal to see if there was any more info regarding the save, but it just outputted that one message "Operation not supported" and that was it.

The .xls file is on another partition so I figured maybe Ubuntu mounted the partition in read-only, but no - I can edit other documents on the partition.
I right clicked on the .xls file to see the permissions and it says Owner Group and Others are all read+write.

I uninstalled and reinstalled gnumeric, but no change.
I dont know what else to do?

---

### Post by jbrefort on 2010-10-28
I don't remember what was the problem, may be libgio, but this works after upgrade to more recent version.

---

