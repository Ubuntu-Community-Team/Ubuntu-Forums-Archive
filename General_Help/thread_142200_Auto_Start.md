---
title: "Auto Start"
date: 2006-03-09
forum: General Help
---

### Post by JoshHendo on 2006-03-09
Hello. Recently I installed adesklets. It works great :). The only thing I wish to do is start it every time that I login. I know that to start it to the provious configuration for my acocunt I just have to type in "adesklets" (no quotes) into the terminal and it will run. Is there a way to make it so that terminal command will just run once every time I login? Thanks!

---

### Post by Xian on 2006-03-09
You mean like System > Prefs > Sessions > Startup Programs ??

---

### Post by JoshHendo on 2006-03-10
I tried that though it doen't work fully. Sometimes, it will just start adesklets for a second or so, though as soon as everything has finished loading, it gets out of it.

---

### Post by JoshHendo on 2006-03-10
Bump..

I have tried everything, though I still can't work it out :(

Thanks if you can help :D!

---

### Post by yabbadabbadont on 2006-03-11
You have to add the --nautilus option for it to work with gnome.  You will also probably want to add a delay to its startup by adding the -d option.  I use:

adesklets -d 5 --nautilus

The only problem I've run into, is that it isn't killed when I log out.  Then when I log back in, it either doesn't work, or there are two copies running in the process list.

I guess I'll have to figure out how to start gnome from .xinitrc and remove xdm from the system startup scripts.

---

