---
title: "&quot;usermod&quot; -  'No'mod"
date: 2011-05-31
forum: General Help
---

### Post by CleveRuse on 2011-05-31
I'm running Ubuntu 11.04 with Gnome classic and having extreme difficulty changing my 'username'. Unfortunately, after doing some research, and seemingly finding the solution, i'm still coming up short. I have 3 Users, 2 of which r simply to serve as testers to practice on so i dont screw up anything vital. I'm using the 'sudo' command cuz the system wont allow me to straight " usermod -l..." while the User is running. So wut I'm typing looks like this:

# sudo usermod -l 'new-name' 'old-name'

But even after a reboot, nothing has changed so ....Next I tried to run it with the additional commands to change my 'Home' directory, 'Group', etc... preceded by the "killall" command, like this:

killall -u old
id old
# sudo usermod -l new old
# sudo groupmod -n new old
# sudo usermod -d /home/new -m new
# sudo usermod -c “New Real Name” new
id new

And to change my UID:

# id old
# usermod -u 10000 tom
# id old[FONT=Verdana]

Alternatively, I tried to change my username with this command:
 
[/FONT]# id tom
# usermod -l jerry tom
# id jerry
# id tom

[FONT=Verdana](tho i dont understand if its suppossed to do they same thing as the first ...and if so, wuts the diffference?)

Anyway, i dont know wut I'm missing but none of these try's yielded even the slightest change so... I'm hoping someone can shed some light on my failure(s). At this point I'm open any suggestion. I'd like to know wut i'm doing wrong but ...was also wondering if there is any alternative methods. Like simply using a 'Test Editor' ( how?- and where are the files located? )

*Note: to be clear, Im able to change my 'Owner' name (i think thats the "Log-In' name) from within 'System-Administration-Users and Groups'. I want to change the 'User' name (admittedly, I'm a little confused on this since I could swear ive seen BOTH referred to as "Users" or "User Names").  I want nothing but my USER NAME changed ...but if thats not possible, then i need all my files tranferred, my UID set to 1000 (i think), and my password set as '3333' for both 'Log-In' and 'Root Access'.

...Sooo ...whenever ur ready;)    Thnx in advance.
[/FONT]

---

### Post by CleveRuse on 2011-05-31
K, well I got it to work by omitting the # sudo at the beginning off the command, then typing it into a 'root' terminal. Now id love to know why I was doing wrong by typing into the regular terminal.

---

