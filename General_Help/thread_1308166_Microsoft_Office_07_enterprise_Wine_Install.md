---
title: "Microsoft Office 07 enterprise Wine Install"
date: 2009-10-31
forum: General Help
---

### Post by Joe Ker1086 on 2009-10-31
Any tricks that anybody knows of to install MS office enterprise using wine? Every time I try to install it, it fails at about half way through. any ideas?

---

### Post by Daniel1994 on 2009-10-31
I think I read somewhere that Crossover("deluxe" version of wine) can run ms office. You should check it out.

Other than that, I have no idea. OOffice statifies all my office needs :)

---

### Post by lavadisco on 2009-10-31
Try this:

[http://ubuntuforums.org/showthread.php?t=1173365&highlight=Office+2007](http://ubuntuforums.org/showthread.php?t=1173365&highlight=Office+2007)

Worked for me.

---

### Post by Joe Ker1086 on 2009-10-31
I agree that open office is better but i have to take some classes where ms office is required (IE access 2007 class). I though crossover was only for MAC

---

### Post by Joe Ker1086 on 2009-11-06
Thanks Lavadisco I will try it.:D

---

### Post by Dark_Stang on 2009-11-06
> **Joe Ker1086 said:**
> I though crossover was only for MAC
Nope, crossover is for Mac and Linux. About a year ago crossover gave away a version for free for 1 day only. It was a pretty sweet deal.

And good luck with access. The last time I had a class with that we were given 2 options.
1. Use access
2. Do everything in SQL manually.
I used access for about 10 minutes on a school PC. Said F that, used my laptop to SSH into the server and login to Oracle. Then did everything with a few scripts. Soooo much easier.

Edit: Also, OpenOffice has a database application. AFAIK it's compatible with access.

---

### Post by e-nygma on 2009-11-06
Which version of wine are you using?  was able to install Office '07 on wine version 1.1.16.  I always had problems using other versions of wine, but version 1.1.16 worked perfectly for me.  You can grab the debian file from WineHq and double click it to install.  Once installed, insert the Office '07 CD and navigate to the setup.exe on the cd and choose open with "wine windows program loader."  Hope this helps.

---

### Post by Joe Ker1086 on 2009-11-07
> **e-nygma said:**
> Which version of wine are you using?  was able to install Office '07 on wine version 1.1.16.  I always had problems using other versions of wine, but version 1.1.16 worked perfectly for me.  You can grab the debian file from WineHq and double click it to install.  Once installed, insert the Office '07 CD and navigate to the setup.exe on the cd and choose open with "wine windows program loader."  Hope this helps.

Let me try the newest version, thanks for the heads up.

---

### Post by Joe Ker1086 on 2009-11-07
> **Dark_Stang said:**
> Nope, crossover is for Mac and Linux. About a year ago crossover gave away a version for free for 1 day only. It was a pretty sweet deal.

And good luck with access. The last time I had a class with that we were given 2 options.
1. Use access
2. Do everything in SQL manually.
I used access for about 10 minutes on a school PC. Said F that, used my laptop to SSH into the server and login to Oracle. Then did everything with a few scripts. Soooo much easier.

Edit: Also, OpenOffice has a database application. AFAIK it's compatible with access.
 I agree with the SQL comment, I hate access but unfortunately i have to take the class :mad:

---

### Post by SamD42 on 2009-11-07
I recently managed to install office 07 through Playonlinux. It configured and ran everything. All works great save for outlook!

Playonlinux is in the standard repos since Karmic, so grab it and give it a go. The way it configures everything for you from missing components to the best wine version for each program is fantastic.

---

