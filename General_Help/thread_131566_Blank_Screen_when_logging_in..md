---
title: "Blank Screen when logging in."
date: 2006-02-16
forum: General Help
---

### Post by moutraji on 2006-02-16
I need Help!!!
I was getting the following error and i believe i 've solved it:
$HOME/.dmcr permission denied.... permission need to be 644 and so on....
i solved that by going to etc/passwd file and changed my root to how it was before.. but now when i try to log in, the screen becomes blank brown and can't go to the envirmenmt... Please if any one know's how to solve this problem i will appreciate it!!!! Thankx

---

### Post by Lord Illidan on 2006-02-16
Have you recently started any KDE apps under Gnome with sudo?

---

### Post by moutraji on 2006-02-16
Not at all!! I didn't started any!!!

---

### Post by CameronCalver on 2006-05-07
Hey my error is similar i have a lan and sometimes when i copy files it says permision denied so i went on the computer i was accesion and when onto the home folder and set permissions to write for owner and group and unclicked all of the things on others
 
Then when i restart then i log in and these are the errors

Your home directory listas as /home/broadband but it does not appear to exist do you want to log in with the (root) directory as your home directory 

then i click yes and this comes up

your $home/.dmcr file has incorrect permissions and is being ignored this oresent the default session and launguage from being saved.
File should be owned by user and have 644 permissions 

then a thing comes up saying this session lasted less then 10 seconds i read the error it says
gnome-session 8139 lib gnome ufs warning unable to create ~/.gnome2 directory permission denied /home/broadband.gnome2.  permission dennied

i can only log into the terminal only does any1 know what i should do to fix it

---

