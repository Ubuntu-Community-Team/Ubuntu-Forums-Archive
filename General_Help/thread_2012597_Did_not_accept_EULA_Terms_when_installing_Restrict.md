---
title: "Did not accept EULA Terms when installing Restricted Extras"
date: 2012-06-29
forum: General Help
---

### Post by snuffy47 on 2012-06-29
Hello

When installing Restricted Extras i did not accept the EULA terms and it told me to go back but I clicked forward

How do I launch that prompt again

I tried removing restricted Extras but doesnt seem to do it

12.04LTS

Also Flash is not working and I am thinking this is why :(  please help me

Found This in another post

sudo apt-get install --reinstall ttf-mscorefonts-installer


doingthis in terminal allows you to accept terms.  Using software center does not

---

### Post by MG&amp;TL on 2012-06-29
Well, if you're removed it, reinstalling it should do the trick. :)

---

### Post by snuffy47 on 2012-06-29
you have to re install through terminal

I am having another problem though

It says flash is installed but using firefox it does not work

Any help there?

---

### Post by MG&amp;TL on 2012-06-29
> **snuffy47 said:**
> you have to re install through terminal

I am having another problem though

It says flash is installed but using firefox it does not work

Any help there?

The software centre opens a terminal, but for some bizarre reason opens it *behind* the software centre. Or at least it did last time I used the software centre...ho hum.

Which restricted extras package did you install?

---

### Post by Lyfang on 2012-06-29
Try to update system from Terminal. Open the Terminal & execute the following commands: 
```
sudo apt-get update && sudo apt-get upgrade
```Fix broken packages, if any:
```
sudo apt-get -f install
```Reinstall Ubuntu Restricted Extras:
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by snuffy47 on 2012-06-29
Man I hate when things go wrong

Tried the above terminal steps and no work

The live cd worked fine 

O well more reading if any other ideas let me know

---

