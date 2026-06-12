---
title: "multifunction scanner not being recognised"
date: 2012-01-15
forum: General Help
---

### Post by dodderer on 2012-01-15
I have ubuntu 10.4. My printer is a multifunction Canon MG5150. I have  installed the drivers provided by canon , The printer works but launching simplescan or xsane results in a message "No devices found". Any advice or instructions on how to fix this greatly appreciated.

---

### Post by dino99 on 2012-01-15
The scanner is drived by scangearmp 

[http://translate.google.fr/translate?sl=fr&tl=en&js=n&prev=_t&hl=fr&ie=UTF-8&layout=2&eotf=1&u=http%3A%2F%2Fforum.ubuntu-fr.org%2Fviewtopic.php%3Fpid%3D4000047&act=url](http://translate.google.fr/translate?sl=fr&tl=en&js=n&prev=_t&hl=fr&ie=UTF-8&layout=2&eotf=1&u=http%3A%2F%2Fforum.ubuntu-fr.org%2Fviewtopic.php%3Fpid%3D4000047&act=url)

---

### Post by dodderer on 2012-01-15
Thanks dino99. I have installed 'scangearamp 1.60
but the scanner is not being recognised . when I launch simplescan I get the message no devices found

---

### Post by bluexrider on 2012-01-15
**Manually installing a scanner**

                                                                          There are some scanners that have less than complete  drivers from the SANE project. They can sometimes be used, but not all  the features may work.
                                    
[LIST=1]
[*]                       Make sure the Universe repository is enabled. The easiest way to do this is probably through **Synaptic**.
[*]                       Get the drivers by searching **Synaptic** for libsane-extras or at a terminal type:
                        
                       **sudo apt-get install libsane-extras**                         							
[*]                       Edit the /etc/sane.d/dll.conf and enable the right driver for your scanner. Look for the lines that say:
                        
                       # The following backends are not part of the SANE distribution # but are provided by the libsane-extras Debian package                         							
                       Below it are several commented out lines. Uncomment (delete the #) the right one for your scanner.
[*]                       Fire up sane and scan away.
[/LIST]
REF: [HERE]("https://help.ubuntu.com/8.04/printing/C/scanning.html")

---

### Post by cdoebbler on 2012-07-25
Your fix does not seem to work and even your reference is a broken link.

---

