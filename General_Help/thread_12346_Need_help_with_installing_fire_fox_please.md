---
title: "Need help with installing fire fox please"
date: 2005-01-23
forum: General Help
---

### Post by Eejay on 2005-01-23
I just finished installing Ubuntu on my computer I really like it so far The only problem that I'm having with Ubuntu is with the Downloading method that it uses to extract downloads.
Ubuntu came pre equipped with fire fox 9 and I wanted to upgrade to fire foxes latest version so I went to fire foxes website and downloaded the tar bal now I can't find the download or know how to install it 

SUSE Linux ( The only version of Linux I know how to use) came with a program that extracted tar balls I'm not to sure about Ubuntu though.

Fire foxes website had instructions on how to install the latest release with Linux here is what the directions said to do> Extract the tarbal and run the installer like so: 
tar -xzvf firefox-1.0.installer.tar.gz
cd firefox-installer
./firefox-installer 
If you have Nautilus set up to run Executable Text Files you can just double click fire- fox-installer to run.

I followed the direction and still no go
I looked for the program Nautilus in the control panel and didn't find it 

Any suggestions on how to install fire fox will be greatly appreciated

---

### Post by akurashy on 2005-01-24
you really but really dont need to do anything of extract or anything
here is a example of how gnome do it oO

go to Computer -> System Configuration -> Synaptic Package manager

it shows all the package you need
just remember to enable all the repository links
and there is a repository link you need to add to download firefox (is here on this forum)

 Synaptic Package manager: It automatic downloaded it from the vault and install it and compile it for you. :)

---

### Post by poofyhairguy on 2005-01-24
[QUOTE=Eejay]I just finished installing Ubuntu on my computer I really like it so far The only problem that I'm having with Ubuntu is with the Downloading method that it uses to extract downloads.
Ubuntu came pre equipped with fire fox 9 and I wanted to upgrade to fire foxes latest version so I went to fire foxes website and downloaded the tar bal now I can't find the download or know how to install it 

SUSE Linux ( The only version of Linux I know how to use) came with a program that extracted tar balls I'm not to sure about Ubuntu though.

Fire foxes website had instructions on how to install the latest release with Linux here is what the directions said to do> Extract the tarbal and run the installer like so: 
tar -xzvf firefox-1.0.installer.tar.gz
cd firefox-installer
./firefox-installer 
If you have Nautilus set up to run Executable Text Files you can just double click fire- fox-installer to run.

I followed the direction and still no go
I looked for the program Nautilus in the control panel and didn't find it 

Any suggestions on how to install fire fox will be greatly appreciated[/QUOTE]


I used the backports....but you will have to remember to uninstall and reistall Firefox when hoary comes (not big deal. Just install backport now, then uninstall firefox before you update to hoary, then install hoary's firefox).

[http://sourceforge.net/projects/ubuntu-bp](http://sourceforge.net/projects/ubuntu-bp)

---

### Post by pseudonym on 2005-01-24
And if you would prefer Firefox 1.0 to be in a language other than English, check this page - [http://www.ubuntuforums.org/showthread.php?t=11369&page=2](http://www.ubuntuforums.org/showthread.php?t=11369&page=2) (although the range of localisation packages available at this time is still fairly limited).

---

### Post by clparker on 2005-01-24
Dude, I had the same problem, but this is by far the easiest way to get it done in english and on an Intel system.
 [url="http://ubuntuforums.org/showthread.php?t=11369&referrerid=2069"]
 http://ubuntuforums.org/showthread.php?t=11369&referrerid=2069[/url]
 
 Lemme know if that works.

---

### Post by Eejay on 2005-01-24
username@linux:~ $ sudo gedit /etc/apt/sources.list
username@linux:~ $ sudo apt-get update
Hit [http://ubuntu-bp.sourceforge.net](http://ubuntu-bp.sourceforge.net) warty-backports/main Packages
Hit [http://ubuntu-bp.sourceforge.net](http://ubuntu-bp.sourceforge.net) warty-backports/main Release
Hit [http://ubuntu-bp.sourceforge.net](http://ubuntu-bp.sourceforge.net) warty-backports/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/main Release
Hit [http://ubuntu-bp.sourceforge.net](http://ubuntu-bp.sourceforge.net) warty-backports/universe Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/restricted Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/main Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/restricted Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/main Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/restricted Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/main Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/restricted Release
Reading Package Lists... Done
username@linux:~ $

---

### Post by Eejay on 2005-01-24
I wrote the following lines below the bottom page [http://ubuntu-bp.sourceforge.net/ubuntu](http://ubuntu-bp.sourceforge.net/ubuntu) 

Then typed sudo apt-get install mozilla-firefox into the terminal 

A error message came back saying invalid operation install 
I wasn't sure rather to save the file as “save as” or just click the floppy icon so I did both then saved the file to app 

everything seemed to have worked, everything but the last part 

Quote:
sudo gedit /etc/apt/sources.list 
add at the bottom: 
Quote:
deb [http://ubuntu-bp.sourceforge.net/ubuntu](http://ubuntu-bp.sourceforge.net/ubuntu) warty-backports main universe 
save the file and get back to the terminal and tell it to update by typing: 
Quote:
sudo apt-get update 
Quote:
**sudo apt-get install mozilla-firefox**

---

### Post by akurashy on 2005-01-24
try sudo apt-get install firefox

---

### Post by Eejay on 2005-01-24
I don't know what else to do 
I tried editing the lines to make sure they were where they were supposed to be and they were. I repeated the steps mentioned on the thread and nothing seemed to have work the only part that sends out error messages is the last part where it says sudo apt-get install mozilla-firefox
Any suggestions on how to get FF up and running will be appreciated  :???:

---

### Post by pseudonym on 2005-01-25
Try uninstalling the version of FF you have at the moment, and then install FF 1.0 using apt-get or synaptic. You will be asked to uninstall 'ubuntu-desktop' but don't panic - this is just a metapackage which doesn't include any code. Just re-install that later if you wish (especially before upgrading to Hoary later on). I did all these things and have not had any issues.

---

### Post by Eejay on 2005-01-25
[QUOTE=pseudonym]Try uninstalling the version of FF you have at the moment, and then install FF 1.0 using apt-get or synaptic. You will be asked to uninstall 'ubuntu-desktop' but don't panic - this is just a metapackage which doesn't include any code. Just re-install that later if you wish (especially before upgrading to Hoary later on). I did all these things and have not had any issues.[/QUOTE]

Bingo !
Not sure but I have a felling that the old version was somehow interfering with the installation of the new one.

Thanks for the replys everybody :D

---

### Post by pseudonym on 2005-01-25
Glad you got it working. I think you might be right about installing new version over old. At Mozilla's website they say not to do that. Not sure how well Ubuntu's package management system gets around this, though.

---

