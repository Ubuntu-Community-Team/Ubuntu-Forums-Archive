---
title: "Some programs won't open for me anymore"
date: 2011-04-05
forum: General Help
---

### Post by polardude1983 on 2011-04-05
I tried starting Mangler and it just won't open anymore. Not sure what even caused this in the first place.

Here is what i get by trying to open it through Terminal

```
christoph@christoph-desktop:~$ mangler

(process:3788): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
Can't set the specified locale! Check LANG, LC_CTYPE, LC_ALL.
christoph@christoph-desktop:~$ 

```

---

### Post by polardude1983 on 2011-04-05
up

---

### Post by polardude1983 on 2011-04-06
up

---

### Post by polardude1983 on 2011-04-06
up

---

### Post by polardude1983 on 2011-04-06
up

---

### Post by techunit on 2011-04-06
This isn't the way to get your problem solved. You have provided no information that is useful to fixing your problem. It simply appears that it is missing components.

You might try the following commands

```
sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo dpkg --configure -a
```

Good Luck.

---

### Post by polardude1983 on 2011-04-06
I apologize but what information do I need to provide? Other then what the terminal prints out.

---

### Post by polardude1983 on 2011-04-07
> **techunit said:**
> This isn't the way to get your problem solved. You have provided no information that is useful to fixing your problem. It simply appears that it is missing components.

You might try the following commands

```
sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo dpkg --configure -a
```

Good Luck.

Unfortunately the above commands did not work. Please tell me what Information I need to provide, so i can provide it

I am running Ubuntu 10.10

---

### Post by polardude1983 on 2011-04-07
Well i just restarted my pc, and everything works again. I don't know what happened to fix it. Sorry for anybody else who comes finding the answer. I don't even know how this happened in the first place. Just a linux quirk I guess :D

---

