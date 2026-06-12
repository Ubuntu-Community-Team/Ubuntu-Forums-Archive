---
title: "update error"
date: 2012-01-04
forum: General Help
---

### Post by luunatik12 on 2012-01-04
i am getting the following error's during update:

W:GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures were invalid: BADSIG A8AA1FAA3F055C03 Launchpad PPA for Daniel Richter, W:Failed to fetch [http://ppa.launchpad.net/erik-b-andersen/rgba-gtk/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/erik-b-andersen/rgba-gtk/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/lkjoel/fix404/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/lkjoel/fix404/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

how to fix them?

thanks

---

### Post by claracc on 2012-01-04
Except fot the first site [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release, the rest of them are not located in the addresses given so, it is better you remove them from sources.list or through the gui interface in system, administration, software origins.

Respect to the first one, you have to import the correct gpg key in the launchpad ppa in order to do the updates. If the ppa is this one: [https://launchpad.net/~danielrichter2007/+archive/grub-customizer?field.series_filter=oneiric](https://launchpad.net/~danielrichter2007/+archive/grub-customizer?field.series_filter=oneiric), you have in read about installing, the way to import the GPG key: Adding this PPA to your system

You can update your system with unsupported packages from this untrusted PPA by adding ppa:danielrichter2007/grub-customizer to your system's Software Sources. (Read about installing)

---

### Post by luunatik12 on 2012-01-04
i got the badsig fixed (using y ppa manager to get signatures fixed, very nice tool), jus the 404 errors left, how do i remove from source list or other way. sorry m not very good at linux, but learning, as i want to use it more and more.

i found the /etc/apt/source.list.d folder, but i dont get option to remove those, or may be i dont knw how to remove them from there.

how do i remove those from the source.list.d folder?

.....ok i found how to remove using sudo rm /etc/apt/source.list command.....

ok all errors cleared ;)

thanks

---

### Post by claracc on 2012-01-04
> .ok i found how to remove using sudo rm /etc/apt/source.list command.....


But in this way you have removed your sources.list file which is used to update your system.

You can recover the file through the gui, deploying the menu in system, administration, software origins, then you'll have to introduce your pass. In the window appearing you have two tabs:

ubuntu's software, where you can tick free software supported by canonical (main), maintained by community (universe), private drivers for devices (restricted) and restricted software by copyright (multiverse).

Other software tab, where you can add by the button add the ppa's software you are interested in. You can read this link: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
in order to add the repositories.

---

### Post by luunatik12 on 2012-01-04
8-[8-[8-[ok but as me being a very nooby noob (lowest category of noobs) what is a gui in ubuntu 11.10 as there is just a dash home, the software origin is same as software sources u mean? or is it the one in synaptics manager cos thats the only place i saw the software origin.8-[

---

### Post by claracc on 2012-01-04
software origins is the same as software sources ( sorry it was my fault, because i have made a direct tranlation from my spanish system).

You read the link provided [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu) in order to recover the sources.list file.

I assume the link's information is valid for oneiric ocelot too

---

### Post by luunatik12 on 2012-01-04
ok ;)

thanks for your help and prompt replies.

---

### Post by claracc on 2012-01-04
You are welcome

---

