---
title: "using traps with dd in bash shell scripts"
date: 2009-09-06
forum: General Help
---

### Post by motoperpetuo on 2009-09-06
i wrote the following short shell script to copy the contents of a CD to an .iso file:
```

#execute control01 function if user tries ctrl-c
trap "control01" SIGINT SIGTERM

#build iso
echo "Creating $1."
dd if=/dev/cdrom of=/home/$USERNAME/$1 bs=2048 conv=sync,notrunc
echo "Done."

```

"control01" is a function that warns the user that the .iso will be unuseable if he quits and asks if he really wants to quit:
```

#function to ask if user really wants to quit
control01 ()
{
echo -n "Do you really want to quit? The iso will not be useable. (y/n)"
read stayorgo
if [ "$stayorgo" = "y" ];then
exit 11
fi
}

```
if i run the script and then hit ctrl-c while the .iso is being created, the trap activates and the script asks me "Do you really want to quit? The iso will not be useable. (y/n)". However, no matter what I answer, the script quits. I'd like to be able to answer 'n' and have the script continue to create the .iso. I've successfully used similar traps to ask "Do you really want to quit?" in other scripts, so I wonder if dd is just incompatible with the kind of trap or something like that. If anyone has any idea, please let me know. thanks!

---

### Post by scragar on 2009-09-06
This works perfectly for me. Can't find your problem, might be worth trying to run bash with debug mode on.
Code I tested with:```
#!/bin/bash

trap "control01" SIGINT SIGTERM
control01(){
        echo -n "Do you really want to quit? The iso will not be useable. (y/n)"
        read stayorgo
        if [ "$stayorgo" = "y" ];then
                exit 11
        fi
}

for I in {1..20}; do
        echo $I
        sleep 1
done
```
EDIT: change the shebang to **#!/bin/bash [color=red]-x[/color]** to enable debug.

---

### Post by motoperpetuo on 2009-09-06
i actually tried almost exactly what you did there as a test and yes, it works perfectly. i think it's something specific about the dd command that doesn't work with this trap.

i tried debug mode (thanks for advice, btw), and the output i got after answering 'n' to "Do you really want to quit?" was:
```

Do you really want to quit? The iso will not be useable. (y/n)++ read stayorgo
n
++ '[' n = y ']'
+ echo Done.
Done.

```
if i understand this correctly, the control01 function sees that i answered 'n' and not 'y', so it passes control back to the script, but the script terminates anyway. maybe you just can't halt dd while it's in progress and then make it resume?

---

### Post by scragar on 2009-09-06
OOh, I just tried it, that is strange.

For an explination it works like this, when you press ctrl+c dd closes it's file link, in my test case this was to /dev/zero, in your cases it was /dev/cdrom once it's closed dd is forced to quit.

I came up with a bit of a work around:
```
#!/bin/bash

dd if=/dev/cdrom of=/home/$USERNAME/$1 bs=2048 conv=sync,notrunc &

export ddspid=$! **## we need this PID for later. Don't lose it.**

trap "wannaQuit" SIGINT SIGTERM

WannaQuit(){
        echo -n "Do you really want to quit? The iso will not be useable. (y/n)"
        read -n 1 stayorgo
        if [[ "$stayorgo" = "y" || "$stayorgo" = "Y" ]];then
                kill -9 $ddspid
                exit 11
        fi
}

while [ ! -z  "$(ps $ddspid | grep $ddspid)" ]
do **## don't let the bash script exit or continue till dd stops**
        sleep 1
done
```

---

### Post by motoperpetuo on 2009-09-08
awesome! very nice workaround. thanks for showing me that.

---

