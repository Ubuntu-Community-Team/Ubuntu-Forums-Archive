---
title: "wacom bamboo pen"
date: 2011-03-03
forum: General Help
---

### Post by slaz on 2011-03-03
Hi, 

I recently purchased a wacom bamboo pen and tablet. When I plugged it into my Ubuntu desktop 10.10, I was disappointed that it did not work. I have enabled the wacom kernel through the package manager, and rebooted the machine but still doesn't work.

What am I doing wrong,
thanks

---

### Post by iheartubuntu on 2011-03-03
Open up a terminal (apps > accessories > terminal) and copy and paste each line in and press enter after each one...

```
sudo add-apt-repository ppa:doctormo/wacom-plus
sudo apt-get update
sudo apt-get install wacom-dkms
```

It works in 10.04 so it should work in Maverick too.

From:
[http://frankgroeneveld.nl/2010/04/11/get-wacom-bamboo-fun-pen-working-in-ubuntu-lucid/](http://frankgroeneveld.nl/2010/04/11/get-wacom-bamboo-fun-pen-working-in-ubuntu-lucid/)

---

