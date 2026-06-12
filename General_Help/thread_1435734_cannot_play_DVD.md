---
title: "cannot play DVD"
date: 2010-03-21
forum: General Help
---

### Post by jesseejames on 2010-03-21
I am totally new to ubuntu I just installed for the first time and am amazingly impressed so far.  I am trying to play a dvd that my friend sent me with a television program recorded on it and I am told that movie player does not have the URI to play it.  Please help me as I have no clue as to what it means.

---

### Post by darolu on 2010-03-21
It is weird the movie player (I suppose Totem) ask for a URI; anyways if it is a regular (commercial) DVD you'll need to install the library needed to decrypt it (libcss), if this is the case open a terminal (under Applications - Accessories) and run this commands:
```
$ sudo apt-get install ubuntu-restricted-extras
```
You can also find this package in Synaptic (System - Administration - Synaptic) but the css library needs to be installed via Command Line (terminal).
After restricted-extras is installed run:
```
$ sudo /usr/share/doc/libdvdread4/install-css.sh
```
More information at: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Try to play the DVD after installing this two packages, if you can't play them still run Totem from a terminal to see if it prints the exact error:
```
$ totem
```

---

### Post by jesseejames on 2010-03-21
Ok now i get
cannot find package ubuntu-restricted-extras
It is Totem that gives the error 
No URI handler implemented for dvd
 
This is a dvd from a friend who puts the television program on dvd for me.  I will have to ask him what format he is using.  They have always played fine with sonic cine player in windows XP.  I am so happy to have found an alternative to Microsoft's mess.  I just wonder how it took me this long to find ubuntu

---

### Post by Megafag on 2010-03-21
> **jesseejames said:**
> I am totally new to ubuntu I just installed for the first time and am amazingly impressed so far.  I am trying to play a dvd that my friend sent me with a television program recorded on it and I am told that movie player does not have the URI to play it.  Please help me as I have no clue as to what it means.

VLC opens everything

```
sudo apt-get install vlc
```

---

### Post by jesseejames on 2010-03-21
OK Thanks

---

### Post by 2hot6ft2 on 2010-03-21
The short way
Open a terminal
Applications > Accessories > Terminal
and copy and paste these into it one at a time
The first one enables the medibuntu repository and gets the key for it, the second one installs what you need.

```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```
type in your password when prompted and hit Enter it wont be displayed.
```
sudo apt-get install ubuntu-restricted-extras libdvdcss2
```
You'll have to agree to the java agreement to install java using the Tab button or arrow keys.

---

### Post by jesseejames on 2010-03-21
Ok Thank You I will have to try these fixes later as I must get to work now.  Thought I might get it done in time that I had but just ran out.  Thanks Again

---

### Post by darolu on 2010-03-22
Why adding a whole new repository (medibuntu's) when restricted-extras and libcss are in regular Ubuntu ones? It is in Multiverse.
Click link for reference: [http://packages.ubuntu.com/karmic/ubuntu-restricted-extras](http://packages.ubuntu.com/karmic/ubuntu-restricted-extras)
You can download it and double click it to install it too, but I'm not 100% sure it will download all the packages on its own.

If you didn't find it, means that you don't have Multiverse enabled, enabling it is very simple, don't worry, follow this steps:

1) Open Software Centre at Applications - Software Center
2) Click on Edit - Software Sources
3) Check all 4 boxes (main, universe, restricted and multiverse) and click close.

It will update the software list, to make sure you can see them all click on View - All applications.

After this, you can search (use the quick search box on to-right corner if you like) for "ubuntu-restricted-extras", and install it.

Then you can install the "css" library in your terminal with the command I gave you earlier.

This package (restricted-extras) will add support to play most popular restricted formats like mp3, aac, wma, mov, wmv, etc.

I said it is weird Totem (movie player) gives you a "URI" error since URI is used to identify resources on the Internet.

Using VLC is a good idea, it is a very good player; you can find it in the Software Centre as well.

---

### Post by soltanis on 2010-03-22
URI's can refer to anything (hence "Universal resource identifier"), not just the Internet. In particular both Totem and VLC (and other players like mplayer) can accept URI strings such as dvd:// to denote appropriate media sources.

Install VLC though (and remove totem) because VLC >> totem. Totem...just never works for me *sigh*.

---

