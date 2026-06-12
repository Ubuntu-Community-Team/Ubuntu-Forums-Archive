---
title: "I need to mount a cd manually"
date: 2010-06-16
forum: General Help
---

### Post by maxrpowell on 2010-06-16
problem: for some reason xubuntu does not mount cds manually as does ubuntu. i need to burn an iso file to a blank cd and brasero insists that i do not have a cd in the drive. hmmm...?? how do i manually mount the cd? terminal time maybe :) thanks for help

---

### Post by angry_johnnie on 2010-06-16
this should work:

```
wodim --devices
```

the output should be something like /dev/sdX, where /dev/sdX is your drive.

create this directory if it does not exist already:

```
sudo mkdir /media/cdrom0
```

then

```
sudo mount -t iso9660 /dev/sdX /media/cdrom0/
```

---

### Post by maxrpowell on 2010-06-16
the first code returns this:

> wodim: No such file or directory. 
Cannot open SCSI driver!
For possible targets try 'wodim --devices' or 'wodim -scanbus'.
For possible transport specifiers try 'wodim dev=help'.
For IDE/ATAPI devices configuration, see the file README.ATAPI.setup from
the wodim documentation.


---

### Post by angry_johnnie on 2010-06-16
:o
that's odd...
i just copied/pasted that same code on a terminal, and it worked.

its also funny how it tells you "For possible targets try 'wodim --devices' or 'wodim -scanbus'."

so, it's telling you to run the same code you just entered...

seems more like a glitch in wodim than anything else.


anyway, cd drives are usually scd.

try

```
ls /dev | grep scd
```

i have two, so it tells me scd0 and scd1.
if  you only have one, it should be scd0.

so try the rest of the code, based on that.

hope it helps :p

---

