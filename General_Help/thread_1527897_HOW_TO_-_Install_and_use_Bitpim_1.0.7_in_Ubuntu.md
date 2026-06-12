---
title: "HOW TO - Install and use Bitpim 1.0.7 in Ubuntu"
date: 2010-07-09
forum: General Help
---

### Post by drewsus on 2010-07-09
While this won't be completely comprehensive (as in, I will not detail your specific phone, and this assumes you have a cable link, not bluetooth - although, I have done that before, and will maybe add that in later when I have some time).

1) Install alien so you can convert the .rpm file to .deb:

```
sudo apt-get install alien
```

2) Get Bitpim:

[http://www.bitpim.org/#download](http://www.bitpim.org/#download) 
(get the linux RPM)

3) Convert rpm to deb:

Open terminal and go to the folder where you just downloaded bitpim*.rpm and issue this command: 

```
sudo alien bitpim*.rpm
```

Install the created .deb file

4) Tie up the lose ends:
```
cd /usr/lib/
sudo ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3

cd /lib/
sudo ln -s /lib/libexpat.so.1 /usr/lib/libexpat.so.0
```

5a) Connect your phone via USB. 
If you phone says something like "**Connect phone to PC using USB Cable**" either do nothing or select "**No**"

5b) Connect your phone via BlueTooth. 
***<under construction>***

6) Run bitpim:

```
sudo bitpim
```
([SIZE="1"]*I ran into exceptions when not running as root*[/SIZE])

You may notice that the menu bar is missing. I dont know why as it shows up in Windows for me using 1.0.7. Just remember that ALT+<Some Letter> accesses those (ie. ALT+V accesses the View menu so you can select "View Filesystem" and once you have that drop down menu accessed you can press left and right to get to the other once if you cant figure out what letter to use).
Also, make sure to select the correct phone! 
I am not responsible for any damage this does to your phone, but I have used this one 3 different phones without problems. 

Thats it for now, I hope that helps someone!

Drewsus

---

### Post by drewsus on 2010-07-09
*[SIZE="1"]<reserved>[/SIZE]*

---

### Post by ashv3524 on 2011-04-17
The alien method doesn't work for those using 64-bit ubuntu. Fortunately, bitpim 1.0.7 is available in the debian repositories and can be installed from Debian 'Sid' (Unstable).

---

### Post by drewsus on 2011-04-17
Great to hear! This little how to was made before they even had a deb file on their homepage and 1.0.6 was in the repos

---

### Post by huangweiqiu on 2011-04-17
This is the tutorial what i am looking for ,it works. thanks

---

