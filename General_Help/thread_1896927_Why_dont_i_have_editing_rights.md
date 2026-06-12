---
title: "Why dont i have editing rights???"
date: 2011-12-18
forum: General Help
---

### Post by tears of the river on 2011-12-18
I have just made new partitions and now am trying to create new folders and pasting folders into them but for some reason i think i dont have administrator rights as when i right click i cant create new folders, create new documents, clean up by name, and no paste options

what should i do ??? 
:confused:

---

### Post by SnickerSnack on 2011-12-18
Some basic questions:

Are you using nautilus or another file manager?

How did you create the partitions?

What filesystem are they?

Have you tried moving the folders from the terminal using sudo?

---

### Post by howefield on 2011-12-18
Change the permissions for the partition(s) that you cannot write to, eg I have created a new partition on my drive called Testing, to be able to write to it I'll run the following command...

```
sudo chown hugh /media/Testing
```

---

### Post by tears of the river on 2011-12-18
> **SnickerSnack said:**
> Some basic questions:

Are you using nautilus or another file manager?

How did you create the partitions?

What filesystem are they?

Have you tried moving the folders from the terminal using sudo?

im not sure about what file manager im using i guess its the default one in ubuntu 10.04 coz i dont think ive changed it

i created the partiotions usuing gparted live cd

i cant remember what file systems they are

no i dont really know how to move folders using terminal

---

### Post by tears of the river on 2011-12-18
> **howefield said:**
> Change the permissions for the partition(s) that you cannot write to, eg I have created a new partition on my drive called Testing, to be able to write to it I'll run the following command...

```
sudo chown hugh /media/Testing
```

i tried it but the result comes:


chown: invalid user: `hugh'

what should i do????

---

### Post by lisati on 2011-12-18
> **tears of the river said:**
> i tried it but the result comes:


chown: invalid user: `hugh'

what should i do????

Instead of "hugh", use your own username.

---

### Post by howefield on 2011-12-18
> **tears of the river said:**
> i tried it but the result comes:


chown: invalid user: `hugh'

what should i do????

Sorry, too early on a Sunday morning for me ... I should have said to change the user name to whatever yours is and the name of the drive/partition to whatever yours is.

My apologies.

---

### Post by tears of the river on 2011-12-18
> **howefield said:**
> Sorry, too early on a Sunday morning for me ... I should have said to change the user name to whatever yours is and the name of the drive/partition to whatever yours is.

My apologies.

no problem but now that ive changed the username it isnt detecting the partition 
the partition's name is D drive when when i type that in the result is:

chown: cannot access `/media/D': No such file or directory
chown: cannot access `drive': No such file or directory

---

### Post by nothingspecial on 2011-12-18
If there is a space in the name you have to escape it

```
sudo chown $USER:$USER /media/D\ drive
```

$USER will expand to your username so you can copy and paste :)

---

### Post by tears of the river on 2011-12-18
Thanks Everyone You were a lot of help problem has been solved and am now marking it so

i must say that it was the quickest fix i ever did like in 20 mins thanks to you guys 

:D :popcorn:

---

### Post by tears of the river on 2011-12-18
Sorry guys :( but i tried the same thing on my main partition that is File System but it didn't work this came up

chown: cannot access `/media/File System': No such file or directory

how do i change the admin rights of File System??

:confused:

---

### Post by howefield on 2011-12-18
This sounds like a bad idea, if by File System you mean / ?

If you need to write to / use the sudo command.

---

### Post by tears of the river on 2011-12-18
> **howefield said:**
> This sounds like a bad idea, if by File System you mean / ?

If you need to write to / use the sudo command.

thanks

---

