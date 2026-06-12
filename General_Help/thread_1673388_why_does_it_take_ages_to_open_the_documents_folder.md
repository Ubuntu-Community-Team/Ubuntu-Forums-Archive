---
title: "why does it take ages to open the documents folder?"
date: 2011-01-22
forum: General Help
---

### Post by rvchari on 2011-01-22
off late i noticed that it takes ages to open the documents folder. the folder grew in size gradually and it neared around 20mb of space. i thot the size of the folder is not letting it open faster and display the contents (funny, isnt it) i reduced the size by organising contents in folders and relocating them.
now the size is around 8 mb and it still takes lots of time to open the folder and display contents...
at times i get a grey window (frozen mode) for a few seconds (minute at times) before it is displayed...
any clue y this funny behaviour ?

---

### Post by LinUxaliVe on 2011-01-22
Try opening your file manager from the command line. Navigate to the folder from there.

IE - Open a terminal (in x), type in the name of your file manager (thunar, pcmanfm, etc...), navigate to the folder in that FM, check the terminal used to launch the FM for any messages.

---

### Post by hakermania on 2011-01-22
If you are talking about nautilus do the following:
Open a terminal and give
```
nautilus ~/Documents/
```
output any error(s)

Btw my Documents folder is up to 1 GB and contains more than 1000 items, but it does just 2 secs to open, and I haven't got a super-pc

---

### Post by akand074 on 2011-01-22
> **hakermania said:**
> If you are talking about nautilus do the following:
Open a terminal and give
```
nautilus ~/Documents/
```output any error(s)

Btw my Documents folder is up to 1 GB and contains more than 1000 items, but it does just 2 secs to open, and I haven't got a super-pc

Mine is 700GB and opens in -2 seconds (that's right it opens in the past). No but it takes a fraction of a second. Shouldn't have anything to do with it, unless your hard drive is dying but it's most likely software issue, yeah post any errors.

---

### Post by rvchari on 2011-01-22
i did all....
still the same. i use nautilus.
i also installed kde4 in ubuntu and tried it from there. still same. on the contrary dolphin hanged !!!

wonder if there is a way to speed up. sometimes it takes more time to open the documents folder to make it display contents than booting into ubuntu !!!
problem is only with documents folder....
it contains zip files, xmls docs excel files all...

---

### Post by rvchari on 2011-01-23
after a whole day of figuring out the funny problem, and ofcourse an oppurtunity to download and experience xfce4 window manager (i tried in kde as well) i could identify the culprit.

first, xfce4 opened the documents folder with a breeze... then i figured nautilus must be the culprit.. but it was not !!! then i shortlisted 2 MS document files that when re-located folder opened instantly.
same file was opened by xfce without any prob and nautilus as well as dolphin froze !!!
the 2 files were scanned and were safe, plain doc files...
have to think about it !!!

one added knowledge i got was the experience of xfce which is light weight and much faster !!!

i ll mark the thread as solved... (will look to solve the unsolved part thru a different thread !)

---

### Post by tredegar on 2011-01-23
My guess is that you have nautilus set to display thumbnails, and insufficient thumbnail cache.
Try setting this option in Edit... Preferences..  Preview  to "Never"
Restart nautilus and see if it is faster.

---

### Post by rvchari on 2011-01-23
it speeded up and yes, you were right, cache size was restricted to 10 mb (is that the default).
not i edited to NEVER...
it should solve the problem..

---

