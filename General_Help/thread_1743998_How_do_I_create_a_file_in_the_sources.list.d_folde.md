---
title: "How do I create a file in the sources.list.d folder"
date: 2011-04-30
forum: General Help
---

### Post by Rlemontw on 2011-04-30
I am using 10.10 and I am trying to download a role playing game and it wants me to do this:

create a file
        called /etc/apt/sources.list.d/unknown-horizons
        in it with the following content:
deb [http://packages.unknown-horizons.org/maverick](http://packages.unknown-horizons.org/maverick) release main

But when I am in the folder I can not create the file unknown-horizons. How can I get this done?

Thanks:D

---

### Post by tgm4883 on 2011-04-30
> **Rlemontw said:**
> I am using 10.10 and I am trying to download a role playing game and it wants me to do this:

create a file
        called /etc/apt/sources.list.d/unknown-horizons
        in it with the following content:
deb [http://packages.unknown-horizons.org/maverick](http://packages.unknown-horizons.org/maverick) release main

But when I am in the folder I can not create the file unknown-horizons. How can I get this done?

Thanks:D

You need admin rights to write to that folder. I'd use the terminal and nano

```
sudo nano /etc/apt/sources.list.d/unknown-horizons.list
```

---

### Post by Rlemontw on 2011-04-30
> **tgm4883 said:**
> You need admin rights to write to that folder. I'd use the terminal and nano

```
sudo nano /etc/apt/sources.list.d/unknown-horizons.list
```

Awesome that worked. I am new to Ubuntu and Linux so I hopefully will learn what all this stuff mean.

One more question - how can I add to that very same file?

:D

---

### Post by bcn17 on 2011-04-30
Use the program "gedit".

Or "nano".

```
sudo gedit /etc/apt/sources.list.d/unknown-horizons.list

OR

sudo nano /etc/apt/sources.list.d/unknown-horizons.list
```

In nano CTRL+X saves.

When you used nano the first time because the file wasn't already created it created the file. However, if the file is there it will open up the file for editing.

Also, you can edit the /etc/apt/sources.list  file instead. 

Just remember, when you are starting to play around with files always make a backup.
```

cp /file/name/here /backup/file/copy
```

Then reverse the command when using your backup. Also, use the man in the terminal. For nano type: "man nano" without the quotes.

---

