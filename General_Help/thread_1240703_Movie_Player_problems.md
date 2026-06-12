---
title: "Movie Player problems"
date: 2009-08-15
forum: General Help
---

### Post by DoubleCross on 2009-08-15
I cant seem to get my Movie Player to work. I insert the DVD but I get he error message that the player is not able to read from the resource. Any suggestions?

---

### Post by fluffman86 on 2009-08-15
DVDs are protected by copy-protection software and as such it is illegal to view them without a license in some countries.  

That being said, you should be able to play them if you open go to Applications > Accessories > Terminal and type:
```

sudo apt-get install libdvdread4 ubuntu-restricted-extras mplayer

```
Then type:
```
 
sudo /usr/share/doc/libdvdread4/install-css.sh

```

More information can be found at [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by Mardoct909 on 2009-08-15
To get all the common codecs, including DVD support, just run this bit of code:

> sudo su

<put in your password>

echo "deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free"  >> /etc/apt/sources.list && apt-get update && apt-get install medibuntu-keyring && apt-get update && apt-get install non-free-codecs

---

### Post by DoubleCross on 2009-08-15
Flawless. Thank you.

---

### Post by East82 on 2009-08-15
Here is a great article on accessing restricted codecs and drivers
[http://www.linuxidentity.com/us/down/articles/Ubuntu_810_codecs_US.pdf](http://www.linuxidentity.com/us/down/articles/Ubuntu_810_codecs_US.pdf)

---

### Post by andrew.46 on 2009-08-15
Hi Mardoct,

> **Mardoct909 said:**
> To get all the common codecs, including DVD support, just run this bit of code:

```
sudo **[COLOR="Red"]su[/COLOR]** [...]
```



On a standard Ubuntu system the command would normally only use sudo...

Andrew

---

### Post by P4man on 2009-08-15
> **fluffman86 said:**
> DVDs are protected by copy-protection software and as such it is illegal to view them without a license in some countries.  

Not that Im gonna care too much, but out of curiosity, does anyone know what countries this applies to (and in which it is legal) ?

---

