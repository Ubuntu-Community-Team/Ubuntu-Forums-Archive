---
title: "IT technician needs advice on some things"
date: 2011-01-04
forum: General Help
---

### Post by uberlube on 2011-01-04
hello all! Ive been using linux for about the last 5 years and within the last year i decided to get serious about my love for IT and got myself A+ certified. Since then I landed myself a job as a resident technician fixing and setting up computers. My employers are great and they have given me the flexibility of using linux and open source tools, alongside windows, to do my job as i see fit.

this has gone quite well for me but there are a few tasks that i need to complete on a regular basis that give me grief while using ubuntu. the first that comes to mind is when im doing a backup of a customers hard drive and all they want is their photos. the first thing that comes to mind is to do a recursive scan and copy of all photo extension such as .jpg and .png so simple right? well whenever i try to accomplish this using nautilus it usually takes forever to finish finding them all and if i try to copy them to another medium, it usually ends in a crash. im not using weak hardware either so we can rule that out. i dont get any joy using programs like catfish either. my next idea was to accomplish this via command line. from what i know about bash i came up with this command:

```
sudo cp -R *.jpg /media/disk
```

this looks reasonable to me to recursively search from the working directory but it doesnt accomplish what i need. am i going about it the wrong way?

anyways id would appreciate some relevent info or suggestions on how i can accomplish this without having to rely on windows. also if u have any suggestions for great tech tools id love to try them out. so far these are my favs:

parted magic (best toolset EVER)
trinity recovery disk
system rescue CD

thanks for taking the time to read this and i hope the new year finds you well d-(^.')z

uberlube

(ps id like to keep this thread going from work in case i have any more related questions)

---

### Post by tshirtdr1 on 2011-01-04
When I need to recover files from a win hard drive, I usually physically install the hard drive into my linux system, mount it, and then get the files off. Have you tried this from konqueror: Tools>Find File> *.jpg Then drag them to a new directory or a big fat DVD. You can get a hard drive docking station for SATA and IDE that will allow you to plug the drive in easily. Love the GUIs! Good luck.

From Gnome at a terminal you can type "sudo apt-get install konqueror" and you get some base KDE packages, including konqueror. Can't live without it. Good luck.

---

### Post by uberlube on 2011-01-05
thanks for the quick reply. i have not yet used konqueror as im using the gnome edition and didnt want to go as far as installing KDE packages although it couldnt hurt to try. also im working in a professional tech center so weve got all the goodies for working with loose hard drives such as SATA/PATA to usb devices n such.

---

### Post by nothingspecial on 2011-01-05
How about find
```
find ./ -type f \( -name '*.jpg' -o -name '*.png' \) -exec cp '{}' /media/disk \;
```

---

### Post by coldraven on 2011-01-05
In Windows if you were not using Total Commander you were not really living. [http://www.ghisler.com/](http://www.ghisler.com/)
Krusader is the next best thing for us Ubuntu users. It's in the Software Centre.

Tip: after you install Krusader it will run through your installed archive utilities. Just click "Next" until it has finished. Afterwards you might like to install any that are missing.
Just look in Settings>Configure>Archives
Root mode Krusader is very powerful/dangerous!!

---

### Post by uberlube on 2011-01-05
> **nothingspecial said:**
> How about find
```
find ./ -type f \( -name '*.jpg' -o -name '*.png' \) -exec cp '{}' /media/disk \;
```

wow all that eh, lol. thnx ill give it a go next time im in need :D

---

### Post by uberlube on 2011-01-05
> **coldraven said:**
> In Windows if you were not using Total Commander you were not really living. [http://www.ghisler.com/](http://www.ghisler.com/)
Krusader is the next best thing for us Ubuntu users. It's in the Software Centre.

Tip: after you install Krusader it will run through your installed archive utilities. Just click "Next" until it has finished. Afterwards you might like to install any that are missing.
Just look in Settings>Configure>Archives
Root mode Krusader is very powerful/dangerous!!

total commander looks interesting, gonna d/l it right now. tyvm for reminding me about krusader, it is definitely a fantastic tool, i remember using it in kde 3.5 wayyy back in the day. ill install it today and see if the KDE packages handle the transfer of large amounts of files better than nautilus.

---

### Post by uberlube on 2011-01-08
bumpity bump bumperoo. id still like to know, if anyone can answer, why gnome/nautilus has such a hard time copying large amounts of files.

---

### Post by uberlube on 2011-01-08
> **uberlube said:**
> bumpity bump bumperoo. id still like to know, if anyone can answer, why gnome/nautilus has such a hard time copying large amounts of files.

i was doing some research just now and read a little about the XFS fle system. if i were to switch my / to XFS would i get better transfer speeds and stability? or would that only benefit me if the filesystem i was transferring from was XFS?

---

