---
title: "I Want Bring  Menu option Back"
date: 2011-04-29
forum: General Help
---

### Post by DR.JJ on 2011-04-29
Hi yall,
Actually before I post this new thread. I checked the forum, and I couldn't find any answer for my question. :(.
Yesterday I upgraded my Ubuntu 10.4 to new version 11. In during installation I don't really remember which option I choose for installing Ubuntu root direction, but after installation completed computer asked for restarting. I restarted computer, and after I restarted the computer, computer should bring up  Menu to choose Windows Or Linux, but this time automatically after a few second screen turn black and than Ubuntu show up. But I don't want that because I want choose Windows, and now I don't have any Idea how should I bring the Menu back. :confused: 
Can anyone help me please :icon_frown: I really new to work with windows, and please don't tell me to format my Hard Drive :(
Thanks.

---

### Post by cymbaline42 on 2011-04-29
If you used the entire hard disk to install Ubuntu 11.04, then Windows would have got erased. 

Is this what you did?

---

### Post by randallecook on 2011-04-29
You need to restore the boot manager or boot loader or other such software. Coincidentally, I do too. Look up "grub" and boot loaders. I expect you'll find some tips there. Good luck. If I find anything relevant I'll post here as well.

---

### Post by howefield on 2011-04-29
Was this a clean install you carried out or an upgrade from the update manager ?

You could try the terminal command

```
sudo update-grub
```

If that doesn't work, what is the output from the terminal command..

```
sudo fdisk -l
```

---

