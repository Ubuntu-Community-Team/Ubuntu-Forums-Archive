---
title: "driver issue now wont boot????"
date: 2012-06-05
forum: General Help
---

### Post by gene simmons on 2012-06-05
hi all,i have a acer d270 with gma 3600 card and cedar trail chipset,i am running ubuntu 12.04 and have isntalled the gma 500 driver with instructions from here,i read that kernel 3.4 has gma support so i installed it but it wouldnt recognize my hardware,mouse or graphics card,so i figured the driver from the other kernel was affecting this so i disabled it in addidiional drivers,well no it wont boot in either kernel,i get the wont recognioze hardware in recovery mode warning,i can get to a root termninal but cant seem to get past that,i can get to a text login stage but thats as far as that goes,how can i enable that driver again via terminal or get past the text login stage,pplease help as i have spent alot of time getting ubuntu to look how i want i dont want to have to format and start again,thanx for any tips

---

### Post by dino99 on 2012-06-05
the latest 3.3.4 kernel might work, but better to test with 3.4.1

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4.1-quantal/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4.1-quantal/)

download into an empty folder the required files: 1 image (...i386.deb) + 2 headers (...all.deb & ...i386.deb), then from there:

sudo dpkg -i *
sudo update-grub

note: before running the above command, be sure that dkms is installed

[http://blog.bodhizazen.net/linux/fedora-17-gma500-poulsbo/](http://blog.bodhizazen.net/linux/fedora-17-gma500-poulsbo/)

---

### Post by gene simmons on 2012-06-05
thnx for the reply,i cant boot into linux to try a diferent kernel though,i need some help enabling the driver i have via terminal or some tips on how to boot via recovery,i cant seem to get it to boot,i can get to a text login and thats about it,any help would be great thanx

---

### Post by gene simmons on 2012-06-05
does anyone know how to boot from console login?i am in recovery and i can get to the login and thats about it,once it boots i shoudl be able to enable the driver thats causing this problem

---

### Post by mikewhatever on 2012-06-07
> **gene simmons said:**
> does anyone know how to boot from console login?i am in recovery and i can get to the login and thats about it,once it boots i shoudl be able to enable the driver thats causing this problem

By the time you see the console login, the system is usually booted. I can only guess that you must have meant the graphical desktop, which has nothing at all to do with booting. ;)

Which driver have you installed? Why do you want to enable the driver that causes problems?

---

### Post by gene simmons on 2012-06-08
sorry yes i meant the graphical desktop,i needed to enable the gma 500 driver,i disabled it to try another kernel,by disabling it i coudnt boot into either kernel,the one made for the gma driver or 3.4 like i wanted to try,i gave up and reinstalled ubuntu alltoghetehr,i tried 12.10 and was very  disapointed so im back on 12.04 and i installed the gma 500 driver again and all is well,only took a day from my life haha:lolflag:

---

