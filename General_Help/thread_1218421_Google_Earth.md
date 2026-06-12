---
title: "Google Earth?"
date: 2009-07-20
forum: General Help
---

### Post by Ratscallion on 2009-07-20
Just found out that Google Earth is available for Linux. I went ahead and downloaded the .bin file, and tried to do what I did with the Adobe Air installer.
I went like this:
cd Downloads
chmod -x GoogleEarthInstaller.bin
./GoogleEarthInstaller.bin
    "Permission Denied"
Ok, so I went
chmod -x GoogleEarthInstaller.bin
sudo ./GoogleEarthInstaller.bin
    "Command not found"

Urm, is this supposed to happen? How would I go about sorting this out? Thanks in advance.

---

### Post by tornadof3 on 2009-07-20
should that not be 

chmod +x and not -x, then sudo as normal?

---

### Post by chriskin on 2009-07-20
you might be interested in using ubuntu tweak to install it for you and avoid all this trouble :)

---

### Post by talava on 2009-07-20
It's named "googleearth" in the standard repositories in Ubuntu.

---

### Post by Ratscallion on 2009-07-21
> chmod +x...

Going to try that

> Ubuntu Tweak

Ubuntu Tweak sometimes messes up my Repos... Not very good...

> It's in the repos

Ok, will have a look when I install it again in the future, or if any of the above don't work.

Thanks for all your help!

---

### Post by scouser73 on 2009-07-21
Hi, I'd suggest you follow the instructions set out [[COLOR="Red"]**Here**[/COLOR]]("http://tombuntu.com/index.php/2007/11/28/how-to-install-google-earth-in-ubuntu") for installing Google Earth

---

### Post by hyperdude111 on 2009-07-21
Dont bother with chmod it is a pointless method of doing the same thing you can do with a GUI.

1. Right click the .bin
2. Go permissions then enable "execute file as program" (Or something like that)
3. Open a terminal and drag the googleearth.bin icon into the terminal.
4. Press enter and hey presto.

---

### Post by oldos2er on 2009-07-21
> **Ratscallion said:**
> Just found out that Google Earth is available for Linux. I went ahead and downloaded the .bin file, and tried to do what I did with the Adobe Air installer.
I went like this:
cd Downloads
chmod -x GoogleEarthInstaller.bin
./GoogleEarthInstaller.bin
    "Permission Denied"
Ok, so I went
chmod -x GoogleEarthInstaller.bin
sudo ./GoogleEarthInstaller.bin
    "Command not found"

Urm, is this supposed to happen? How would I go about sorting this out? Thanks in advance.

 I thought the file name was GoogleEarthLinux.bin ?

---

### Post by Ratscallion on 2009-07-21
> **hyperdude111 said:**
> Dont bother with chmod it is a pointless method of doing the same thing you can do with a GUI.

1. Right click the .bin
2. Go permissions then enable "execute file as program" (Or something like that)
3. Open a terminal and drag the googleearth.bin icon into the terminal.
4. Press enter and hey presto.
That just brings up the old Command Line Vs GUI argument. I just use whichever is quicker.

---

### Post by Ratscallion on 2009-07-21
> **oldos2er said:**
> I thought the file name was GoogleEarthLinux.bin ?
Might be... Though it was just an example. Would have used a quote tag if I was properly quoting.

---

### Post by philinux on 2009-07-21
> **Ratscallion said:**
> Just found out that Google Earth is available for Linux. I went ahead and downloaded the .bin file, and tried to do what I did with the Adobe Air installer.
I went like this:
cd Downloads
chmod -x GoogleEarthInstaller.bin
./GoogleEarthInstaller.bin
    "Permission Denied"
Ok, so I went
chmod -x GoogleEarthInstaller.bin
sudo ./GoogleEarthInstaller.bin
    "Command not found"

Urm, is this supposed to happen? How would I go about sorting this out? Thanks in advance.

Click the medibuntu link below if not done already. Follow instructions.
Then:-
```
sudo apt-get install googleearth

```

---

