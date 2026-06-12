---
title: "I'm not sure I have Java installed correctly"
date: 2006-02-04
forum: General Help
---

### Post by JeffV on 2006-02-04
I just installed Ubuntu on my machine and I was attempting to install Java SDK 1.5 update 6.  I followed all the directions here: [https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=AddingJavaSupport](https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=AddingJavaSupport)

It seemed to work, but if I type "java -version", it says "java version 1.4.2".  If I type javac -version, it correctly says version 1.5.  Does this mean I didn't get the newer runtime environment installed correctly?

---

### Post by dcstar on 2006-02-04
[QUOTE=JeffV]I just installed Ubuntu on my machine and I was attempting to install Java SDK 1.5 update 6.  I followed all the directions here: [https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=AddingJavaSupport](https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=AddingJavaSupport)

It seemed to work, but if I type "java -version", it says "java version 1.4.2".  If I type javac -version, it correctly says version 1.5.  Does this mean I didn't get the newer runtime environment installed correctly?[/QUOTE]
The SDK is the Software Development Kit, which to my knowledge is not the Runtime.

You want sun-j2re1.5

---

### Post by njzillest on 2006-02-04
you can get runtime from Automatix.  search it on the forums or google.

---

### Post by JeffV on 2006-02-04
I could have sworn it said the SDK also includes the runtime environment.  When I installed it for Windows it did.  Oh well...I'll just go ahead and install the runtime package.  Thanks!

---

### Post by cutOff on 2006-02-04
You could try 'java -version' from a console.

---

### Post by JeffV on 2006-02-04
Ok, I think I figured out what happened.  I think it did install the JRE 1.5 because the directory and files exists for it, however there also a directory for JRE 1.4.  So I'm guessing that it did install the new JRE, but because the old one is still installed it is defaulting to that.   So how do I fix this?  How do I remove JRE 1.4 but keep JRE 1.5?

---

### Post by JeffV on 2006-02-04
Never mind.  I figured it out.  I specified the default version to use by typing:

sudo update-alternatives --config java

---

### Post by nomad311 on 2006-02-15
[QUOTE=JeffV]Never mind.  I figured it out.  I specified the default version to use by typing:

sudo update-alternatives --config java[/QUOTE]

amazing ive been looking for an easy solution like this for a while ...i installed 1.4 unwittingly and then install 1.5 but couldnt use it ...so i have gone through the manaula install instructions on the site ...wit no luck so i thought i had to change a bunch of system varibles ...but couldnt find out which ones

then i resulted to runing programs with the -vm arg didnt work with everything *cough*azureus*cough* so i was planning to just stab my comp and see whos the boss then!

no more bit tornado GO AZUREUS

thanks for that
-nomad311

---

