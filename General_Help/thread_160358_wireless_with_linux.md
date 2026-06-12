---
title: "wireless with linux"
date: 2006-04-14
forum: General Help
---

### Post by saithe on 2006-04-14
ok, havin some trouble with linux reading my wireless card. its  a builtin Broadcom card, and i got the linux dirver for it. but i am at a loss as how to install the drivers. i cant find any help files for it. any help would be greatly appricated. thanks

---

### Post by PriceChild on 2006-04-14
[https://wiki.ubuntu.com/?action=fullsearch&context=180&value=Broadcom&titlesearch=Titles](https://wiki.ubuntu.com/?action=fullsearch&context=180&value=Broadcom&titlesearch=Titles)

Might help you... if your card is part of the 43xx series

---

### Post by saithe on 2006-04-14
ok, how do i know which series it is? its a newer gateway laptop model mx 6123. it just said boradcam card. well, looking at the bottom, i found 2 model #'s, the other is MA2A. so i dont know.

---

### Post by PriceChild on 2006-04-14
Neither MA2A or ms 6123 gave me any joy on gateway's site.

The laptops listed there didn't even show what model network card was installed either.

Have you got the documentation that came with the laptop? even an install cd may have a windows driver on there, named with the wireless card's model.

I think it's pretty pointless using the How Tos i've shown you before we establish what model the card is.

Sorry that i don't know any other way, I'm a big noob too :)

---

### Post by saithe on 2006-04-14
ok, found out what version it is, if thatll help. its version 3.100.64.1, if that helps, and the driver date (windows) is 2/18/2005. so id assume its a newer one.

---

### Post by PriceChild on 2006-04-14
No i think that's just a driver version.

Can anyone else help here? I'm running out of ideas :)

---

### Post by xXx 0wn3d xXx on 2006-04-14
Go to: [http://support.gateway.com/support/drivers/dlcenter.asp](http://support.gateway.com/support/drivers/dlcenter.asp) and type in your serial number. Then you will see something like Broadcom Wireless Card ***** where the *'s are numbers. Then download it. It may be an exe so download and install wine. "sudo apt-get install wine" without the quotes. Then follow [ this tutorial. ](http://ubuntuforums.org/showthread.php?t=25683&highlight=Broadcom+chipsets)

---

### Post by saithe on 2006-04-14
hmm, ok. well, can i just assume that its a newer card?

---

### Post by PriceChild on 2006-04-14
You're such a beast MasterChief1234, almost like John himself.

See saithe, you just have to be patient, then someone who knows what they're doing will come along and help :)

---

### Post by saithe on 2006-04-14
ok master. but when i looked at that, the only available one on gateway was the one for windows xp. i went to the boradcom site and got a linux one, but theres 2 different versions.

---

### Post by xXx 0wn3d xXx on 2006-04-14
[QUOTE=saithe]ok master. but when i looked at that, the only available one on gateway was the one for windows xp. i went to the boradcom site and got a linux one, but theres 2 different versions.[/QUOTE]
You will need the windows version.

---

### Post by saithe on 2006-04-14
ok downloaded the file, and ran it. now, i run linux or something? im still very new to it, sorry for nubbish questions

---

### Post by xXx 0wn3d xXx on 2006-04-14
[QUOTE=saithe]ok downloaded the file, and ran it. now, i run linux or something? im still very new to it, sorry for nubbish questions[/QUOTE]
If you have wine and ran the exe open up the file browser to your home directory. Now, go to view and check "Show Hidden Files." Then go under .wine and then drive_c, and then it will _most likely_ be under cabs and then under some weird filename, like DOS-377487-or somthing like that. Then open that file and drag and drop the bcmwl15.inf and the bcmwl5.sys to you desktop and follow the tutorial that I linked you to earlier.

---

### Post by saithe on 2006-04-14
uh, whats wine?

---

### Post by xXx 0wn3d xXx on 2006-04-14
[QUOTE=saithe]uh, whats wine?[/QUOTE]
It's a windows emulator. It allows you to run .exe programs.

---

### Post by saithe on 2006-04-14
oh... ok. where do i get that? cause im still on windows, because i cant get online with linux until i get the wireless card working :D

---

### Post by xXx 0wn3d xXx on 2006-04-14
[QUOTE=saithe]oh... ok. where do i get that? cause im still on windows, because i cant get online with linux until i get the wireless card working :D[/QUOTE]
Can you connect to a wired connection. It is going to be very hard to do this from windows.

---

### Post by saithe on 2006-04-14
its likely, just have to move from where i am :P ill post when i get back on.

---

### Post by xXx 0wn3d xXx on 2006-04-14
[QUOTE=saithe]its likely, just have to move from where i am :P ill post when i get back on.[/QUOTE]
Very well, it will be much easier if you are on ubuntu.

---

### Post by saithe on 2006-04-14
ok, im on ubuntu. im redownloading the file, itll take about 10 minutes. what do i do in the meantime?

---

### Post by xXx 0wn3d xXx on 2006-04-14
[QUOTE=saithe]ok, im on ubuntu. im redownloading the file, itll take about 10 minutes. what do i do in the meantime?[/QUOTE]
Watch TV, and all that stuff. If you are downloading the drivers, then download and install wine or vice versa.

---

### Post by saithe on 2006-04-14
ok, got te driver for the card, did a search for wine, but cant seen to get it downloaded. i tried following the instructions, but they dont seem to be working right.

---

### Post by xXx 0wn3d xXx on 2006-04-14
[QUOTE=saithe]ok, got te driver for the card, did a search for wine, but cant seen to get it downloaded. i tried following the instructions, but they dont seem to be working right.[/QUOTE]
Download Wine [[here] ](http://prdownloads.sourceforge.net/wine/wine_0.9.10-winehq1-2_i386.deb?download)
Then when the .deb is in your home directory, open terminal and type:
> 
sudo dpkg -i  wine_0.9.10-winehq1-2_i386.deb It's not the latest version but it will work for now.

---

### Post by saithe on 2006-04-14
ok got it, and typed that. it said that the database area is being locked by another process

and i need to get going home, so ill be back on tomorrow morning around 12 noon

---

