---
title: "Problem with gnome-shell-extensions-user-theme"
date: 2012-09-08
forum: General Help
---

### Post by irem-altan on 2012-09-08
Hello all,
I'm trying to install themes with gnome tweak, and I need to install gnome-shell-extensions-user-theme because otherwise I cannot see the shell extensions tab.  However, I cannot install shell extensions.  I have tried to install by adding the ppa with the following:

sudo add-apt-repository ppa:webupd8team/gnome3

then, 
sudo apt-get update

Finally, when I try to install:
sudo apt-get install gnome-shell-extensions-user-theme

It gives an error:
The following packages have unmet dependencies:
 gnome-shell-extensions-user-theme : Depends: gnome-shell-extensions-common but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


I am convinced that there is a problem with the package.  So I went on and tried to install the extensions from the website:
[https://extensions.gnome.org/](https://extensions.gnome.org/)

But even though I use firefox (15.0), I cannot see the "switch" that is being mentioned to install the extension.
Maybe the version of firefox is too new.

Is there any workaround that you know of?

(By the way, I use Ubuntu 12.04, freshly downloaded and installed. )

Thanks in advance,
Irem

---

