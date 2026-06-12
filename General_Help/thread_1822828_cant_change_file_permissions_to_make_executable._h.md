---
title: "cant change file permissions to make executable. help!"
date: 2011-08-11
forum: General Help
---

### Post by jshx87 on 2011-08-11
im having trouble running programs with wine, keep getting the same error. its not set as executable. the check box under permission tab within the properties of the file will not stay checked. not sure if i need to sudo it, and i really don't know how to do that. im newish to linux so please help
[URL="http://youtu.be/1FJTAnjayU0"]
video of the issue[/URL]

---

### Post by Bart92 on 2011-08-11
> **jshx87 said:**
> im having trouble running programs with wine, keep getting the same error. its not set as executable. the check box under permission tab within the properties of the file will not stay checked. not sure if i need to sudo it, and i really don't know how to do that. im newish to linux so please help
[URL="http://youtu.be/1FJTAnjayU0"]
video of the issue[/URL]

Right click on the exe file and select properties. Then check "Allow executing as program" in the Permissions tab.

---

### Post by jshx87 on 2011-08-11
i do that but the box will not stay checked. reverts almost instantly. is there a command line in terminal i can  use to do this?

---

### Post by Bart92 on 2011-08-11
> **jshx87 said:**
> i do that but the box will not stay checked. reverts almost instantly. is there a command line in terminal i can  use to do this?

Sounds like you are trying to run an executable that is on some kind of removable media, like a CD or DVD ?

---

### Post by jshx87 on 2011-08-11
its on a external harddrive. should i move it to /home?

---

### Post by IT Support on 2011-08-11
have  you try to chmod this  file? 
type  in terminal 
sudo chmod 777 /and location your file 
maybe it will be help you

---

### Post by Bart92 on 2011-08-11
Try to copie the *.exe file onto the desktop and right-click and marking the  box. 
Then run it, give that a  try.

---

### Post by Bart92 on 2011-08-11
[FONT=Verdana]Or install Ntfs configuration tool and set both internal and external drives to write
[/FONT]

---

### Post by 3rdalbum on 2011-08-11
If the external hard disk doesn't support Linux permissions, or if it's mounted read-only, you can't set the execute permission.

However, you can run Wine and tell it to run this file, even without the execute permission. Open a terminal and type *wine* and press the space bar to leave a space at the end. Drag the file to the terminal window so its path fills into the terminal. Click on the terminal window again to foreground it, and then press Enter.

Wine starts running the program, assuming it works with Wine of course :-)

---

