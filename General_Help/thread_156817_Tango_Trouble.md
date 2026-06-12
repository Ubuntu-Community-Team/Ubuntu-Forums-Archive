---
title: "Tango Trouble"
date: 2006-04-07
forum: General Help
---

### Post by souteneur3190 on 2006-04-07
How in the world am i supposed to install the tango theme (the original one from the tango website)?  I have absolutly no idea what to do after > ./configure --help.  I just need someone to tell me the commands because ive never installed anything like this before.  Reply ASAP!

Thanks in advance]

---

### Post by dreamsINdigital on 2006-04-07
You could just install it from apt-get.  I think it's up to date.  You probably have to enable universe or multiverse.

---

### Post by souteneur3190 on 2006-04-07
done that, and i have no idea how to access it

---

### Post by shame on 2006-04-07
```
./configure
make
sudo make install
```
If you have any errors post back.
Probably need to install build-essential if you haven't already but I'm not certain.
```
sudo apt-get build-essential
```

To install from repos - ```
apt-get install tango-icon-theme tango-icon-theme-extras
``` if that fails you need to uncomment the repos in /etc/apt/sources.list (delete the # at the start of the lines).

---

### Post by dreamsINdigital on 2006-04-07
[QUOTE=souteneur3190]done that, and i have no idea how to access it[/QUOTE]Assuming you're using GNOME, System > Preferences > Theme > Theme Details > Icons

---

### Post by souteneur3190 on 2006-04-07
ive jus read on that u need about 4 more applications to install this icon theme.   Im not gonna kill my slef for some damn icons, thanks anyway.

---

### Post by shame on 2006-04-07
<Deleted>

---

