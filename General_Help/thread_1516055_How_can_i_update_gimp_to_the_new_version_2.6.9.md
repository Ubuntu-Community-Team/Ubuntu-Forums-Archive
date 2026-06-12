---
title: "How can i update gimp to the new version 2.6.9?"
date: 2010-06-23
forum: General Help
---

### Post by aviramof on 2010-06-23
A few hours ago one of my sites posted a new gimp version for Linux but i don't want bz2 files i want deb/ppa anyone know where i can one of those things?

Thanks in advance.

---

### Post by SoFl W on 2010-06-23
Is this an official release?  According to the [GIMP website]("http://www.gimp.org/") the last update was in December of 2009.  The Ubuntu packages always seem to be a little behind on the official releases, but the GIMP site does have install info:

> *[COLOR=DimGray]Ubuntu, Debian[/COLOR]*
[COLOR=DimGray]Ubuntu or Debian users can simply run apt-get install gimp  to get the latest stable release of GIMP.[/COLOR][http://www.gimp.org/downloads/](http://www.gimp.org/downloads/)

---

### Post by aviramof on 2010-06-23
I found this:
[http://registry.gimp.org/node/24523](http://registry.gimp.org/node/24523)

and here is a link for linux:
[ftp://ftp.gimp.org/pub/gimp/v2.6/gimp-2.6.9.tar.bz2](ftp://ftp.gimp.org/pub/gimp/v2.6/gimp-2.6.9.tar.bz2)

---

### Post by SoFl W on 2010-06-23
And now it appears on the Gimp main page.  The debs should be available soon, but the ubuntu versions might need a little while later to catch up.

I just clicked on a few US mirrors, it isn't posted on some of them yet.

---

### Post by maizuddin35 on 2010-06-23
if you want to update to gimp 2.7 with one window, this the way

add the repository
[B]sudo add-apt-repository ppa:matthaeus123/mrw-gimp-svn

[/B]then update the and upgrade 
[B]
sudo apt-get update && sudo apt-get upgrade[/B]

try out your gimp.

a reminder this one is not stable yet.

---

### Post by aviramof on 2010-06-28
So whats up with the ubuntu stable package of gimp 2.6.9?

---

### Post by aviramof on 2010-06-28
You know this is all very ridiculous i mean what's the point of ppa's if no one is updating them on time and i'm not talking just about gimp i'm talking about a lot of things.

---

### Post by crichard on 2010-06-29
> **maizuddin35 said:**
> if you want to update to gimp 2.7 with one window, this the way

add the repository
[B]sudo add-apt-repository ppa:matthaeus123/mrw-gimp-svn

[/B]then update the and upgrade 
[B]
sudo apt-get update && sudo apt-get upgrade[/B]

try out your gimp.

a reminder this one is not stable yet.

FYI, I'm using this PPA, It's pretty stable, at-least for me.  If you want to install GIMP 2.6.9, you can even try this PPA 
**sudo add-apt-repository ** **ppa:ferramroberto/gimp**

[B]sudo apt-get update && sudo apt-get upgrade

[/B]If you noticed, this particular PPA is updated on 23rd of June, the very same-day GIMP released it but I prefer to experiment with beta versions, So, I'm using this PPA **ppa:matthaeus123/mrw-gimp-svn**

---

### Post by aviramof on 2010-06-29
Just to let you know gimp 2.7.1 final version have just been released will see how long would it take for it to update in the main repos or other ppa's.

---

### Post by crichard on 2010-07-10
> **crichard said:**
> you can even try this PPA 
**sudo add-apt-repository ** **ppa:ferramroberto/gimp**

[B]sudo apt-get update && sudo apt-get upgrade

[/B]If you noticed, this particular PPA is updated on 23rd of June, the very same-day GIMP released it **ppa:matthaeus123/mrw-gimp-svn**

As I told you earlier, this PPA  ferramroberto/linuxfreedomlucid  has updated the GIMP version to 2.6.10. Rightnow, GIMP 2.7.1 is an unstable development version. So, if you want to upgrade your GIMP to stable 2.6.10 version, try this PPA.

---

### Post by aviramof on 2010-07-10
I installed **2.7.3 from **[B]mrw-gimp-svn in the end. 
[/B]

---

