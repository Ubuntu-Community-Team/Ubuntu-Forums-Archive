---
title: "Possible to delete files with a live CD?"
date: 2010-04-04
forum: General Help
---

### Post by Gav_amigaman on 2010-04-04
Hi
When i boot ubuntu i got to the login screen and i get a message and gnome power management not being installed correct.When i attempt to login it just brings me back to the login screen.Now i actually think it might have something to do with my drive being full so i put in the ubuntu install cd to access the Hard drive and erase files but the delete option is not highlighted.
So is there any way i can delete files from a partition by using the boot CD?
Thanks

---

### Post by MooPi on 2010-04-04
While using the Live CD Navigate to the directory where you want to deletion files. Open a terminal and enter this command  ```
sudo rm thefileyouwantdelted
```
Be very careful with this command.

---

### Post by neur0 on 2010-04-04
Or if you are not comfortable with the command line,
You can just type 
```
gksudo nautilus
```
in the console and use the file browser.

---

