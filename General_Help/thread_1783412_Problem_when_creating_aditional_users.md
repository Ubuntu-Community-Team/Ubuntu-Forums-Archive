---
title: "Problem when creating aditional users"
date: 2011-06-15
forum: General Help
---

### Post by jsanchezm on 2011-06-15
Hi, i just updated ti ubuntu 11.04. The problem is not to create the users, it is when they log in. For example, when i create the user "luli", when i log in this message appears:
```
Could not update ICEauthority file /home/luli/.ICEauthority
```
I can only see the cursor and the background, then:
```
There is a problem with the configuration server. (usr/lib/libgconf2-4/gconf-sanity-check-2 exited with state 256)
```
Then a notification shows up an the right up corner:
```
Could not apply the stored configuration for monitor.
```
And finally another error message:
```
 Nautilus could not create the following folders:  /home/luli/Desktop and /home/luli/.nautilus. Before running nautilus, please create this folders, or set permissions such that Nautilus can create them.
```
Then nothing else happens, and i have to restart the computer.
I looked for this error on the internet and someone said that fixed with changing permissions to the folders manually.
I created those folders, as said on the last error message, and set the permissions using:
```
sudo chmod 755 /home/luli/
sudo chown luli:luli /home/luli/
```
Then i copied the archive .ICEauthority form my personal user folder, to the new user's folder and used this:
```
sudo chmod 600 /home/luli/.ICEauthority
sudo chown luli:luli /home/luli/.ICEauthority
```
And i got nothing to change, it still not work. I have to add that a couple of days ago i moved the /home folder to its own partition, in order to have my files more independent from the system. I did that following this steps: [http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/](http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/)

Thank you for your time!

---

