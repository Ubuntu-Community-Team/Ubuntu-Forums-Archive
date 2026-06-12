---
title: "Can't install openoffice or libreoffice"
date: 2011-01-12
forum: General Help
---

### Post by yaoverstand on 2011-01-12
I tried to install LibreOffice on the recommendation of my friend and it failed to install.  Now I have neither LibreOffice or OpenOffice.  I also cannot install OpenOffice from the Ubuntu software center. what can i do to have either one of these.  I dont care which at this point lol.

---

### Post by kellemes on 2011-01-13
> **yaoverstand said:**
> I also cannot install OpenOffice from the Ubuntu software center.

Why?

---

### Post by MARP1961 on 2011-01-13
Do you have a working internet connection? If you do, is it using wi-fi or is it wired directly? Assuming you're connected to the internet then go to System, Administration and down the list to Update Manager. Open Update Manager then let it check for and apply all updates. Then go back to Software Centre to attempt to reinstall the office software of your choice. I assume you originally had Open Office but removed it? Ubuntu comes with it already in place.

---

### Post by yaoverstand on 2011-01-14
i did have open office to begin with, but i had to mess with it for some stupid reason.  i did the update manager thing and it didnt give me any updates for open or libre...just chrome.  I updated it anyway, then tried to reinstall open but no luck.

---

### Post by stoneage on 2011-01-14
How did you install libreoffice? From source? From a .deb? What happens when you try to install openoffice? Error messages? To be able to help you we need information.

You probably need to purge libreoffice before doing anything else, then reinstall openoffice.

---

### Post by Primefalcon on 2011-01-14
if yo try installing from the terminal, ```
sudo apt-get install openoffice.org
``` do you get an error message back, if so what does it say

---

### Post by RustyWyatt on 2011-01-15
Howdy,

I found the solution in another posting:

Re: help-Reinstall OOo in 10.04

I found a solution: Uninstall the 'ure' packages, then disable the libreoffice ppa. Then you can re-install openoffice.

Markus

and:

Thanks for the help! I also had to uninstall/update/reinstall uno-libs3.

From:   [http://ubuntuforums.org/showthread.php?t=1662355&highlight=reinstall+openoffice](http://ubuntuforums.org/showthread.php?t=1662355&highlight=reinstall+openoffice)

Thanks everyone!

Tom

---

### Post by yaoverstand on 2011-01-15
> **Primefalcon said:**
> if yo try installing from the terminal, ```
sudo apt-get install openoffice.org
``` do you get an error message back, if so what does it say

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  openoffice.org: Depends: openoffice.org-core (= 1:3.2.0-7ubuntu4.1) but it is not going to be installed
                  Depends: openoffice.org-writer but it is not going to be installed
                  Depends: openoffice.org-calc but it is not going to be installed
                  Depends: openoffice.org-impress but it is not going to be installed
                  Depends: openoffice.org-draw but it is not going to be installed
                  Depends: openoffice.org-math but it is not going to be installed
                  Depends: openoffice.org-base but it is not going to be installed
                  Depends: openoffice.org-report-builder-bin but it is not going to be installed
                  Depends: openoffice.org-officebean but it is not going to be installed
                  Recommends: openoffice.org-filter-binfilter but it is not going to be installed
E: Broken packages

this is what i got

---

### Post by stoneage on 2011-01-15
Which version of Ubuntu are you using?

The current OpenOffice for 10.10 is 1:3.2.1-7ubuntu1

---

### Post by gradinaruvasile on 2011-01-15
> **yaoverstand said:**
> I tried to install LibreOffice on the recommendation of my friend and it failed to install.  Now I have neither LibreOffice or OpenOffice.  I also cannot install OpenOffice from the Ubuntu software center. what can i do to have either one of these.  I dont care which at this point lol.

If you want to install LibreOffice go to

libreoffice.org

and download the archive containing the deb format, unpack it, go to that folders DEBS folder and in the terminal and do a 

sudo dpkg -i *.deb

then go into DEBS\desktop-integration folder

and do the same. This will install LibreOffice in a way that does not conflict with anything.

---

### Post by mike555 on 2011-01-15
You could go here and follow their instructions;
[http://www.webupd8.org/2011/01/install-libreoffice-in-ubuntu-from.html](http://www.webupd8.org/2011/01/install-libreoffice-in-ubuntu-from.html)

---

### Post by TGBaker on 2011-01-15
I used Ubuntu Tweak. It added: [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) to my repository list. When I selected LibreOffice in Synaptic it uninstalled OpenOffice first then installed LibreOffice. I'm running Ubuntu Studio 10.10

---

### Post by yaoverstand on 2011-01-25
> **mike555 said:**
> You could go here and follow their instructions;
[http://www.webupd8.org/2011/01/install-libreoffice-in-ubuntu-from.html](http://www.webupd8.org/2011/01/install-libreoffice-in-ubuntu-from.html)

this worked perfectly....thank you so much

---

