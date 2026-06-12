---
title: "recoving ubuntu (crashed from my own blunder)"
date: 2009-10-12
forum: General Help
---

### Post by lalamax3d on 2009-10-12
i m sorry, for what i just did. but need guidance anxiously.

ubuntu was working fine, i had updated kde on that and using kdm, even that was fine.
i had multiple versions of python installed(2.5, 2.6, 3.0), i wanted to make sure that certain apps / modules using only python2.5. didn't find a way, so i thought about unintalling python (newer ones)

so i opened synaptic and removed python 2.6 and 3.0. it showed me those in red. and 1.6 GB removal of data. i thought for a second, python installation is quite huge in size, and without noticing detail, hit apply.
now it removed, i m not sure, but lot of things (kde and i don't know what else)

i know, when restarted, pc logged in on a black screen(terminal)

don't want to format partition and reinstall. there is so much data on my main drive / documents / home folder. i can see all this from with in terminal.

is there a way to fix it? e.g
1- simple command, so old ubuntu or new kde pops up back, magically??
2- insert ubuntu boot cd, and tell it to fix already installed version, so it come to factory state (default) without disturbing my account / installed apps (blender/ gimp/ etc)

hope to hear soon and once again, i promise i won't do that again
regards, lala

---

### Post by nothingspecial on 2009-10-12
```
sudo apt-get install kubuntu-desktop
```

You may have to manually connect to the internet. If you don`t know how, post back.

---

### Post by lalamax3d on 2009-10-12
ok, i tried, didn't worked, its giving some error, most probably, not connected to internet. just go back, looked at them in detail.
its saying that cannot initiate connection to proxy(172.26.143.12:8080) .... (101 network connection unreachable)

---

### Post by monkeyKata on 2009-10-12
If you can't get your install working again, I think it's possible to boot into a liveCD and access your drive and files, then transfer them over to another computer or external hard drive... right?

---

### Post by monkeyKata on 2009-10-12
> **nothingspecial said:**
> ```
sudo apt-get install kubuntu-desktop
```

You may have to manually connect to the internet. If you don`t know how, post back.

Maybe this

---

### Post by lalamax3d on 2009-10-12
yup, last solution, but too much work. too much data to move. too many things to take care of. 
i m sure, there must be a way via live CD, it should detect previous installed ubuntu and give me an option to fix this>> by copying missing files, or copying all the source files of ubuntu: but keeping my account / documents as is
option is too logical, even win xp does this.... it repair it self ...

---

### Post by zer0x on 2009-10-13
Hi,

This should get you started:
[URL="https://help.ubuntu.com/community/LiveCdRecovery"]
https://help.ubuntu.com/community/LiveCdRecovery[/URL]

HTH

zer0x

---

