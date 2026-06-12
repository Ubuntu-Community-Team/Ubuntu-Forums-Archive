---
title: "shred script help"
date: 2011-07-11
forum: General Help
---

### Post by razvedka on 2011-07-11
I am really new to linux and probably getting over my head but got to start somewhere. 
Can anyone help me with making a shell script to run on puppy linux to shred all drives connected to it. I have been able to successfully use the command to wipe all drives connected but cant figure out how to write a script for it. any help would be very appreciated. I have several hard drives i got and want to shred wipe them before using them..
 
Thanks, 
Raz

---

### Post by vamped on 2011-07-12
> **razvedka said:**
>  I have been able to successfully use the command to wipe all drives connected but cant figure out how to write a script for it.

I'm not sure what you want to do. Please be more specific. If you have already been successful in using "the command" (assumed "shred"), and have already wiped all connected drives, then what else do you wish to do?

For more information on the shred command, type "man shred" at the command prompt.

---

### Post by razvedka on 2011-07-12
here is what i would like to do .
 
locate all hd's connected to the computer
Then ask how many times to wipe 
then just show the progress. I have a couple of boxes of drives /about 100 of them varrying in size and type from sata to ide. Im looking to remove the ones I wipe and put more on and run a script for it. 
Hope that makes sense.
 
make it more automated to where i just input the values and it does its process.

---

### Post by Spyderkid on 2011-07-12
okay that shouldn't be too hard.....
i'm not sure for all of it but i can help.......

```

echo "how many times do you want to re-write?"
read WIPE
echo "what drive would you like to wipe?"
read DRIVE
shred -n $WIPE -v $DRIVE

```

Im not sure how to do them all automatically

---

### Post by Spyderkid on 2011-07-12
oh btw what i just did was in bash.... hope thats ok

---

### Post by razvedka on 2011-07-12
THank you very much that works great , much better than typing in the syntax each time. Maybe I can figure out how to have it print the connected drives right after it ask for how many times to wipe.
this helps alot thank you very much !!!!

---

### Post by Spyderkid on 2011-07-15
no problem XD

---

### Post by KeyserSoze93 on 2011-07-15
EDIT: Ignore post. Just realized there's some stuff in the script that won't work on a generic system setup.

---

