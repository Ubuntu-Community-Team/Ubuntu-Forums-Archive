---
title: "Firefox won't start"
date: 2010-07-04
forum: General Help
---

### Post by pkimga on 2010-07-04
I can't get my Firefox to start, I press the FF icon and it says that it's starting, but then it disappears, no window opens. The process seem to start though, when i check in the terminal it says that it's running and if I try to start it again, it says it's already running. I've tried to uninstall/reinstall several times, but nothing changes. No error message is appearing at any time.

---

### Post by J V on 2010-07-04
run firefox from a terminal to see what errors are being thrown.

Open a gnome-terminal from accessories and type in "firefox"

---

### Post by happyhamster on 2010-07-04
- In a terminal, run:

killall firefox

killall firefox-bin

- Then start firefox again:

firefox

- If that doesn't work, rename the folder ~/.mozilla/firefox/ to something else, then restart firefox again (this will create a new, default profile). The folder is in the hidden .mozilla folder in your home directory. (To see hidden stuff in nautilus: press ctrl-h.) Good luck.

---

### Post by pkimga on 2010-07-04
It doesn't say anything when i type it in the terminal. I changed the name on the folder and now i can't see the firefox processes in the terminal (I wrote ps -x). It still says that is already running though.

---

### Post by lovinglinux on 2010-07-04
Looks like you have just installed Ubuntu 10.04 right? Have you updated it? If not, then open a terminal, paste the following commands and hit Enter:

```

sudo apt-get update
sudo apt-get upgrade

```

If you don't like the terminal, you can do that from "System >> Administration >> Update Manager".

This problem with Firefox started recently or since you installed Ubuntu?

Have you tried the command **killall firefox-bin** as already suggested?

---

### Post by pkimga on 2010-07-04
Tried all of it, I installed a couple of weeks ago I think, problems with firefox started like a day or two ago, don't remember that anything special happened, just didn't start. Now I'm using Opera, does anyone know about the function that tricks the sites to think that I use IE or FF? Only read about it, but haven't figured out have it work, need it to log in to some sites.

---

### Post by lovinglinux on 2010-07-04
> **pkimga said:**
> Tried all of it, I installed a couple of weeks ago I think, problems with firefox started like a day or two ago, don't remember that anything special happened, just didn't start. 

If you are running Firefox 3.6.6, try to delete the file secmod.db from your Firefox profile and start it.

If that doesn't help, then see if the command below works:

```
firefox -no-remote
```


> **pkimga said:**
> Now I'm using Opera, does anyone know about the function that tricks the sites to think that I use IE or FF? Only read about it, but haven't figured out have it work, need it to log in to some sites.

[https://addons.mozilla.org/en-US/firefox/addon/59/](https://addons.mozilla.org/en-US/firefox/addon/59/)

---

### Post by happyhamster on 2010-07-04
Perhaps there's a permission problem? Could you show the output of:

ls -l ~/.mozilla

ls -l ~/.mozilla/firefox

---

