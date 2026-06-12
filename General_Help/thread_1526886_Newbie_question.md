---
title: "Newbie question"
date: 2010-07-08
forum: General Help
---

### Post by Ziton on 2010-07-08
HI
I'm new to ubuntu.
I'm trying to get my US Robotics external serial modem working so I can use Ubuntu.
This is a pretty steep hurdle for me.
I copied
 wvdial & dependencies:
libuniconf4.6
libwvstreams4.6-extras
libwvstreams4.6-base
to a flash drive.
How do I get them to /var/cache/apt/archives?
I tried to copy and drag&drop wont work.

thanks

---

### Post by mikewhatever on 2010-07-08
You need to open Nautilus file browser with admin privileges. In a terminal window, type **gksudo nautilus**, then copy away.

---

### Post by dabl on 2010-07-08
With your USB stick connected, open a terminal window.

```
sudo mount
```

Study the output to determine which drive is the USB stick.  Let's assume it is /media/disk-1.

Next:
```

cd /var/cache/apt/archives
```

```
sudo cp /media/disk-1/libuniconf4.6 .
```

You should see the light on the USB stick flash.

Do this for each file that you need (use the up-arrow, and then retype just the file names).

I have no clue if this is going to make your modem work, I'm just answering the question you asked.  :)

EDIT: Ubertypist Mike beat me, with an equally effective solution.  :)

---

