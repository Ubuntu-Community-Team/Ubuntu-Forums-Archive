---
title: "repository list"
date: 2011-08-12
forum: General Help
---

### Post by spiritech on 2011-08-12
hi 

i have the following repositories in my Other Software list.

Canonical
Independent

could someone tell me if there should be any others, like multiverse or universe.

---

### Post by raja.genupula on 2011-08-12
man all those are 3rd party software links . install any thing like google chrome or opera . that ppa will be add there . 
i mean if any new ppa added to your repo's list then it will be at other software

---

### Post by gordintoronto on 2011-08-12
Universe and Multiverse are under the "Ubuntu Software" tab.

---

### Post by Bluesan on 2011-08-12
To be sure that you have them all, edit your sources list. At the terminal:

```
sudo gedit /etc/apt/sources.list
```Uncomment the repositories that have a # in front of them, and save your changes. Then:

```
sudo apt-get update
```

Also, you might want to add the Medibuntu repository:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by spiritech on 2011-08-25
hi,

thanks for the replies.

---

### Post by spiritech on 2011-08-25
> **Bluesan said:**
> To be sure that you have them all, edit your sources list. At the terminal:

```
sudo gedit /etc/apt/sources.list
```Uncomment the repositories that have a # in front of them, and save your changes. Then:

```
sudo apt-get update
```Also, you might want to add the Medibuntu repository

i checked the list and they are all there accept the backports, but i dont use those anyway so
alls good.

thankyou

---

### Post by Bluesan on 2011-08-26
^,

You're welcome.

:)

---

