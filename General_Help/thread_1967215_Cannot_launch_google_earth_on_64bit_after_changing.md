---
title: "Cannot launch google earth on 64bit after changing appearance"
date: 2012-04-27
forum: General Help
---

### Post by vienswuer on 2012-04-27
I installed Google Earth (from its website) on Xubuntu 12.04 LTS 64 bits. It had worked properly until I tweaked that creepy fonts and window styles. Now, it won't launch anymore (not even from a terminal). I followed these steps: [http://www.omgubuntu.co.uk/2012/01/how-to-make-google-earth-look-native-in-ubuntu/](http://www.omgubuntu.co.uk/2012/01/how-to-make-google-earth-look-native-in-ubuntu/)
The terminal returns this message: $ google-earth
./googleearth-bin: symbol lookup error: ./libmoduleframework.so: undefined symbol: _Z34QBasicAtomicInt_fetchAndAddOrderedPVii
Any idea, missing packages perhaps? Thanks in advance.
\\:D/XUBUNTU

---

### Post by Primefalcon on 2012-04-27
If I remember right it has something to do with crypto and 64bit objects....

what you'll need to is delete or rename I'd recomend renaming it libcrypto<versionnumber>.so in your google earth install directory, which from aquick lookup is typically /opt/google-earth but if its not there just do a simple

```
find / -type d -iname 'google-earth'
```

if it is there just do somethging like ```
sudo mv /opt/google-earth/is/libcrypto.so /opt/google-earth/is/libcrypto<versionnumber>.so~moved
```

---

### Post by vienswuer on 2012-04-28
There is no such file in GEarth's directory. Any other suggestion?

---

### Post by xyzzyman on 2012-04-28
sudo apt-get purge google-earth-stable

then start over from the beginning.

---

### Post by vienswuer on 2012-04-28
Didn't work at all. :(

---

### Post by jerryrice on 2012-09-14
I have the exact same problem with 12.04 , followed the same path to fix the fonts and get 

undefined symbol: _Z34QBasicAtomicInt_fetchAndAddOrderedPVii

 Have purged Google earth, reloaded , same funky non usable fonts, follow the same instructions using the "replacement" files, same result.

---

