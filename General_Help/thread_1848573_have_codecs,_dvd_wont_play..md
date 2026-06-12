---
title: "have codecs, dvd wont play."
date: 2011-09-22
forum: General Help
---

### Post by NERDMAN! on 2011-09-22
bad enough my network is dead but now ubuntu wont play a dvd for me?

ok so i'm running ubuntu 10.04 LTS on a dell inspiron 1525 laptop, i have every decoder codec pack i can find in the software center installed.
i have both mplayer and dragonplayer.

and it spits an error "cannot read from resource".
its a region 4 dvd, region 4 drive.
knowing my luck its probably something painfully obvious and i just cant see it but if anyone out there knows a trick or 2 that might get this laptop to actually behave itself i would greatly appreciate it.

oh and i'm tryin to watch "the girl who leapt through time" if it helps at all.

---

### Post by MG&amp;TL on 2011-09-22
What application are you trying to watch it with?

---

### Post by NERDMAN! on 2011-09-22
movie player and / or dragonplayer as indicated in first post.

---

### Post by hansdown on 2011-09-22
Hi NERDMAN!

You also need to install

```
ubuntu-restricted-extras
```

and 

```
libdvdcss2
```

---

### Post by NERDMAN! on 2011-09-22
installed the restricted extras an hour ago. sadly it did nothing.

---

### Post by hansdown on 2011-09-22
Did you also install

```
libdvdcss2
```

---

### Post by NERDMAN! on 2011-09-22
> **hansdown said:**
> Did you also install

```
libdvdcss2
```

pacgage wasnt found in software sources.

---

### Post by Primefalcon on 2011-09-22
here's what you need: [http://medibuntu.org/repository.php](http://medibuntu.org/repository.php)

step one (this installs the software into the repository)
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

step 2 (so you can find it in the software center)
```
sudo apt-get install app-install-data-medibuntu apport-hooks-medibuntu

```

step 3 (actually installs the codecs)
if 32 bit
```
sudo apt-get install w32codecs libdvdcss2
```

if 64bit
```
suo apt-get install w64codecs libdvdcss2
```

**OR** if you want to do it all in one go
32bit
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update; sudo apt-get install app-install-data-medibuntu apport-hooks-medibuntu; sudo apt-get install w32codecs libdvdcss2
```
64bit
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update; sudo apt-get install app-install-data-medibuntu apport-hooks-medibuntu; sudo apt-get install w64codecs libdvdcss2
```

---

### Post by hansdown on 2011-09-22
Thanks Primefalcon.

I haven't needed to do a fresh install in a long time.

I forget these things.

---

### Post by NERDMAN! on 2011-10-06
WOOO!
thanks!

i'm sure theres a perfectly reasonable explanation for it but it escapes my sense of logic as to why ubuntu doesnt come with (or have available by default) the packages required for basic dvd playback.
it just seems stupid to me.

---

### Post by 3rdalbum on 2011-10-06
> **NERDMAN! said:**
> WOOO!
thanks!

i'm sure theres a perfectly reasonable explanation for it but it escapes my sense of logic as to why ubuntu doesnt come with (or have available by default) the packages required for basic dvd playback.
it just seems stupid to me.

Commercial DVDs are encrypted. It's trivial to break the encryption, which is what libdvdcss2 does; but in some parts of the world it's a little bit illegal.

Legal DVD playback uses a licensed playback decryption key, which costs money.

That's why Ubuntu doesn't come with commercial DVD playback out-of-the-box. They'd either need to pass on the license key charge to all its users, or risk getting sued.

---

