---
title: "Wide HDD Clean"
date: 2010-05-22
forum: General Help
---

### Post by FinalShot on 2010-05-22
I want to write all 0's to my HDD, only 1 pass, what would be the appropriate command? And will I have to boot up a live cd to execute the command?

---

### Post by jamesisin on 2010-05-22
Maybe understand what you are ultimately trying to accomplish will help get you the most useful answer.

---

### Post by wieman01 on 2010-05-22
> **jamesisin said:**
> Maybe understand what you are ultimately trying to accomplish will help get you the most useful answer.
Lol... that's kind of true.

Do you want to erase your data?

---

### Post by bumanie on 2010-05-22
> dd if=/dev/zero of=/dev/sdxMake sure you replace the x with the appropriate drive letter eg /dev/sda if it is the first or only hard drive in the computer. This can be done from a live cd or from a linux installation if the drive to be zereoed is a drive other than one with linux installed on it.

---

### Post by FinalShot on 2010-05-22
Ok I entered that, can I check the progress?

---

### Post by wieman01 on 2010-05-22
You can't, just watch the HD's LED that indicates activity. Depending on the size of your harddisk, it can take a while, even a few hours.

---

### Post by rnerwein on 2010-05-22
> **wieman01 said:**
> You can't, just watch the HD's LED that indicates activity. Depending on the size of your harddisk, it can take a while, even a few hours.

hi guy
that's a very good answer ( perfect ! ) :-) :-) :-)
have fun
ciao

---

### Post by bumanie on 2010-05-22
AS far as I remember, when dd has finished it will show an output in terminal saying how many bytes were inputted and outputted.

---

### Post by FinalShot on 2010-05-22
You can actually check the progress, currently @ 70GB :( Fair bit to go yet...

---

### Post by jamesisin on 2010-05-22
Be nice if you said HOW...

---

### Post by wieman01 on 2010-05-23
100 GB took about 6 hours last night.

---

### Post by wieman01 on 2010-05-24
One more thing you could do by the way... It's way faster. Install **"Truecrypt"** and encrypt the entire partition. It will overwrite it with random data and takes only about 2 hours for a 250 GB volume.

---

### Post by jamesisin on 2010-05-24
Still be nice to know how the OP checked the progress.

---

### Post by FinalShot on 2010-05-24
Get the process id of the terminal running dd:

```
$ pgrep -l '^dd$'[FONT=monospace]
[/FONT]8789 dd
```

Then run this:
```
$ kill -USR1  8789
```

---

### Post by jamesisin on 2010-05-24
The man page is a little shy on what -USR1 actually does, but I suppose I could run dd myself and have a look-see.

---

### Post by jerome1232 on 2010-05-24
dd will go alot faster if you tell it to write in larger chunks

ie

```
dd if=/dev/zero of=/dev/sdx bs=1M conv=notrunc
```

I'm not sure what the best numbers are for optimal speed.

---

