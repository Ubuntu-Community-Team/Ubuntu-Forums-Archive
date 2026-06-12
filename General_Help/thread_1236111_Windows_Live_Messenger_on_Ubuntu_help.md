---
title: "Windows Live Messenger on Ubuntu help"
date: 2009-08-09
forum: General Help
---

### Post by xxhopingtearsxx on 2009-08-09
I'm a beginner at Ubuntu, and while there's already Amsn and Pidgin, I wanted to try Windows Live Messenger with wine.. The main reason I want to try it is because I like MSN Plus's chat logging, and if Windows Live Messenger works with Wine, then MSN Plus might work. Even if it doesn't, I want to try it.

Well, one thing the howto site I'm using tells me I need is "Install_{508CE775-4BA4-4748-82DF-FE28DA9F03B0}.msi".. I have the file. I don't know what to do with it. [http://forum.wine-reviews.net/wine-reviews/microsoft/msn-messenger-2008-and-2009-on-linux-with-wine.html](http://forum.wine-reviews.net/wine-reviews/microsoft/msn-messenger-2008-and-2009-on-linux-with-wine.html) is what I'm using.. Please explain how to use that file.. Remember, I'm a newbie.

---

### Post by coldReactive on 2009-08-09
Applications > Accessories > Terminal

use cd to get to your directory where the MSI is in.

type **wine file_name** and hit enter.

It may give an error saying it cannot execute or it may give help information. If it does either of these... then I can't help (as I have had it before, but the winehq community was of no help whatsoever.)

---

### Post by xxhopingtearsxx on 2009-08-09
DOes my .msi file have to be on a certain folder in my computer before i type in the terminal?

---

### Post by coldReactive on 2009-08-09
> **xxhopingtearsxx said:**
> DOes my .msi file have to be on a certain folder in my computer before i type in the terminal?

It would be best if the msi file was under drive_c (located in your home folder under the .wine hidden folder.)

---

### Post by zkriesse on 2009-08-09
Well to start with the wine software you apparently downloaded is not the correct one...go here to get the actual software. [http://www.winehq.org/](http://www.winehq.org/) That website gives you the actual software. To install wine in the terminal do this. Go to Applications-Accessories-Terminal. In the terminal window type the following in order given. First type cd. Just type the word, cd. Then hit enter. After that type the following WITHOUT QUOTES!!!!!!!!!!!!!!!!!!  "sudo apt-get *install* wine" After you type that WITHOUT THE QUOTES! hit enter. It will ask for your password. Type it correctly as it will NOT SHOW. Hit enter then follow the instructions. Let me know how it turns out and feel free to ask me any questions you got. Hope this helps.

---

### Post by xxhopingtearsxx on 2009-08-09
joey@ubuntu:~$ wine Install_{508CE775-4BA4-4748-82DF-FE28DA9F03B0}.msi
wine: could not load L"Z:\\home\\joey\\Install_{508CE775-4BA4-4748-82DF-FE28DA9F03B0}.msi": Bad EXE format for 
joey@ubuntu:~$ 


PS: I already have wine.

---

### Post by zkriesse on 2009-08-10
TYPE WHAT I PREVIOUSLY POSTED!!!!! NOT WHAT YOU DOWNLOADED!!!!:cool:

---

