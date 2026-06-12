---
title: "write protect without nautilus icon"
date: 2010-02-19
forum: General Help
---

### Post by cong06 on 2010-02-19
This is kind of a shot in the dark...
I want to "write protect" icons on the desktop of a public computer in order to prevent them from being deleted.

What I don't want is those "lock" icons showing up overtop to show that the files are write protected.

I guess I could write protect the desktop, but I want to allow people to use it as a place to temporarily store files, and if files are downloaded there it makes them easy to see.

Any ideas?

---

### Post by amsterdamharu on 2010-02-19
You can open the console and run the following commands:

```
cd ~/Desktop
sudo chmod 555 -R *
```

Chances are the lock icon will appear because now the files are read only and executable to everyone but root.

---

### Post by cong06 on 2010-02-20
> **cong06 said:**
> What I don't want is those "lock" icons showing up overtop to show that the files are write protected.

> **amsterdamharu said:**
> Chances are the lock icon will appear because now the files are read only and executable to everyone but root.

You've found the problem... I wonder where the icon is stored so that I can 'delete' it.

---

### Post by cong06 on 2010-02-20
I wish there was a better way (like removing the delete option from the icon) But this might just have to do:

The "~/.icons" folder is an override for the folder /usr/icons/
so what I did was I made the folder:
```

mkdir -p ~/.icons/Human/scalable/emblems/

```

Then I touched the files, to make blank over-rides:
```

cd ~/.icons/Human/scalable/emblems/
touch emblem-nowrite.icon emblem-nowrite.svg

```

So, if someone has a way to remove the delete option that would be so much better... until then this kinda works.


Edit: It doesn't. I forgot that having a file 'write-disabled' doesn't prevent it from being deleted.

---

