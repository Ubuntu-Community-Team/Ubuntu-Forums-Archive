---
title: "How to install .deb packages"
date: 2011-09-10
forum: General Help
---

### Post by riff76 on 2011-09-10
Hi! to everyone.. I do have an ovpn packages(.deb) in a folder and I just wanted to know how to install it all simultaneously. I'm just starting using ubuntu.. TIA

---

### Post by haqking on 2011-09-10
> **riff76 said:**
> Hi! to everyone.. I do have an ovpn packages(.deb) in a folder and I just wanted to know how to install it all simultaneously. I'm just starting using ubuntu.. TIA


from terminal:

sudo dpkg -i **package**.deb

in the location where the .deb is and replacing **package** with the name

---

### Post by riff76 on 2011-09-10
Many thanks for the the quick reply.... thanks haqking!

---

### Post by sisco311 on 2011-09-10
Hi and welcome to the forums!

dpkg -i should do the trick, however its a *low-level* tool. I'd use gdebi for this. It resolves the dependencies as well.
```
sudo gdebi package.deb
```

Or if you are using the GUI, then you can simply double click the .deb file. ;)

---

### Post by haqking on 2011-09-10
> **sisco311 said:**
> Hi and welcome to the forums!

dpkg -i should do the trick, however its a *low-level* tool. I'd use gdebi for this. It resolves the dependencies as well.
```
sudo gdebi package.deb
```Or if you are using the GUI, then you can simply double click the .deb file. ;)

+1

yeah good point ;-)

this also

---

### Post by el_koraco on 2011-09-10
Or go to the folder you downloaded the packages and issue 

```
sudo dpkg -i *.deb
```

---

### Post by Frogs Hair on 2011-09-10
I use Gdebi , but the software center can also be used . The option to open with the software center has been displayed with some of .deb packages I have installed .

---

### Post by IWantFroyo on 2011-09-10
> **el_koraco said:**
> Or go to the folder you downloaded the packages and issue 

```
sudo dpkg -i *.deb
```

This is the best method to install many .debs simultaneously. Just make sure you move any you don't want to install out of the folder.

---

### Post by CharlesA on 2011-09-10
Is Gdebi GUI or CLI?

I just use dpkg to install debs.

---

### Post by haqking on 2011-09-10
> **CharlesA said:**
> Is Gdebi GUI or CLI?

I just use dpkg to install debs.

the G stands for Gnome doesnt it so i always assume graphical. though it has a CLI interface also

[https://help.ubuntu.com/community/InstallingSoftware#Using_GDebi_to_install_packages](https://help.ubuntu.com/community/InstallingSoftware#Using_GDebi_to_install_packages)

---

### Post by sisco311 on 2011-09-10
> **CharlesA said:**
> Is Gdebi GUI or CLI?

I just use dpkg to install debs.

It's CLI, gdebi-gtk is the GUI. ;)

---

### Post by CharlesA on 2011-09-10
> **sisco311 said:**
> It's CLI, gdebi-gtk is the GUI. ;)
Oh cool. Thanks! I might have to start using it instead of regular dpkg if I am unsure of dependencies.

---

### Post by haqking on 2011-09-10
> **sisco311 said:**
> It's CLI, gdebi-gtk is the GUI. ;)


ahh yes i see.  I always assumed the G would mean graphical anyways.

~$ gdebi
Usage: gdebi [options] filename
For a graphical version run gdebi-gtk


cheers, good to know

The [community docs]("https://help.ubuntu.com/community/InstallingSoftware#Using_GDebi_to_install_packages") describe it misleadingly

---

### Post by sisco311 on 2011-09-10
> **haqking said:**
> 
The [community docs]("https://help.ubuntu.com/community/InstallingSoftware#Using_GDebi_to_install_packages") describe it misleadingly

Not anymore. ;)

---

### Post by haqking on 2011-09-10
> **sisco311 said:**
> Not anymore. ;)


ahhh sweet. 

I just realised i could of done that, i wasnt aware that the community docs were editable like the wiki.

Good to know

I guess the community docs are moving over to the wiki.ubuntu as time moves on.

---

### Post by oldos2er on 2011-09-10
> **CharlesA said:**
> Oh cool. Thanks! I might have to start using it instead of regular dpkg if I am unsure of dependencies.

There's also gdebi-kde for KDE users.

---

