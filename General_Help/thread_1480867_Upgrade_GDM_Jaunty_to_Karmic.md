---
title: "Upgrade GDM Jaunty to Karmic"
date: 2010-05-12
forum: General Help
---

### Post by Cenwio on 2010-05-12
Hi!

I want to upgrade my Jaunty GDM to the GDM of Karmic. My goal is to have the same login screen in Jaunty that now exists in Karmic. 

I've Googled to find some commands on how to upgrade jist the GDM, but haven't found anything yet.

---

### Post by Cenwio on 2010-05-12
bump

---

### Post by Cenwio on 2010-05-12
Any ideas anyone...plz

---

### Post by warfacegod on 2010-05-12
If I were you I wouldn't do what your looking to do. GDM 2.20's Login screen app is superior to GDM 2.28

The Login screen app in 2.28 is extremely dumbed down with no ability to change splash screens.

I would go to [http://gnome-look.org/]("http://gnome-look.org/") and find the splash and install it with GDM 2.20

---

### Post by Cenwio on 2010-05-14
Hi,

I already know the limitations of GDM 2.28 but I need to use for various reasons.. 

Any guidelines on how to update GDM to 2.28 in Karmic, anyone?

---

### Post by Cenwio on 2010-05-14
Anyone?

---

### Post by warfacegod on 2010-05-14
You could try:

```
sudo apt-get install gdm2.28
```

---

### Post by Cenwio on 2010-05-17
Thanks, but I get "E: couldn't find package gdm2.28", and I can't seem to find the Karmic repository..

---

### Post by warfacegod on 2010-05-17
You'll need to rename this to drop the .zip at the end, then just double click it. I got this from Synaptic 9.10. I have no idea if installing gdm 2.28 into 9.04 will totally frag your system. If it does, don't hold me responsible. I will help you fix it if the need arises.

---

### Post by Cenwio on 2010-05-18
Thanks Warfacegod. I'll test this right away. I've made an image backup with CloneZilla so I have something to restore from.

---

### Post by Cenwio on 2010-05-18
Ok, I give up. When I try to install the package I get alot of dependecy problems, which ultimately points me to upgrade the whole libc6 package - which I'll never do.. I'll let this one be I think.

---

### Post by warfacegod on 2010-05-18
That's what I figured would happen. There's always that gnome-look site I posted, you should be able to find the 9.10 splash there so you'll have that at least. To bad there isn't a "Sort of Solved" option.

---

### Post by Cenwio on 2010-05-20
Yup, to bad :| Thanks for your guidance anyway.. I would probably be stuck in this still if it were'nt for your help, so thanks!

---

### Post by warfacegod on 2010-05-20
Glad I could help even though you didn't get what you wanted.

---

