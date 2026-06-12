---
title: "How to move a file into another which requires permission"
date: 2009-07-26
forum: General Help
---

### Post by razorboy5 on 2009-07-26
Hi

after research i'm trying to move my aMSN plugins to the appropriate folder however u need "admin" status i believe so it's proving very difficult for me

i'm using the mv ~/ with sudo in the beginning of it but wont work for me

if i use ~/usr/share/amsn/plugin 
it says /home/daniel/usr/share/amsn/plugin does not exist

why does it go to /home/daniel ?

and how can i direct it to my hard drive which is default named Filesystem

also is there an easier way like giving "admin" status all the time when ur logged in? 

thx

---

### Post by danxx on 2009-07-26
When I want move files that way I do not use command line but open a window with gksudo nautilus and next to it another window again with the same command, after I simply drag files from one window to the other, yes it is not the right way but is more user friendly, I even created a launcher with the command

gksu -u root nautilus

in order to open windows with administrator permissions directly

---

### Post by razorboy5 on 2009-07-26
thx alot
gotta save that command too :D

---

### Post by oldos2er on 2009-07-26
> **razorboy5 said:**
> Hi

after research i'm trying to move my aMSN plugins to the appropriate folder however u need "admin" status i believe so it's proving very difficult for me

i'm using the mv ~/ with sudo in the beginning of it but wont work for me

if i use ~/usr/share/amsn/plugin 
it says /home/daniel/usr/share/amsn/plugin does not exist

why does it go to /home/daniel ?

and how can i direct it to my hard drive which is default named Filesystem


 It goes to /home/daniel because that's what you told it to do. "~" is shorthand for your user's home directory. "/" is the root or top-level directory, so you'd want to run
```
sudo mv /home/daniel/plugin /usr/share/amsn/plugin
``` for example.

---

### Post by danxx on 2009-07-27
a little thing more, with the solution gksudo nautilus you can even delete the entire system with one click as you have "su" privileges, then keep an eye on what you are doing and disable "immediate deletion" if you have enabled it in the right click menu,bye

---

### Post by undeadboe on 2009-07-27
login as a root user

Type this: sudo nautilus

---

### Post by razorboy5 on 2009-07-27
> **oldos2er said:**
> It goes to /home/daniel because that's what you told it to do. "~" is shorthand for your user's home directory. "/" is the root or top-level directory, so you'd want to run
```
sudo mv /home/daniel/plugin /usr/share/amsn/plugin
``` for example.

thx for the info that'll be VERY helpful later on in my Ubuntu experience :D

---

### Post by Whiffle on 2009-07-27
You should be able to put them in ~/.amsn/plugin, not have to worry about permissions.

~ means /home/<username>, at least by default on ubuntu.

---

