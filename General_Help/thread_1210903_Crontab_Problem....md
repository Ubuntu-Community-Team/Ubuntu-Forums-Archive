---
title: "Crontab Problem..."
date: 2009-07-12
forum: General Help
---

### Post by WongFuChu on 2009-07-12
Well, I never had this before when trying to set up a crontab for a tmpfs script for firefox. I had to reinstall eeebuntu and recreate one. Did the following steps... I don't know where I messed up, but whenever I put in:

crontab -u myusername -e

some number (62) shows up. Anything I put into the terminal + enter only returns a ?

help please!

---

### Post by akudewan on 2009-07-12
What is the output of crontab -l ?

---

### Post by WongFuChu on 2009-07-12
Something like...

# (the stuff that's like M, DOM...)
*/1 * * * *   $HOME/.packed_ffox.sh

I can't really remember the exact stuff (I'm on a windows pc now and letting my computer charge as I'm working on some school project), but that's what's basically in there. I got it to work now, btw. I had to do chmod +x .packed_ffox.sh then sh .packed_ffox.sh two times (without the sh, i got some kinda error).

Anyway, I'm more concerned about the crontab editor and why I get the number 62 rather than the editor.

---

### Post by akudewan on 2009-07-12
nano is used as the default editor for crontab. There may be some problem with nano. Try running: ```
nano somefile
``` in a terminal to check if nano is working correctly.

You can change the default editor by running:
```

export EDITOR=/usr/bin/gedit

```

This will change the editor to gedit, assuming you have the X server running. (The change will be temporary, only until you quit the terminal). You could also try vim or emacs if you're comfortable with it.

---

