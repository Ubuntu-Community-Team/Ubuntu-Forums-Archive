---
title: "UBUNTU and WINDOWS 7"
date: 2011-02-24
forum: General Help
---

### Post by gabrel on 2011-02-24
Hello guys,

1.  after installing ubuntu 10.10 I had to install win7.i made 2 other partitions (1 for win os 2nd for other data).

2.  after installing win7 ive noticed there was NO boot menu and by default bios was loading win7.
searched forums and find out next solution wich I also did: 

                 -run ubuntu from cd -- open console -- type 

"*mount | tail -1*"

 huge line with numbers and letters appeared. next ive typed 

"*sudo grub-install --root-directory=media/ "*that huge line of nrs and letters*" dev/sda --recheck*"

that was a solution so ubuntu would show in the boot menu besides win7. it didnt worked. now its starting by default ubuntu without any menus in bios. 

before asking for help i have to say im an amateur, i desperately need both ubuntu and win, both os are 64bit ,my pc is a notebook asus n61jv.

..and now im shouting for help.
 **Please, HOW or WHAT should I do to have them both without a major headache everytime i boot this virtual machine ..**

---

### Post by Foxheadz on 2011-02-24
Well if your booting into ubuntu normally try just running ```
sudo update-grub
```

---

### Post by gabrel on 2011-02-24
> **Foxheadz said:**
> Well if your booting into ubuntu normally try just running ```
sudo update-grub
```
omg its working. just restarted the pc and my whole menu was there.
thank you foxheads. i shoud buy you a bear or sth :)

---

### Post by Foxheadz on 2011-02-24
Lol no problemo. Also if you find your selection screen kind of ugly you can download BURG/burg-manager it easily lets you add cool themes to your plain grub screen
[http://www.omgubuntu.co.uk/2010/06/get-animated-themed-icon-only-grub-menu-using-burg-now-simple-to-use/](http://www.omgubuntu.co.uk/2010/06/get-animated-themed-icon-only-grub-menu-using-burg-now-simple-to-use/)

[http://www.omgubuntu.co.uk/2010/11/burg-boot-manager-tool-updated-1-0/](http://www.omgubuntu.co.uk/2010/11/burg-boot-manager-tool-updated-1-0/)

---

### Post by gabrel on 2011-02-25
thanks man..again i appreciate.boot menu, its ok as it is.now im learning about wine and making use of this little miracle. photoshop, corel draw and ableton live under ubuntu would surely be awsome.

---

### Post by Foxheadz on 2011-02-25
Why use photoshop under wine when you can use gimp the free gnu version on photoshop. Also mind switching this thread to SOLVED by using the thread tools at the top

---

