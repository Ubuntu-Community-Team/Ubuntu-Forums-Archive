---
title: "Simple problems with bash (environment variables) and grep"
date: 2011-09-14
forum: General Help
---

### Post by KidDisaster on 2011-09-14
ok im having problems. 

1) I can't figure out where i am suppose to store my environment variables

i've tried bashrc .profile .bash_profile bash.bashrc in my root directory and my home (kiddisaster) directory...at the end of all of these files I included :

FULLNAME="CAMERON"
$FULLNAME="CAMERON"

when i logout and log back in and type echo $FULLNAME it is just empty. 

but i added an environment (COUNTRY="USA") variable from the command prompt...and it works fine...so by common sense thinking i was like 'oh ill use grep and find out where they're stored' 

tried grep -l "COUNTRY" * ...didn't work..

grep -i "home" * ....came up with nothing (the word home is in like...a million files....)

so i replaced the asterik with an actual directory....returned nothing

but i tried grep -i 'home' /etc/passwd and that worked...
what the hell is going on here...and why can't i easily edit these damn bash files and add variables...

---

### Post by mue.de on 2011-09-14
I'm not quite shure, but does > env|grep "home" gives a result ?

---

### Post by KidDisaster on 2011-09-14
root@kiddisaster-P-6860FX:~# env|grep "home"
PWD=/home/kiddisaster
HOME=/home/kiddisaster


yea that gave a result....but im searching for "FULLNAME" or "COUNTRY" ...i've added fullname to every file...and through command line added country as a variable ...but env|grep "FULLNAME" env|grep "COUNTRY" come back with no result ...when i know for a fact that atleast FULLNAME should be showing up...

---

### Post by KidDisaster on 2011-09-14
just did this:

root@kiddisaster-P-6860FX:/# export CAM="YES"
root@kiddisaster-P-6860FX:/# echo $CAM
YES
root@kiddisaster-P-6860FX:/# env|grep CAM
CAM=YES
root@kiddisaster-P-6860FX:/# grep -i "CAM"
no results


im wanting to find WHERE CAM=YES is stored...is there any way i can do this...

---

### Post by KidDisaster on 2011-09-14
root@kiddisaster-P-6860FX:/# grep -i "CAM" *
Binary file initrd.img matches
Binary file vmlinuz matches


...ummm.....

---

### Post by KidDisaster on 2011-09-14
ah nevermind.../etc/profile decided to start working!

---

