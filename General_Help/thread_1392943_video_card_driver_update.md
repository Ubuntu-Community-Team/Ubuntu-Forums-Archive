---
title: "video card driver update"
date: 2010-01-28
forum: General Help
---

### Post by Mashvv on 2010-01-28
hey guys! hows it goin ?! anyways  i have geforce fx 5200  and i downloaded  the 32 bit and 62 bit for the video card driver update and i dont know how to use them and they  and they come in scripts ! i dont know how to run them :( any help would be useful Thanks!

---

### Post by wheredidrealitygo on 2010-01-28
open up the terminal. cd into the directory you've downloaded them to, ex:

```
cd Downloads
```

then run

sudo chmod +x <name of the file>

so if the filename were NVIDIA-DRIVERS-FX5200.run

you'd do:

```
sudo chmod +x NVIDIA-DRIVERS-FX5200.run
```

then just:

```
sudo ./NVIDIA-DRIVERS-FX5200.run
```

*NOTE*: if it says your X server can't be running, you need to do the following:

```
sudo /etc/init.d/gdm stop
```

you'll be given only a prompt, and you'll need to cd to the directory again, then just the sudo ./NVIDIA-DRIVERS-FX5200.run again.

If you want any more specific help than that then you'll need to provide the actual filenames and directories they're located in.

---

### Post by Mashvv on 2010-01-29
Thanks you so much im trying to do wt u told me but i dont know how exactly i open up the terminal them  i dont know wt exactly to do :(

---

### Post by no2498 on 2010-01-29
do NOT do anything till someone ask if what he said is for you
they will need more info
sorry i cant help

---

