---
title: "Accidentally enabled the root account..."
date: 2006-05-07
forum: General Help
---

### Post by subxero on 2006-05-07
I meant to change my password, but I was dumb and typed "sudo passwd" instead of just "passwd".

Anyway, I looked around a bit and disabled the root account, but now all administrative tasks (anything graphical, specifically) uses the default hard-edged GTK theme and really doesn't look good with the rest of my desktop. I'm obsessive-compulsive and am very, very picky about computer aesthetics.

Is there a way to fix this?

---

### Post by nanotube on 2006-05-08
hmm, i am not sure exactly what's going on... but read through [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)
and see if anything looks helpful...

---

### Post by bluevoodoo1 on 2006-05-08
For part two of your question...

[http://ubuntuforums.org/showthread.php?t=77694](http://ubuntuforums.org/showthread.php?t=77694)
look at step four.

---

### Post by aysiu on 2006-05-08
Go to Applications > Accessories > Terminal and type ```
sudo ln -s ~/.themes /root/.themes
sudo ln -s ~/.icons /root/.icons
```

---

### Post by subxero on 2006-05-08
I read the Wiki article, it didn't contain anything that helped. Thank you, however.

I tried the other suggestions (linking the root's theme/icon/font configuration to my own) and it didn't work either.

How, then, are the programs executed with gksudo or whatever skinned when Ubuntu is first installed? Is there some configuration option or configuration file that controls this behavior?

---

### Post by aysiu on 2006-05-08
[QUOTE=subxero]
How, then, are the programs executed with gksudo or whatever skinned when Ubuntu is first installed? Is there some configuration option or configuration file that controls this behavior?[/QUOTE] Even though you can't log in as root in the default Ubuntu, the root account exists, and in a standard Ubuntu installation, the instructions I gave you would have worked. I'm not sure what the deal is now that you've enabled root.

When you say the Wiki didn't help, you tried [this](https://wiki.ubuntu.com/RootSudo#head-b06dbcd33c40480dcfd3aada1ca67bbd77f80594) specifically? What happened when you did?

---

### Post by subxero on 2006-05-08
When I execute "sudo passwd -l root" in a terminal, it tells me "Password changed."

I use Automatix -- this behavior started long after I started to use Automatix, so it's not its fault, but could Automatix have anything to do with why the normal fix isn't working? I've read that Automatix has some adverse effects on various things here and there, but that was when I was using Windows, so I didn't read a whole lot into it.

---

### Post by aysiu on 2006-05-08
No idea about Automatix. Maybe ask Arnieboy (the author)?

---

