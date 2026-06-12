---
title: "cant install opera"
date: 2010-01-03
forum: General Help
---

### Post by wicres on 2010-01-03
i wanted to install opera 9 in ubuntu 6.06 lts, i get an error message when it hits file 10
i spoke with my tech support, they said they have disabled automatic uptades since some updates interfere with the software i am using.  i can install updates , if the software crashes i can just restart to a saved backup.  if i post the error messages any help with getting updates so i can use opera?????? ty

---

### Post by zvacet on 2010-01-04
Dapper (6.06) is not supported any more.If you have some important files back them up and install new version of Ubuntu.Then you will b e able to install Opera.

---

### Post by wicres on 2010-01-04
we currently have 6.06 lts,    like i said certain deb updates conflict with our business software that is why updates are currently off they are currently testing new versions to make sure it doesnt conflict and cause the software to crash.

i guess ill have to wait out, continue to use ff, i know i use "internet exploder" with wine but i refuse to

---

### Post by zvacet on 2010-01-04
Do you have any machine to test Hardy (also LTS)?Maybe you can upgrade or do fresh install of Hardy if you can run all applications you want on it.

---

### Post by jamesisin on 2010-01-04
I hope you are able to get your version of Ubuntu updated soon.  In the meantime you can take a look at this post of mine for installing Opera:

[http://www.soundunreason.com/InkWell/?p=197](http://www.soundunreason.com/InkWell/?p=197)

You may be able to modify it for your older version, but I have a feeling that the latest versions will not work with your old OS.  Let me know if you have success.

---

### Post by wicres on 2010-01-04
[http://archive.canoical.co/ubuntu/dist/dapper-commercial](http://archive.canoical.co/ubuntu/dist/dapper-commercial) Release.gpg: Could not resolve 'archive-canoical.co,'
[http://archive.canocial.com/ubuntu/dist/dapper-commercial/main/binary-i386/packages.gz:](http://archive.canocial.com/ubuntu/dist/dapper-commercial/main/binary-i386/packages.gz:)
400 Not found
[http://archive.canocial.co/ubuntu/dist/dapper](http://archive.canocial.co/ubuntu/dist/dapper) commercial/main/binary-i386/Packages.gz: could not resolve 'archive.canoical.co

this is the error message i get when enable opera and install link :confused:

---

### Post by zvacet on 2010-01-05
Edit your source list with 

```
gksudo gedit /etc/apt/sources.list
```

and remove lines you add and add this one 

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

Save and close file.

```
sudo apt-get update
```

Find Opera in synaptic and install it.You will not be able to install Opera 10 versions,but Opera 9.As I said before test if your desired software works with Hardy and if it is install it.

---

### Post by wicres on 2010-01-05
i spent an hour with our tech support and opera would still not work


we have a quick-lube and the software has custom programs written for example graphical service reviews which requires java and other programs. *to make these work certain ubuntu 6.06 updates and packages conflict with this and the operating software. *they have tried ubuntu 8 and the software is not compatible, it crashes. *they are currently trying to re-write the software to be compatible with newer versions of ubuntu. * *for now we have use ff 1.5 or mozilla, *they tried ie6 for ubuntu, wine also has missing packages and wouldnt work, they are still going to try, * this has to be done after we close and have a good backup in case the system crashes, so we reinstall software and open for the next day.


ty for the input and help

---

### Post by mocoloco on 2010-01-05
Take a look at [Klik]("http://klik.atekon.de/").  I haven't used it for years but I think it's supposed to included dependencies for the app all in the package.  They have Opera available.

As far as your version, I would suggest to your IT that they just wait until April and switch to 10.04, which will be LTS.  That leaves them more support time than if they go for 8.04 which will not be supported after April 2011.

---

### Post by wicres on 2010-01-06
:Dfinally got it to work, *in one of the lines canonical was spelled wrong, it wasn't getting the updates, changed that and a few other changes,


we now opera 10 in ubuntu 6.06 lts

---

### Post by mocoloco on 2010-01-06
Great to hear.  If you get a chance mark this thread as solved.

---

### Post by jamesisin on 2010-01-07
Impressive.  I hope you can get the newest version of Ubuntu soon.

---

### Post by mister_p_1998 on 2010-01-07
[QUOTE=zvacet;8612734]Edit your source list with 

```
gksudo gedit /etc/apt/sources.list
```

and remove lines you add and add this one 

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main


I'm still running gutsy on my Vaio Laptop, do you know the archive repo for gutsy?

Steve

---

### Post by jamesisin on 2010-01-07
Follow these instructions substituting gutsy's Debian equivalent (I think it's sarge) for etch:

[http://www.soundunreason.com/InkWell/?p=197](http://www.soundunreason.com/InkWell/?p=197)

---

