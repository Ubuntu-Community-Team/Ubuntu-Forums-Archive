---
title: "System back up and restore?"
date: 2011-08-06
forum: General Help
---

### Post by stevennlv on 2011-08-06
OK, so I've got 11.04 hacked up and tweaked out just the way I want and running sweet.

I've established what I consider to be a "baseline" state. But, I'm sure I'll tinker with it more as time goes on.

So, how do I back everything up and create a set of system restore disks?

If I doof around and blow it up all I want to have to do to restore every everything that is currently on it is feed the box a few DVDs and viola!

Is there a program / feature that will do that?

If possible I'd prefer something with a GUI; something similar to ToDo / Shadow Protect / Acronis for win.

Thanks for the help.

---

### Post by Basher101 on 2011-08-06
Get Remastersys. It creates a bootable Live CD .iso from your current installation, thus you will have a bootable, pre-configured installation with pre-installed things you have installed on your current ubuntu installation. You can install it by searching in the ubuntu software center. It is a significant backup tool.

---

### Post by daccount10 on 2011-08-06
Deja Dup - change preferences to fit your needs, read the help for more info

---

### Post by Basher101 on 2011-08-06
Oh i forgot to mention, Remastersys has only one limitation: space. Keep your "basic" configuration (programs included) as small as possible. The .iso that Remastersys creates must be less than 4 GB, otherwise it wont backup. Also, on the bootable iso you wont have the "Install 11.04" on the desktop. You will be able to install it from your System preferences. There should be a new icon with RELEASE install next to it. Otherwise you can install it with a command: ```
sudo ubiquity --desktop %k gtk_ui
```

---

### Post by dFlyer on 2011-08-06
> **daccount10 said:**
> Deja Dup - change preferences to fit your needs, read the help for more info

1+ for Deja Dup. I've been using it for the last two releases. If you wish to clone the whole system, I'd recommend clonezilla.

---

### Post by Basher101 on 2011-08-06
I once tried to use/install clonezilla and failed. Remastersys did its job formidably for me. I also looked at some threads how to install it but i could not. Does clonezilla have the same limitations? does it create a bootable image? or just copy the files?

---

### Post by stevennlv on 2011-08-06
I appreciate all the info.

I don't think a 4 GB limit will do what I need.

I'm just converting from win after 20 years and am still most comfortable with point and click (although I'm learning).

In win they have programs, like the ones I listed above, that back up everything on the drive. Every picture, song, program, system setting: the whole shabang.  And then if you're install goes kaboom you just boot from a restore DVD and then sit there and feed your box maybe 4 to 10 DVDs (just depending on how much stuff you had on the drive) and then you were automaigically completely and totally restored like old (er, new). You get what I mean. The only stuff you lost was whatever you did after your last backup. 

And some of the better win programs had incremental back up systems so that you didn't have to waste DVDs constantly backing up the whole thing. You could just back up the newest stuff, from the time of your last back up.

Those types of programs are one of the few good things about win. I'm hoping there's something like it here. If I blow up my box I don't want it to take more than about 45 minutes to get everything, and I mean _****EVERYTHING****_ back.

Thanks for the help.

---

