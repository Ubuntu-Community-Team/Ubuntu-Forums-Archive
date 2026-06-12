---
title: "jre1.5 error"
date: 2006-01-24
forum: General Help
---

### Post by wizzkid on 2006-01-24
I installed Kubuntu from scratch. and trying to install the jre 1.5. I already installed the requirements

Im following this instructions
First install the required packages:
sudo apt*get install fakeroot java*package java*common
Create the Deb file for the install:
fakeroot make*jpkg jre*1_5_0_05*linux*i586.bin
Install The deb file
sudo dpkg *i sun*j2re1.5_1.5.0+update05_i386.deb
Now make Sun's java the default by running this command and selecting it.
sudo update*alternatives **config java

However I encounter this error
root@user:~# fakeroot make-jpkg jre-1_5_0_05-linux-i586.bin
Creating temporary directory: /tmp/make-jpkg.XXXXOYeYMm
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk.sh

anyone knows how to fix this?

---

### Post by bulldogzerofive on 2006-01-25
This is not a solution to your problem, however, are you aware that JRE 1.5 is in the repositories?

---

### Post by tokyovigilante on 2006-01-25
I don't see an error in that output, but there is one in your approach.

Fakeroot allows your regular user to masquerade as the superuser for the purpose of building the jre 1.5 deb. Therefore you should run it as your user, not as root. That should get you going.

@bulldogzero5: Really? Which one?

---

### Post by Jucato on 2006-01-25
[QUOTE=bulldogzerofive]however, are you aware that JRE 1.5 is in the repositories?[/QUOTE]


They are? which repositories? omg...  i was never aware of that.
My solution was to use automatix. It does make my life a bit easier (especially in installing Firefox 1.5), but kinda makes me fill a lot less smarter. :p 

Btw, jre 1.5 can also be installed through Automatix, last time I checked.

---

### Post by wizzkid on 2006-01-25
hi! Thanks so much for your replies. it worked now, i just updated my repo. :)

---

### Post by bulldogzerofive on 2006-01-25
[QUOTE=tokyovigilante]@bulldogzero5: Really? Which one?[/QUOTE]

I have no idea but I installed it via synaptic shortly after adding universe and multiverse... or it might have been in PLF.

---

### Post by noigeaR on 2006-01-25
sun java is neither in universe nor multiverse (only blackdown java 1.4 is).
i think you've got it from the ubuntu plf repository. [http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf)
they still only have jre1.5.0_update5 though. update 6 has been out for weeks now, so i've built my own .deb package of update 6.

---

### Post by bulldogzerofive on 2006-01-26
Yeah you're right; I wasn't on my Ubuntu computer when I wrote that.

I checked it now it was in PLF.

Although PLF runs a couple weeks behind the bleeding edge, i must say that I prefer it to building my own package every time they release an update...

---

### Post by noeluylee on 2006-01-26
Hi, yes the jre 1.5 can be located at PLF :-)

---

