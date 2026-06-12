---
title: "Superuser is the devil"
date: 2011-09-30
forum: General Help
---

### Post by skrill on 2011-09-30
i need to load a launcher which is saves as a .run file, every time i open it it says i need to have root acces or super user, ive done the terminal commands to give myself root acces and still it will not open, can someone just give me the commands to load the launcher with root access from the terminal? the file is saved to the desktop, not in a file

thx in advance

---

### Post by haqking on 2011-09-30
> **skrill said:**
> i need to load a launcher which is saves as a .run file, every time i open it it says i need to have root acces or super user, ive done the terminal commands to give myself root acces and still it will not open, can someone just give me the commands to load the launcher with root access from the terminal? the file is saved to the desktop, not in a file

thx in advance

terminal commands to give yourself root access ? if you mean  you unlocked the root account then you dont need to and shouldnt do that.

Ubuntu uses the [ROOTSUDO]("https://help.ubuntu.com/community/RootSudo") so you append sudo or gksudo to commands needing elevated priveleges, the password it requires when you do this is YOUR own password you use to login with.

example

```
sudo <command>
```

Please read the link to grasp this

---

### Post by searchfgold6789 on 2011-09-30
So you're saying that the file is actually a launcher, not a file itself. But then if it were a launcher, it would come up with an error different than what you're experiencing.
Try this:
```
sudo su
./filename
```

---

### Post by dave01945 on 2011-09-30
just do

```
cd Desktop
sudo ./file.run
```

---

### Post by pkg9991 on 2011-09-30
sudo command
and the terminal will ask you for the password..
and your done as the root

---

### Post by skrill on 2011-09-30
ahh yes ty :) i did that earlier but for some unknown reason it didnt work, thanks much :) <3:popcorn:

---

### Post by haqking on 2011-09-30
> **skrill said:**
> ahh yes ty :) i did that earlier but for some unknown reason it didnt work, thanks much :) <3:popcorn:

ok cool.

Make sure you use thread tools to mark this thread as solved.

Cheers

---

### Post by dino99 on 2011-09-30
sudo chown user:user path/to/my/runfile

where user:user is yours

---

### Post by pkg9991 on 2011-09-30
change the title to solved ;)

---

