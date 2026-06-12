---
title: "Q about installing stuff from the terminal"
date: 2006-06-01
forum: General Help
---

### Post by syxbit on 2006-06-01
i asked about installing kde on ubuntu and was told
sudo aptitude install kde-desktop.

it works just fine, but how do people know the exact wording.
is there a list somewhere, or do they get it from synaptic etc..

i know you can do the same for lots of other stuff.
i assume:
sudo aptitude install abiword
sudo aptitude install totem

but i'm merely guessing.
is this supposed to be trial an error ?
thanks

---

### Post by Kevin on 2006-06-01
That is correct, although if you wanted kde I would suggest sudo aptitude install kubuntu-desktop.  Using aptitude is good for large packages like kubuntu-desktop that depend on many many packages, because when you want to uininstall it, it will remove the unneeded dependencies with it.

To find the name of the packages, you can use synaptic, or there is also [this page]("http://packages.ubuntu.com/dapper/")

---

### Post by ash211 on 2006-06-01
You can also use ```
apt-cache search <program>
``` to find programs

---

### Post by mattisking on 2006-06-01
Other distro's use different tools than apt. apt is fastest, but unlike yum or rug doesn't seem to offer a way to easily search for packages.

---

### Post by mcduck on 2006-06-01
there are many ways. I usually use the searh tool in Synaptic, but you can also do 'apt-cache search xxxxxx' to search for packages with 'xxxx' in their name/description, and 'apt-cache show packagename' to read information about packages.

Anyway, most of the time the package name is same as the program's name, but if your not sure 'apt-cache show packagename' is easy way to check if such a package exists.

You can also browse available packages here: [http://packages.ubuntu.com/]("http://packages.ubuntu.com/"), and I've seen somewhere Ubuntu Package Search for the search bar in Firefox..

---

### Post by rcarring on 2006-06-01
You can also use synaptic if you prefer. I haven't used aptitude yet. Myself, if I want a specific app I would type in 
```

sudo apt-get install nameof-app.

```

---

### Post by mattisking on 2006-06-01
[QUOTE=ash211]You can also use ```
apt-cache search <program>
``` to find programs[/QUOTE]
I stand corrected.

---

### Post by RAOF on 2006-06-01
aptitude also works to search.  In fact, I do (almost) **all** of my package management stuff with aptitude:
```
aptitude search *packagename*
aptitude show *packagename*

```
Aptitude does everything.  Except, perhaps, searching in the package descriptions - Synaptic does that.

---

