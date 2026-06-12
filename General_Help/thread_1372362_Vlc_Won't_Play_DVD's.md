---
title: "Vlc Won't Play DVD's"
date: 2010-01-04
forum: General Help
---

### Post by Final Version on 2010-01-04
I'm trying to play a dvd (StarGate) from the dvd drive, but when I open it with vlc it just sits there, the dvd doesn't even pop-up. Help is appreciated.

---

### Post by HappyFeet on 2010-01-04
Copy and paste the following into a terminal:
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```
then:
```
sudo apt-get install libdvdcss2
```
enjoy your movie.

---

### Post by jamesisin on 2010-01-04
If you have not done so, you may want to go over this comprehensive media how to:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by Final Version on 2010-01-04
> **HappyFeet said:**
> Copy and paste the following into a terminal:
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```then:
```
sudo apt-get install libdvdcss2
```enjoy your movie.
Thanks.

---

