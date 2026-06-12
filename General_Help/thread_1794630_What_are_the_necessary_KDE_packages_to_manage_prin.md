---
title: "What are the necessary KDE packages to manage printer"
date: 2011-07-01
forum: General Help
---

### Post by gandaran on 2011-07-01
I'm trying to get my HP printer to work on Backtract 5 KDE (Ubuntu 10.04), I have installed 'system-config-printer-kde' and 'kde-printer-applet' plus the HP drivers but I think something is still missing cause I cant setup up the printer (clicking on add new printer I only have the option for network printer and new class printer) and if I try to print from any application there's only one option that is to file.
I'm sure there's a solution for this, I have searched a lot but can't find the list of packages necessary to manage printers.

---

### Post by DawieS on 2011-07-01
Do you have **cups** installed? It is available in Synaptic and normally auto-configures just about any type of printer, and also allows for customization.:grin:

---

### Post by gandaran on 2011-07-01
> **DawieS said:**
> Do you have **cups** installed? It is available in Synaptic and normally auto-configures just about any type of printer, and also allows for customization.:grin:
yes, cups is pre-installed on backtract 5 but I don't want to use cups, I want the normal Ubuntu/Kubuntu way of detecting and using printers.

---

### Post by SeijiSensei on 2011-07-01
CUPS **is** the "normal" way of connecting to printers in all flavors of Ubuntu.

---

### Post by DawieS on 2011-07-01
> **gandaran said:**
> I want the normal Ubuntu/Kubuntu way of detecting and using printers.
AFAIK **cups** is the normal (default) way of detecting and using printers in Ubuntu. I cannot remember having to install anything additional, and my Epson 915 worked perfectly out of the box.

---

### Post by collisionystm on 2011-07-01
> **gandaran said:**
> I'm trying to get my HP printer to work on Backtract 5 KDE (Ubuntu 10.04), I have installed 'system-config-printer-kde' and 'kde-printer-applet' plus the HP drivers but I think something is still missing cause I cant setup up the printer (clicking on add new printer I only have the option for network printer and new class printer) and if I try to print from any application there's only one option that is to file.
I'm sure there's a solution for this, I have searched a lot but can't find the list of packages necessary to manage printers.


Make your life easy. Install hplip

Its meant specifically for HP Printers.
Its available in most software repo's. Just search for hplip

here is the website.

[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

---

### Post by gandaran on 2011-07-01
hplip, hpijs, and hp-toolbox are installed, the HP drivers have nothing to do with my problem, my problem is setting up or detecting any printers the usual way, for this to work I need to install all packages Kubuntu uses for printing.
cups is installed but I don't want to use a cups-printer, I know very well how to set up a cups-printer but that isn't what I want as my aim is to get the hp-toolbox working.
I also had the problem getting sound and video to work on backtract 5 but after a few days searching I found out the missing phonon package, installed it and no problems with sound or video now but the printer setup is probing a lot more difficult, I have read some posts from users claiming printers don't work running as root, maybe it's true or not but I still think it's some dependency missing, I'll keep looking.

---

### Post by collisionystm on 2011-07-01
> **gandaran said:**
> hplip, hpijs, and hp-toolbox are installed, the HP drivers have nothing to do with my problem, my problem is setting up or detecting any printers the usual way, for this to work I need to install all packages Kubuntu uses for printing.
cups is installed but I don't want to use a cups-printer, I know very well how to set up a cups-printer but that isn't what I want as my aim is to get the hp-toolbox working.
I also had the problem getting sound and video to work on backtract 5 but after a few days searching I found out the missing phonom package, installed it and no problems with sound or video now but the printer setup is probing a lot more difficult, I have read some posts from users claiming printers don't work running as root, maybe it's true or not but I still think it's some dependency missing, I'll keep looking.

Okay so you open HPLIP, you hit add printer, and enter the ip address of the printer. It downloads the HP plugin and installs. Is this not happening?

---

### Post by gandaran on 2011-07-01
> **collisionystm said:**
> Okay so you open HPLIP, you hit add printer, and enter the ip address of the printer. It downloads the HP plugin and installs. Is this not happening?
No, I don't have a add printer option only a add network printer, this is the problem! if everything was working as it should it would detect the printer automatically.

---

### Post by collisionystm on 2011-07-01
You should see, Network, Usb, something else and advanced options. Click advanced options and hit manual discovery.

---

