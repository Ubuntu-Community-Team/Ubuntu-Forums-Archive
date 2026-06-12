---
title: "problems with Epson stylus cx4300 scanner"
date: 2011-01-15
forum: General Help
---

### Post by ilantal on 2011-01-15
I have a problem with my Epson cx4300 scanner. I have it working to the stage that it is recognized by the scanner:

ilan@ilan-laptop:~$ scanimage -L
device `epkowa:interpreter:002:006' is a Epson (unknown model) flatbed scanner

I am using the instructions in

[http://ubuntuforums.org/showthread.php?t=908443](http://ubuntuforums.org/showthread.php?t=908443)

Both Simple Scan and XSane recognize it, but as soon as I start to scan it exits the program(s). It says in the above thread that I need to become part of the scanner group, and I think THIS is where the problem is.

If I go into System -> Administration -> Users and Groups -> Manage Groups, I am supposed to see scanner as one of the groups. Then I add myself to this group and I am done. The trouble is that in 10.10 there is no such group, so I can't add myself to it.

I discovered this first in the above thread where under the command line I tried to add myself to the scanner group and it told me there was no such animal. I found the GUI version to confirm the problem. I did add myself to the saned group but that didn't help.

So I have 2 questions: why is there no scanner group? Is the fact that the XSane and Simple scan exit connected to the fact that I am not part of the non existent scanner group?

Thanks,
Ilan

---

### Post by ellgor on 2011-01-16
Hi,

Go to this site "Avasys" and get their "imagescan.deb", go through the form filling in bit (as if for your printer, or nearest to it) and when the download page appears scroll right down until you see the "imagescan.deb" app, easily loads in with gdebi, needs a reboot to run properly.

Regards, Ellgor.

---

### Post by ilantal on 2011-01-17
Hi Ellgor,
Thanks for your reply. It turns out that I already did what you suggested. Before I had accomplished it scanimage -L would give me no output.

Since you suggested it, I tried it again. This time it did scan ONCE. After that it gave me an error and I had to reboot. After each reboot I can scan one single page and then it will return to the error.

I think it must be connected to the groups business. As I said there is no scanner group:
ilan@ilan-laptop:~$ sudo adduser ilan scanner
[sudo] password for ilan: 
adduser: The group `scanner' does not exist.

I tried another suggestion mentioned:
sudo gedit /etc/udev/rules.d/45-libsane.rules

where I add something like
# Epson CX4300
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="083f", MODE="664", OWNER="lp", GROUP="scanner"

but since there is no group called scanner, the whole idea doesn't make sense. Maybe there is another group I can use, or I can somehow create scanner?

In any case I can now scan ONE page each reset instead of ZERO pages....

Still someone with more experience than I have should be able to suggest something.

Ilan

---

