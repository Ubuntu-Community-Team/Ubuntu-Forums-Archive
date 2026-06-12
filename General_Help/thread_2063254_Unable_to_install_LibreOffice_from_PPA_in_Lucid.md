---
title: "Unable to install LibreOffice from PPA in Lucid"
date: 2012-09-26
forum: General Help
---

### Post by learning_ on 2012-09-26
> **Irony said:**
> Follow the instructions here; [http://maketecheasier.com/replace-openoffice-with-libreoffice-in-ubuntu/2011/01/26](http://maketecheasier.com/replace-openoffice-with-libreoffice-in-ubuntu/2011/01/26)

I have followed this guide, and several others like it (identical to it) and I keep getting hung up at the following step:
```
sudo apt-get install libreoffice
```
No matter what I do it comes with the same error: ```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libreoffice: Depends: libreoffice-core (= 1:3.5.4-0ubuntu1~lucid1) but it is not going to be installed
               Depends: libreoffice-writer but it is not going to be installed
               Depends: libreoffice-calc but it is not going to be installed
               Depends: libreoffice-impress but it is not going to be installed
               Depends: libreoffice-draw but it is not going to be installed
               Depends: libreoffice-math but it is not going to be installed
               Depends: libreoffice-base but it is not going to be installed
               Depends: libreoffice-filter-mobiledev but it is not going to be installed
               Depends: libreoffice-java-common (>= 1:3.5.4~) but it is not going to be installed
               Recommends: libreoffice-gnome but it is not going to be installed or
                           libreoffice-kde but it is not going to be installed
E: Broken packages

``` 
:confused:
ANYONE with answers please help me out here. I've been searching for quite some time.

---

### Post by oldos2er on 2012-09-26
Post moved to its own thread.

---

### Post by learning_ on 2012-09-29
Thank you for the correction on the thread.

---

### Post by jerrrys on 2012-09-29
Im not so sure that autoremove gets the job done.  I think the [purge command]("https://help.ubuntu.com/community/AptGet/Howto#Removal_commands") would be a better choice.  But no matter now.

Open Nautilus and do a search on openoffice and remove any left over files.  Then:

sudo apt-get clean

sudo apt-get update

sudo apt-get install -f

---

