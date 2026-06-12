---
title: "after gimp 2.8 upgrade - can't open shotwell"
date: 2012-05-05
forum: General Help
---

### Post by geovino on 2012-05-05
After installing the new Gimp 2.8... now Shotwell will not open. What does Shotwell have to do with Gimp? Maybe I should start over and remove the new Gimp and reinstall older one?

here's what comes up:

davek@davek-lub:~$ shotwell

(shotwell:3265): GLib-GObject-CRITICAL **: Read-only property 'read-only-view' on class 'GeeAbstractList' has type 'GeeCollection' which is not equal to or more restrictive than the type 'GeeList' of the property on the interface 'GeeList'


(shotwell:3265): GLib-GObject-CRITICAL **: Read-only property 'read-only-view' on class 'GeeAbstractSet' has type 'GeeCollection' which is not equal to or more restrictive than the type 'GeeSet' of the property on the interface 'GeeSet'


(shotwell:3265): GLib-GObject-CRITICAL **: Read-only property 'read-only-view' on class 'GeeReadOnlySet' has type 'GeeCollection' which is not equal to or more restrictive than the type 'GeeSet' of the property on the interface 'GeeSet'


(shotwell:3265): GLib-GObject-CRITICAL **: Read-only property 'read-only-view' on class 'GeeReadOnlyList' has type 'GeeCollection' which is not equal to or more restrictive than the type 'GeeList' of the property on the interface 'GeeList'

shotwell: symbol lookup error: shotwell: undefined symbol: gtk_window_set_has_resize_grip
davek@davek-lub:~$ davek@davek-lub:~$ shotwell

running Lubuntu 11.10 64bit

---

### Post by geovino on 2012-05-05
Now I removed shotwell and gimp, removed the ppa for gimp 2.8 and then tried to reinstall them:


davek@davek-lub:~$ sudo apt-get install gimp shotwell
[sudo] password for davek: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gimp : Depends: libgimp2.0 (<= 2.6.11-z) but 2.8.0~rc1-8oneiric0~ppa is to be installed
E: Unable to correct problems, you have held broken packages.
davek@davek-lub:~$ 

is there a way to fix broken packages? now that the ppa is removed should it install gimp 2.6 again?

---

### Post by geovino on 2012-05-05
so I was able to reinstall gimp 2.6. but Shotwell will not open. How do I get shotwell to work again?

---

### Post by philinux on 2012-05-05
> Install GIMP 2.8 (stable) in Ubuntu

Important: The PPA below provides GIMP 2.8 final for Ubuntu 12.04 Precise Pangolin and RC1 for Ubuntu 11.10 Oneiric Ocelot (the final GIMP 2.8 for Ubuntu 11.10 will probably follow shortly) and while the packages in the PPA worked just fine in my tests under both Ubuntu 12.04 and 11.10, the PPA description says that there are some dependency issues, especially for Ubuntu 11.10, so use it at your own risk!

From [http://www.webupd8.org/2012/05/gimp-28-stable-finally-available-for.html](http://www.webupd8.org/2012/05/gimp-28-stable-finally-available-for.html)

All working fine in 12.04.

To fix yours try.

```
sudo apt-get update

sudo apt-get install -f
```

---

### Post by geovino on 2012-05-05
> **philinux said:**
> From [http://www.webupd8.org/2012/05/gimp-28-stable-finally-available-for.html](http://www.webupd8.org/2012/05/gimp-28-stable-finally-available-for.html)

All working fine in 12.04.

To fix yours try.

```
sudo apt-get update

sudo apt-get install -f
```

I was able to take out the gimp 2.8 repos and then reinstall gimp 2.6. then I was able to upgrade Shotwell to the new version and now it works again. I don't care to upgrade to Lubuntu 12.04. I only do clean installs. Upgrades to new versions of Ubuntu/Lubuntu always causes trouble.

---

