---
title: "Can't get rid of PPA"
date: 2012-05-08
forum: General Help
---

### Post by xjonquilx on 2012-05-08
I added the mozillateam/thunderbird-stable PPA to Ubuntu and it keeps erroring out so I decided to purge it. However, when I try to purge the PPA using ppa-purge it tells me it can't find that repository. 

Is there any other way to purge the repository?

---

### Post by oklokl on 2012-05-08
If the same
 Hidden in some cases
register you do not view
Normally
Automatic registration is complete.

Do not need to worry about
```


## backup
mkdir -p ~/backup/sources
mkdir -p ~/backup/sourcesD
sudo cp -rf /etc/apt/sources.list ~/backup/sources
sudo cp -rf /etc/apt/sources.list.d ~/backup/sourcesD

## sources.list.d remove
sudo rm -rf /etc/apt/sources.list.d/*

# edit

gksudo gedit /etc/apt/sources.list

#Change save

sudo apt-get update


#ex> key error..
#ex>
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys [COLOR=Red]A200C40D[/COLOR]
sudo apt-get update


#ex> ppa Google search
sudo add-apt-repository ppa:freefilesync/ffs    ##  freefilesync    https://launchpad.net/~freefilesync/+archive/ffs
sudo apt-get update

```

---

### Post by wilee-nilee on 2012-05-08
> **oklokl said:**
> If the same
 Hidden in some cases
register you do not view
Normally
Automatic registration is complete.

Do not need to worry about
```

gksudo gedit /etc/apt/sources.list
```

That ppa is in

```
/etc/apt/sources.list.d
```

probably

---

### Post by plant on 2012-05-08
The easiest way is to go to Update Manager->Settings. From there you can uncheck or remove ppa's,(better to uncheck than remove).

---

### Post by oklokl on 2012-05-08
Before that, using the following ...  I was a mistake.
Thank Good, modify

---

### Post by wilee-nilee on 2012-05-08
Actually /etc/apt/sources.list.d is a file that wont do it either.

OP with thunder bird I think your safe to just open nautilus in root with.

```
gksudo nautilus
```Then go to file in the left panel and follow this path.

```
/etc/apt/sources.list.d
```and just delete it, then run a update.

As suggested as well it is in software sources probably and can be unticked or deleted from there.

It could be in the original /apt/etc/sources.list if you put it there, but it seems if you're running a ppa purge you probably used this to install.

```
sudo add-apt-repository ppa:"ppa address"
```This can be confusing, that is for sure. :)

---

### Post by Baldrick_NZ on 2012-05-08
> **wilee-nilee said:**
> Actually /etc/apt/sources.list.d is a file that wont do it either.

OP with thunder bird I think your safe to just open nautilus in root with.

```
gksudo nautilus
```Then go to file in the left panel and follow this path.

```
/etc/apt/sources.list.d
```and just delete it, then run a update.

As suggested as well it is in software sources probably and can be unticked or deleted from there.

It could be in the original /apt/etc/sources.list if you put it there, but it seems if you're running a ppa purge you probably used this to install.

```
sudo add-apt-repository ppa:"ppa address"
```This can be confusing, that is for sure. :)

+1. I was just going to say that, but you beat me to it! ;-)

---

### Post by oklokl on 2012-05-08
[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

```
sudo apt-get update --fix-missing
sudo apt-get -f 
```

---

### Post by xjonquilx on 2012-05-08
Thanks so much for the response! I was a little confused and thought the GUI for sources had been removed. I went in to Update Manager and got rid of the PPA there. :)

---

### Post by oklokl on 2012-05-08
Congratulations ...

Terminal
 It is recommended ..
ctrl alt T 

n,.n
Nautilus, occasionally an error.

---

