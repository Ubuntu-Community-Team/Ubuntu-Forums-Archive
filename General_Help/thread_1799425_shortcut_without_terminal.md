---
title: "shortcut without terminal"
date: 2011-07-07
forum: General Help
---

### Post by nmxdaven on 2011-07-07
Hey guys!

I have a few programs that need to be run as root, and I'm lazy, so I like to make a shortcut on the desktop with "sudo programname" to start them up. My question is, is there a command I can put in the shortcut that will run the program but hide the terminal that pops up along with it? When i launch like this it leaves the terminal showing everything thats going on, on the desktop. 

Thanks!
nmxdaven

---

### Post by CaptainMark on 2011-07-07
create a desktop launcher of the application type (not application in terminal) and use the gksu prefix instead of sudo, so a launcher with ```
gksu nautilus
```will open a file manager after asking for your sudo password in a non-terminal window

---

### Post by nmxdaven on 2011-07-07
Im an idiot. Never thought of that. Thanks!

---

