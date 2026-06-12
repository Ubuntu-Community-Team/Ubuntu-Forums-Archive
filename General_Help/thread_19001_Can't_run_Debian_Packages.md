---
title: "Can't run Debian Packages"
date: 2005-03-09
forum: General Help
---

### Post by JMY1983 on 2005-03-09
I am trying to double click on skype for debian and dillo for debian and both say that the files could not be read or something to that effect. Does installation take place through text commands instead of clicking?

---

### Post by Kimm on 2005-03-10
not sure what you mean... but if you mean installing a .deb package then type this in console...

> 
sudo dpkg -i <packagename>.deb


---

### Post by JMY1983 on 2005-03-10
[QUOTE=Kimm]not sure what you mean... but if you mean installing a .deb package then type this in console...[/QUOTE]
 Your instructions are correct, but I am running the amd64 version and these programs are i386. Is all I have to do restart and boot from a non-amd64 version then run them?

---

### Post by Slapdash on 2005-03-10
I think he means that if one downloads a .DEB package DBL clicking on it doesnt install it automatically like in Mepis or RPM in Mandrake.

---

### Post by JMY1983 on 2005-03-10
[QUOTE=Slapdash]I think he means that if one downloads a .DEB package DBL clicking on it doesnt install it automatically like in Mepis or RPM in Mandrake.[/QUOTE]
 That's correct, I can't double click on them to install. They are for i386 apparently.

---

### Post by Kimm on 2005-03-10
I doubt you can install i386 packages on an amd64 computer...

---

### Post by JMY1983 on 2005-03-10
[QUOTE=Kimm]I doubt you can install i386 packages on an amd64 computer...[/QUOTE]
 That's precisely my point. But I can't find an AMD64 version of either skype or dillo...

---

### Post by Kimm on 2005-03-10
well... that would be a problem... I doubt that (atleast) Skype has released the source, so you cant compile it...

Perhaps emulating the windows version in wine??

---

### Post by dermotti on 2005-03-10
Why the hate on double clicking to install!?

---

### Post by JMY1983 on 2005-03-10
[QUOTE=Kimm]well... that would be a problem... I doubt that (atleast) Skype has released the source, so you cant compile it...

Perhaps emulating the windows version in wine??[/QUOTE]
 Damn, too bad. I had a feeling having a 64 bit processor I was going to be left out in the cold on a few programs.

---

### Post by Kimm on 2005-03-11
now that I come to think of it... perhaps you could send them a mail offering t compile their software for the amd64 platform, then provide them with the binaries... I dono what they will say but its worth a shot

---

