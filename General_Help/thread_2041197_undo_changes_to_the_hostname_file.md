---
title: "undo changes to the hostname file"
date: 2012-08-12
forum: General Help
---

### Post by adiz on 2012-08-12
hi..
 
I somehow managed to modify my /etc/hostname file. Now I want to undo the changes I have made. But it says that the file is owned by the root. How do I change it?
 
Thanks for the help..

---

### Post by chadk5utc on 2012-08-12
usually the computer name is in this file. not sure what you would need to change in it but using sudo vi /etc/hostname will open and edit this file. replace vi with your editor of choice.

---

### Post by chadk5utc on 2012-08-12
forgot to mention that you can simply type hostname thensomename to change it as well

---

### Post by claracc on 2012-08-12
What is exactly the change you have made?, is it in hostname file under /etc?. Have you changed the name of the host?. 

To back it to the original name you will have to run in a xterm:

gksudo gedit /etc/hostname
then you enter your password
And inside the file you change the name to the original
save and close

I recommend no mess with hostname file, it can do your system unusable.

---

### Post by Cheesemill on 2012-08-12
Also bear in mind that whenever you edit /etc/hostname you should also make the relevant changes to /etc/hosts as well to properly change the name of your machine.

---

