---
title: "Google Earth - It's installed. But, uh?"
date: 2009-11-03
forum: General Help
---

### Post by Roasted on 2009-11-03
I just installed Google Earth from Synaptic.

Yet, I see it no where.

I tried to create a launcher, but I don't know the command.

google earth
googleearth
google-earth

all didn't work.

Where's my menu icon?

---

### Post by RedSingularity on 2009-11-03
The command is "googleearth".  What happens if you try it in a terminal?

---

### Post by Old *ix Geek on 2009-11-03
> **Roasted said:**
> I just installed Google Earth from Synaptic.

Yet, I see it no where.

I tried to create a launcher, but I don't know the command.There's nothing mysterious about finding the command name when you install something via Synaptic--just look under the **Installed Files** tab [in Synaptic] for the program you installed.

---

### Post by Roasted on 2009-11-03
jason@Area51:~$ googleearth
bash: googleearth: command not found
jason@Area51:~$

---

### Post by liquidbee on 2009-11-03
> **Roasted said:**
> jason@Area51:~$ googleearth
bash: googleearth: command not found
jason@Area51:~$

```
dpkg -l | grep google
```

What's the output ?

---

### Post by faial on 2009-11-03
> **Old *ix Geek said:**
> There's nothing mysterious about finding the command name when you install something via Synaptic--just look under the **Installed Files** tab [in Synaptic] for the program you installed.
I'm an Ubuntu (Linux) complete neophyte; I've been using Ubuntu 9.04 JJ for 12 days now after over 20 years of Windows (yes! I finally said goodbye to Mr. Gates & Co!).

Sooo, I see in Synaptic that the googleearth-package 0.5.4.1~Oubuntu1 is installed. Now what? How do I get Google Earth to work?

---

### Post by philinux on 2009-11-03
> **Roasted said:**
> jason@Area51:~$ googleearth
bash: googleearth: command not found
jason@Area51:~$

Using the terminal do this.

```
apt-cache policy googleearth
```

Post back the output.

---

### Post by P4man on 2009-11-03
> **faial said:**
> I'm an Ubuntu (Linux) complete neophyte; I've been using Ubuntu 9.04 JJ for 12 days now after over 20 years of Windows (yes! I finally said goodbye to Mr. Gates & Co!).

Sooo, I see in Synaptic that the googleearth-package 0.5.4.1~Oubuntu1 is installed. Now what? How do I get Google Earth to work?

You did not install google earth. you installed a package to BUILD a debian package for google earth. Not the program itself. 

Looks like google earth is not in the repositories, 

**edit:**

follow this:
[https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)

---

### Post by scouser73 on 2009-11-03
> **Old *ix Geek said:**
> There's nothing mysterious about finding the command name when you install something via Synaptic--just look under the **Installed Files** tab [in Synaptic] for the program you installed.

Alternatively, you can add the Google repositories.

> [B]deb [http://packages.medibuntu.org/jaunty](http://packages.medibuntu.org/jaunty) free non-free
#deb-src deb [http://packages.medibuntu.org/jaunty](http://packages.medibuntu.org/jaunty) free non-free[/B]

---

### Post by szaboz on 2009-11-03
hi;




~/google-earth/googleearth

in console should do.

(make sure yo are not root)

---

### Post by philinux on 2009-11-03
Anyone reading this. To get googleearth click the medibuntu link in my signature below and follow the full instructions.

Then the googleearth package will be in synaptic.

Either use synaptic to install or

sudo apt-get install googleearth

or in firefox address bar type

apt:googleearth

The menu item appears udner Apps>Internet

---

