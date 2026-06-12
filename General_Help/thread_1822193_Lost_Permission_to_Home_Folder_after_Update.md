---
title: "Lost Permission to Home Folder after Update"
date: 2011-08-10
forum: General Help
---

### Post by doggage on 2011-08-10
Hello. Be forewarned: I'm a complete ubuntu novice. 

I was happily running Ubuntu Netbook Version 10.04 on my Dell Mini 10v, until I began having trouble booting up. I tried to upgrade to Ubuntu Netbook Version 11.04 to fix the problem. However, now I can not boot up unless it's to a USB drive with Netbook Version 11.04.

I'd like to copy my files to an external hard drive so I can copy them to a new Macbook. However, when I boot to the USB and try to view my files in my HOME folder and other folders, they are X-ed out. They say that I don't have permission to view the files since I did not create them. Again, I only want to get the files onto an external hard drive and onto my Macbook. 

Please help! How can I gain access to my files? Thanks in advance. - Tony

---

### Post by anaconda on 2011-08-10
run in terminal:
sudo nautilus

and you should have enough rights to do what you want

---

### Post by doggage on 2011-08-11
Thank you Anaconda. Now, when I go to the home folder now, I see a folder for myself and one for my wife. When I click on mine (where all my files are) I see two files: "Access-Your-Private-Data-desktop" and "READ-me.txt"

If I click on the first file I get a dialogue box: Untrusted Application Launcher - The application launcher "Access-Your-Private-Data.desktop" has not been marked as trusted. If you do not know the source of this file, launching it may be unsafe.

If I click on the READ-me.txt, it reads:

 THIS DIRECTORY HAS BEEN UNMOUNTED TO PROTECT YOUR DATA.
From the graphical desktop, click on:
 "Access Your Private Data"
or
From the command line, run:
 ecryptfs-mount-private


I opened terminal and ran that ecryptfs-mount-private, and the terminal read:
ERROR: Encrypted private directory is not setup properly

---

