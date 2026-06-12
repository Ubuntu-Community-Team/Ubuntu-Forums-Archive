---
title: "downloadable packages?"
date: 2006-03-09
forum: General Help
---

### Post by jeisma on 2006-03-09
hello!

after lots of googling.. forums.. i can seem to run apt-get to update and download packages..

just wondering if there are any downloadable packages similar to the ones you have in the mirrors (those you can find in sources.list?) that i can simply download, perhaps store on a cd, or put in the intranet, and tell sources.list to get updates there.

(im not sure if i used the right words or put stated my question right.)


thank you!

(ubuntu 5.10)

---

### Post by sublime on 2006-03-09
google the name of the program and youll most likely find the development website and you can download the source packages.  i always like to dl packages from the websites and compile myself so as to get the latest versions.

---

### Post by jeisma on 2006-03-09
hi!

thanks.

in that case, would you be using apt-get to install the package?

or you simply do the install yourself?


thank you!

---

### Post by byen on 2006-03-09
If you are asking us how to install the downloaded package...this is what you do:
1.Find the .deb version of the package which will work well with ubuntu (as ubuntu is debian based)
2.Open terminal and go to the dir where you stored the package and type the following:
sudo dpkg -i packagename.deb
sudo apt-get -f install

The first one installs the package
The second takes care of dependencies of they arise.

Hope that is what you were looking for..Goodluck!

PS- If you have downloaded other formats such as .tar or .gz or source package...there are many threads explaining step by step procedures. Its not that hard really!

---

### Post by jeisma on 2006-03-09
hello!

whats the difference when installing a package via :

sudo dpkg -i packagename.deb
sudo apt-get -f install
or 
executing the install of package

vs 

synaptic?

thanks!

---

### Post by byen on 2006-03-09
Im not expert but here goes:

- All packages in synaptic are stable and tested to work under Ubuntu.Only programs that have been tried and tested are usually included in the synaptic list.
whereas
-Packages installed from other sources may or may not work with Ubuntu. Most debs do but sometimes you can run into trouble  (which can be fixed by compiling the program). 

Bottom line...synaptic is an easy way to install software on your Ubuntu installation. It has tons (literally) of software and eases the installation process!

Well..that is the simple version! Hope it helps!

---

### Post by Sutekh on 2006-03-09
[QUOTE=byen]
- All packages in synaptic are stable and tested to work under Ubuntu.Only programs that have been tried and tested are usually included in the synaptic list.
whereas[/QUOTE]But not those in universe/multiverse/backports.  They *potentially* could be just as bad.  The [Masters of the Universe (MOTU)](https://wiki.ubuntu.com/MOTU) aim to make sure that the packages in the universe repository are good to use, but there are so many, and they come with no guarantee.


Still 
[QUOTE=byen]-Packages installed from other sources may or may not work with Ubuntu. Most debs do but sometimes you can run into trouble (which can be fixed by compiling the program).[/quote]
**byen** is right.  Installing packages (.debs) that aren't specifically tailored for Ubuntu could cause many problems.   If there is something that you want that isn't in any of the Ubuntu repositories, then you can always install from source.

---

