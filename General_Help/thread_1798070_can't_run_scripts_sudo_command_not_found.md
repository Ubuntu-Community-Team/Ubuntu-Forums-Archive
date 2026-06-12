---
title: "can't run scripts? sudo command not found"
date: 2011-07-05
forum: General Help
---

### Post by brunobliss on 2011-07-05
I've just upgraded to 11.04 and as much as i'm loving the eye candy this problem is killing it for me:

whenever i try to run a script **"./sakis3g (e.g.)**" i get "**Permission Denied**" - Fair enough
so i try "**sudo ./sakis3g**" and i get "**sudo ./sakis3g: command not found**"

This is a big issue, i also noticed that when i try to **TAB **after the "**./**" for name completion, nothing happens, i have to type in everything manually .... PLEASE HELP !!!

---

### Post by papibe on 2011-07-05
Try this before:
```
$ chmod a+x ./sakis3g
```
then run it normally (not sudo necessary).

Hope it helps.

---

### Post by brunobliss on 2011-07-05
THANK YOU ! IT WORKS!!

can you explain what happened? I need to run more things like this, is it something to do with permissions on my own home folder??

---

### Post by 98cwitr on 2011-07-05
Might want to look at this :)

[http://catcode.com/teachmod/chmod_cmd.html](http://catcode.com/teachmod/chmod_cmd.html)

a = All users
x = execute

You didn't have execute permissions on that file. It would also be a good idea to just move that file to your home directory and run it from there where you have recursive ownership.

---

### Post by papibe on 2011-07-05
The file didn't have execution permissions. Take a look at this tutorial [Ubuntu File Permissions]("https://help.ubuntu.com/community/FilePermissions").

Regards.

---

### Post by brunobliss on 2011-07-05
but all these scripts are inside my home folder, that specific one was on my desktop just for testing ....

I noticed that i can run other scripts once i apply the permissions mentioned above, but, i also noticed i have to do this everytime even though things are in my home folder!

maybe this has to do with the backup i made from my old ubuntu installation to the new one?

---

### Post by 98cwitr on 2011-07-05
run this 

chown -R *username* ~/

you'll get a few errors probably, but they can be ignored.

---

### Post by brunobliss on 2011-07-06
this seemed to have fixed my issue, still, i tried putting another scripts folder inside my home folder and once again "Permission denied" or "command not found" with sudo, i had to chown -R that folder aswell, but i'll look into it later on and post my feedback here.

thank you all for the support !

---

### Post by brunobliss on 2011-10-03
Alright so i bought a new laptop and stumbled upon this issue again on natty 11.04. Using the chown command to change ownership of my home folder to myself (errr.. redundant but real) returns an error message

```

chown: cannot access '/home/*username*/.gvfs

```so running this, solves it:

```

#umount /home/useraccount/.gvfs
#find . -inum 554009 -exec rm{} \;

After that,

#rm -rf .gvfs

```

---

