---
title: "Installing JTR from tar.gz"
date: 2010-04-04
forum: General Help
---

### Post by spiky001 on 2010-04-04
Ok I installed JTR from the respotoies but it cant check sha512, so I went to openwall website downloaded jtr 1.7.5 as they say this will do 512, when i unpacked it I then followed the instructions on website to install
[http://www.openwall.com/john/doc/INSTALL.shtml](http://www.openwall.com/john/doc/INSTALL.shtml)

the unpacked folder jtr 1.7.5 is in downloads so I done as they said Now i cant find where it is installed when I type john in termial not found looked for run folder found it in jtr folder cd to run still john wont start
Where have i gone wrong plz

---

### Post by SPr on 2010-04-04
In the run directory is there a file called john?
```

cd run
ls

```
will tell you. If it is present then:
```

chmod +x john
./john --test

```

---

### Post by spiky001 on 2010-04-04
ta that worked, so do i have to cd to run then ./john everytime? if so is it possible to move it to another folder, when I installed from repo I cld just type john it would run or should I reinstall it in usr/share I think it was?

---

### Post by SPr on 2010-04-04
> Alternatively, you may copy the entire "run" directory to anywhere you like and use John from there. From your link. I would keep it in my home dir.

Out of curiosity what are you using it for?

---

### Post by spiky001 on 2010-04-04
well it was 2 reasons 1st to use command line more then out of curiosity check my password on server now it looks like 3 learn how to install tar it,s ok with click and go but I keep seeing how good command line is must make an effort thats all

---

### Post by SPr on 2010-04-04
Fair enough I suddenly wondered just what I was becoming an accomplice to LOL.

Using the command line unlocks the real power of Linux. Anyone who refuses to use it missing something special.

---

### Post by spiky001 on 2010-04-04
It,s not easy when all you have used is widows although ubuntu makes it easy to click and go as well thks for help anyway

---

