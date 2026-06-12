---
title: "Linux Mint 8 64-bit and getlibs"
date: 2010-01-07
forum: General Help
---

### Post by siblog on 2010-01-07
I have been trying to get Adobe Air installed on my Linux Mint 8 64-bit desktop for a few days now. The issue that I am finding is that though I can install getlibs, I can't find any of the packages or libraries. 

```
$ sudo getlibs -l libnss3.so.1d
No match for libnss3.so.1d
No packages to install

```

My guess is that Linux Mint does not have all the necessary Ubuntu repositories. Does anyone know what repository I need to add to access getlibs packages and libraries?

---

### Post by ajgreeny on 2010-01-07
libnss3-1d is in ubuntu's main repo, so should be in your repos as well.

You should not search for libnss3.so.1d, however, but just libnss3-1d will find it.  Install it if needed and it will give you the .so file.

---

### Post by siblog on 2010-01-07
Ok I actually figured it out (or should I say got some help elsewhere). What I needed to do was provide somewhat of a full path since Mint does not have it in their repositories. Here is what I needed to provide:

```
sudo getlibs --distro Ubuntu --release karmic -l libnss3.so.1d
```

So now Adobe Air is running correctly and Tweetdeck is running great too

---

### Post by lannatwin on 2010-05-15
Can you please exp[lain how you got Tweetdeck to install?  I have installed Adobe Air, but Tweetdeck install link on their website is not working for me.  Thanks.

---

### Post by siblog on 2010-05-17
Here is a great step-by-step tutorial to get Air installed on Ubuntu 64-bit

[http://www.omgubuntu.co.uk/2010/01/how-to-install-adobe-air-ubuntu-64bit.html](http://www.omgubuntu.co.uk/2010/01/how-to-install-adobe-air-ubuntu-64bit.html)

Once you have Air running, installing Tweetdeck should be straight forward. If you are trying to install Air on 64-bit Mint you need to provide the full path to the Ubuntu repositories like I showed above. let me know if you have any issues or questions

---

