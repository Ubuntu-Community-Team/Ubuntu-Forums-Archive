---
title: "run script or comand on log out?"
date: 2006-05-10
forum: General Help
---

### Post by junior aspirin on 2006-05-10
is it posible to run a comand or script when a user logs out?

i have a problem where photos imported via f-spot are only read write to the user who imported them. i want them readable by all users ( i have a shared docs directory in /home). the easiest way to solve this is to run the command
chmod -R %permisions% %directory%

since the people using this pc do not understand computers the best way would be to do this automagicaly. idealy on logout. is that posible?

---

### Post by cgjones on 2006-05-10
I think you can create a file called .bash_logout in each users home directory that contains commands that will be run upon logout, although I'm not sure how this works in a graphical environment. I would think that it would still run.

---

### Post by Ramses de Norre on 2006-05-10
Or store the script in /etc/init.d/ and add a simlink to it in /etc/rc6 (reboot scripts) and /etc/rc0 (halt scripts).
Only thing I'm not sure about are those S or K codes you need to add to the name..
Look at /etc/init.d/skeleton for an example.

---

### Post by cgjones on 2006-05-10
[QUOTE=Ramses de Norre]Or store the script in /etc/init.d/ and add a simlink to it in /etc/rc6 (reboot scripts) and /etc/rc0 (halt scripts).
Only thing I'm not sure about are those S or K codes you need to add to the name..
Look at /etc/init.d/skeleton for an example.[/QUOTE]

Won't that just run the script at reboot and shutdown?

---

### Post by Ramses de Norre on 2006-05-10
Oh, right.. I should have read the question more carefully.

---

### Post by junior aspirin on 2006-05-10
thanks for your replys.

cgjones unfortunatly it doesnt seem to work.

it looks as though it will have to be run on login. unless i can think of another way. the problem is it will invole the user loging out, then back in again in order for the other users to see the files.

---

### Post by junior aspirin on 2006-05-10
edit: ignore.
dupe post due to the forum going weird..

---

### Post by cgjones on 2006-05-10
Depending on exactly what you need to do, you could write a script that makes the changes you need, then put the script in /usr/local/bin (I think that should be in the users path). That way, the user could just type one command, and the changes would be done.

---

### Post by flyingbrass on 2006-05-10
Add what you want in /etc/X11/gdm/PostSession/Default.  Apparently adding scripts to the PostSession directory doesn't work because only the Default script gets run.  In other words, edit the Default file, don't just throw scripts in the PostSession directory and expect them to work.

I added a line to delete all my thumbnails.

---

### Post by junior aspirin on 2006-05-11
so stuff in /etc/X11/gdm/PostSession/Default gets run when the user logs out. am i correct?

its only a simple comand i wish to run. although i normaly fudge it up. i think this is what i want:
```
chmod -R a=rwrwr /home/shared/photos/
```
can someone just clarrify that that is correct. i always get the rwx bit wrong. its to make all the files in that directory and all its subdirectorys read and writeable by the owner and group, but readable and not writeable by all other members.

i hope that is clear.

---

### Post by cgjones on 2006-05-11
I think you are going to need something more like this. Although that's off the top of my head, so I would try it out first on a test directory.
```

chmod -R ug=rwX,o=rX /home/shared/photos/

```

---

### Post by ashrack on 2006-05-17
how would I achieve a similar thing but on a user level?
I've written 2 different scripts for 2user accounts. Script No.1 should be executed when user No.1 is loging out and the same with user No.2.

---

### Post by Ramses de Norre on 2006-05-17
```
chmod -R a=rwrwr /home/shared/photos/
``` should be ```
chmod -R 664 /home/shared/photos
``` or ```
chmod -R ug=rw,o=r /home/shared/photos
```

---

### Post by ashrack on 2006-05-18
[QUOTE=ashrack]how would I achieve a similar thing but on a user level?
I've written 2 different scripts for 2user accounts. Script No.1 should be executed when user No.1 is loging out and the same with user No.2.[/QUOTE]
anyone?

---

### Post by corny on 2007-06-10
/etc/gdm/PostSession/Default is run as root.
I would do first a chown -R $USER:[gid] with all files. [gid] would herein be the group id of the group  all allowed users belonging to. then I would do the chmod -R 664 with that files.

---

