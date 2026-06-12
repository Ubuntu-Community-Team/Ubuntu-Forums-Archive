---
title: "ubunto wont boot!"
date: 2011-06-01
forum: General Help
---

### Post by jmg1013 on 2011-06-01
hey, please read the whole thing, ill try to keep it short, i really need some help.

long version:
yesterday i decided that i wanted to have debian along with ubuntu, ive had ubuntu for a while now
i downloaded the iso for debian and i was doing a whole bunch of stuff to get my flash drivve able to boot it. after a while i did write the iso to the flash drive, but formatted it because i did something wrong and debian wouldnt boot, so i keep trying to do it and keep formatting my flash drive. after a while none of my applications would open ( they would say opening, but would close right away).
then i went to restart my netbook and once it came back up all it showed was the debian installer (which didnt work  since i didnt have the iso anymore)
so i kept trying to get ubuntu to show up it wouldnt, so i went on my my windows netbook and made the flash drive able to boot debian. so then i could use the debian installer. 
but now when the flash drive isnt plugged in i dont even get the debian installer i just get a black screen (with the blinking underscore thing just sitting there) and it wont do anything
and i dont want to install debian since i cant without deleting the whole hard drive since it doesnt have the same partitioning options ubuntu did when installing that.

any help would really be appreciated.

im running:
ubuntu 11.04
on a asus eee 1001p

currently stuck writing this on a windows 7, asus eee 1001p

short version:

ubuntu wont boot after trying to install debian, and i dont want to install debian because it would delete ubuntu. and it doesnt even acknowledge that ubuntu is there, it acts like i have no os

---

### Post by xdragonforce on 2011-06-01
It seems that you have dug yourself into a reeeaaallly deep hole.
My solution (the only one) would to be to download the ubuntu iso and burn it to a CD/USB . Then fire up your laptop and boot into a live session. (Try Ubuntu From CD) and access your personal files, back them up, and then (im sorry) install ubuntu again.

---

### Post by jmg1013 on 2011-06-01
im gonna try that and as long as i can get my personal files im fine, the main reason its bad is because i have some files i dont want to lose

edit: also, how do i get the files once i boot into a live session, will they already be there or is there some way i have to get them?

---

### Post by jmg1013 on 2011-06-01
really need some help, how do i get the files on my hard drive, its not listing them. i dont mind reinstalling ubuntu i just want to get some of my files!

---

### Post by xdragonforce on 2011-06-04
Try going into Places > _GB file system.
Else try sudo mount /dev/sda1.

---

