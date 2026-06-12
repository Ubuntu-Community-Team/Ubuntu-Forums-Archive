---
title: "Libreoffice/11.04 prints uglier than Openoffice/10.10"
date: 2011-05-10
forum: General Help
---

### Post by quini on 2011-05-10
Hi,

I use to print some menus for a restaurant every year, using the "Bitstream Charter" font.

I upgraded from 10.10 to 11.04 as soon as it was out, and now I find my printer (HP Photosmart 2575) is printing the same documents much uglier.

I've already cleaned heads and:
-it prints the automatic test after cleaning the heads perfectly,
-it prints the documents as ugly as before 8-(

So it doesn't seem to be a printer problem (it also prints fine from for instance the image viewer (small letters are printed very clean)...

I think it's a Libreoffice problem, but... I completely uninstalled Libreoffice and installed Openoffice instead with exactly the same results.

I also don't think it's a font problem, because:
1. I've reinstalled the package xfonts-scalable (AFAIK it provides the Bitstream Charter font),
2. there're also thin lines on the document, and they are neither being printed clean/fine


Any idea on where to look for?  I'd really prefer not to have to reboot to windows to print (I've tryed openoffice under windows and it prints fine)...

TIA  ;)

---

### Post by Hagar Delest on 2011-05-13
Hi,

You can export as PDF first as a workaround.

You can also try to [reset your OOo user profile](http://user.services.openoffice.org/en/forum/viewtopic.php?p=58403#p58403) but don't transfer your personal data during the welcome process (if you had 2.x before), configuration files from the former version might corrupt the new profile.

---

### Post by quini on 2011-05-13
Hi,

I've deleted both ~/.openoffice & ~/.libreoffice directories, then started libreoffice and printed with the same result.

Also, exporting to pdf modifies the font and page size, so it's not perfect...

I'll finally go and print them from windows -shame-... but I understand it's 11.04 or 10.10 related (last time I printed them I used 10.04).

Thanks!  ;)

---

### Post by Hagar Delest on 2011-05-13
Have you tried the Linux Libertine font? It has quite nice looks.

---

### Post by nrundy on 2011-05-13
How do Prints from the internet look? Is it only occurring in Office?

---

### Post by kostkon on 2011-05-13
Yeah, try printing from other programs.

My HP printer prints fine all the documents coming from my 11.04 system (including LibreOffice). I'm saying "coming from" because the printer is connected to (and shared from) a 10.04 pc.

---

### Post by quini on 2011-05-22
Thanks for your replies.

Unfortunately I needed those documents printed as soon as possible, so I ended printing them through OpenOffice 3.3 in windows xp...

That was the last time I printed with my HP Photosmart 2575, and I've given it as a present to a friend (I'm waiting for my brand new Officejet 6500A Plus to arrive).

Thanks again  ;)

---

### Post by linuxinstalledfromhdd on 2011-05-22
I have a brother laser printer and after I tested Natty with it, it just spewed blank pages. I had to physically unplug it to make it quit. I rolled my system back, I didn't have to install any drivers or anything like that, and lo and behold my laser printer works perfect again.

---

