---
title: "HP Photosmart B110a"
date: 2011-01-03
forum: General Help
---

### Post by nomko on 2011-01-03
Hello,
 
First of all: i wish you all the best for 2011!
 
I've bought a HP Photosmart printer, HP Photosmart wireless e-All-in-One printer - B110a and i've got a problem installing it properly. I'm using Ubuntu 10.04.1 LTS version. When i connect the printer, Ubuntu recognizes it as the Photosmart B109 printer. Can i use this driver or does it conflict with my printer? 
 
When i go to the site of HP and search for a driver, it directs me to this site: [http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html) and from this site i'm directed to [http://sourceforge.net/projects/hplip/files/hplip/](http://sourceforge.net/projects/hplip/files/hplip/) (version 3.10.9).
 
I've downloaded that latest hplip file as a .run file and installed it. My printer is recognized proparly, but when i try to print a colored image, it comes out black/white. Something is not crrect. Does anyone recognize this problem with this type HP printer?
 
And how can i make it print with colours??
 
Many thanks in advange for your input!!
Nomko

---

### Post by nomko on 2011-01-03
Nobody?

---

### Post by bigman_3xl on 2011-01-04
Hi there.
Any progress with the printer? Thinking of purchasing the same printer.


  (\/)
 (0_O)
(>   <)

---

### Post by nomko on 2011-01-05
> **bigman_3xl said:**
> Hi there.
Any progress with the printer? Thinking of purchasing the same printer.
 
 
(\/)
(0_O)
(> <)
 
I've contacted the helpdesk of HP here in Holland and according to them it has to do with an error during alignment of the printer. I received an instruction by email so i have to ty that.

---

### Post by guyvdv on 2011-02-13
> **nomko said:**
> I've contacted the helpdesk of HP here in Holland and according to them it has to do with an error during alignment of the printer. I received an instruction by email so i have to ty that.
hello, i was thinking about the B110A printer scanner in ubuntu10.10
Did you had succes
Ben je eruit gekomen methet installeren van de printer in ubuntu?
Ik heb een epson SX510W , maar de scanner krijg ik niet aan de praat

hg guy van der velden

---

### Post by JM1082 on 2011-05-26
I've got the same printer and she works a treat in Windows, but if HP don't support Ubuntu then where can I go for answers?

:confused:

---

### Post by Matt__ on 2011-05-26
I have installed two of these printers and they work [faultlessly on ubuntu 10.04, 10.10 and linux mint Julia.]("http://ubuntuforums.org/showthread.php?p=10837781#post10837781")

Remove anything to do with the 109 version of the printer then use the PPA to get the latest version.
```
sudo add-apt-repository ppa:hplip-isv/ppa 

sudo apt-get update

sudo apt-get install hplip
```
Add the printer from the hplip GUI (may need to add it from software center).
Both simple scan and xsane pick up the scanner and work 100%

---

