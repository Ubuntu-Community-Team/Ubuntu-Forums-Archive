---
title: "Help installing Terratec Aureon 7.1 usb ubuntu 12.04"
date: 2012-06-01
forum: General Help
---

### Post by juliusjonzon on 2012-06-01
So I downloaded the driver, double klick on hthe downloaded file an instalation starts, complets and nothing happens...

I allso tried right klicking on the instalation from the cd and i get to the part where i have to pick my modell and there it stops...

Wery grateful for tipps and help!

Allso trie this but don't know what step 3, is...


[LIST=1]
[*]Download the Windows application from any source (e.g. download.com).  Download the .EXE (executable). 
[*]Place it in a convenient directory (e.g. the desktop, or home folder). 
[*]Open the terminal, and **cd** into the directory where the .EXE is located. 
[*]Type wine *the-name-of-the-application.extension* (e.g. wine realplayer.exe). 
[/LIST]

---

### Post by Cheesemill on 2012-06-01
.exe files are for Windows, not Linux. The drivers you have downloaded won't work with Ubuntu (not even with Wine).

It should work just by plugging it in as the kernel has some USB audio drivers built in. If not I'm afraid you won't get it to work as Terratec don't provide Linux drivers.

---

### Post by juliusjonzon on 2012-06-01
Downloaded pulseaudio and it started=)

Great sound in just under 2 hours!

Just out of interest why not with wine?

Thats what wine is for or?

---

### Post by Cheesemill on 2012-06-01
Wine can run some Windows *applications*, it doesn't work with drivers because it doesn't have direct access to the hardware in the same way a Windows or Linux installation does.

---

