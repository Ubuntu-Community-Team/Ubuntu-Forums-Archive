---
title: "Strange locale problem..."
date: 2011-03-12
forum: General Help
---

### Post by icaro829 on 2011-03-12
Hi all!

this is my first message, and sorry for my bad english :)

I have a problem with a Maverick installed on a Macbook 3.1, with italian keyboard.
I've installed maverick months ago with english language settings and, obviously, italian keyboard.
This morning, with an apt-get update i've seen some problems with my locale setting, and if i do
$locale
the result is

```
LANG=it_IT.utf8
LANGUAGE=en_US:en
LC_CTYPE="en_US.utf8"
LC_NUMERIC="en_US.utf8"
LC_TIME="en_US.utf8"
LC_COLLATE="en_US.utf8"
LC_MONETARY="en_US.utf8"
LC_MESSAGES="en_US.utf8"
LC_PAPER="en_US.utf8"
LC_NAME="en_US.utf8"
LC_ADDRESS="en_US.utf8"
LC_TELEPHONE="en_US.utf8"
LC_MEASUREMENT="en_US.utf8"
LC_IDENTIFICATION="en_US.utf8"
LC_ALL=en_US.utf8

```but if i look at /etc/default/locale i see

```
LANG="en_US.UTF-8"
```How can i modify this LANG settings? I want a system entirely in english language, some errors regarding strange options are really not so cute :)
Thank you all :)

---

### Post by Krytarik on 2011-03-12
Please see this earlier thread:
[http://ubuntuforums.org/showthread.php?p=10233941](http://ubuntuforums.org/showthread.php?p=10233941)

---

### Post by icaro829 on 2011-03-12
> **Krytarik said:**
> Please see this earlier thread:
[http://ubuntuforums.org/showthread.php?p=10233941](http://ubuntuforums.org/showthread.php?p=10233941)

Thank you! but i solved with 
$ sudo apt-get remove locales
then
$ sudo apt-get install locales
:)

---

