---
title: "Problems with new KDE 3.5.2"
date: 2006-04-07
forum: General Help
---

### Post by Hygelac on 2006-04-07
I've had a few problems since upgrading to the (otherwise nice) KDE 3.5.2.  For instance, when I run Konsole and try to "Configure Konsole," I get an error message saying that the library files for 'kcm_konsole.la' were not found 'in paths.'  Does anyone know how to fix this?  (For that matter, is this the place to ask?)

Another problem I now have is that I cannot change the screen resolution: that part of kcontrol (and everywhere else it used to be) is gone!  I can still change the resolution by manually editing xorg.conf though.  Once again, does anyone know where that resolution control went?

---

### Post by nykobing on 2006-04-07
I can only help you with the second part of your question because someone here was nice enough to post the answer for me yesterday.

[http://kubuntuforums.net/forums/index.php?topic=4373.0](http://kubuntuforums.net/forums/index.php?topic=4373.0)

That returns everything under kcontrol.

---

### Post by Hygelac on 2006-04-07
Thanks for that; I now have my resolution control back.  I can also see from your post that there is a 'kdesu' command; I never knew that!  Out of curiousity, do you have the same problem with Konsole as I do?  I have had it happen to two (out of a total of two) computers since I upgraded them.

---

### Post by wanger123 on 2006-04-08
Thanks guys, I never even realised that I had this prob until I checked. 
Also Hygelac, I have the same prob as you with Konsole

wanger

---

### Post by nykobing on 2006-04-08
Same with konsole here as well.

---

### Post by magnusbb on 2006-04-08
The solution to your Konsole problem can be found in this thread:
[http://www.ubuntuforums.org/showthread.php?t=154417](http://www.ubuntuforums.org/showthread.php?t=154417)

For the short version:
> The problem is solved. The problem is only with the packaging for Breezy - KDE version 3.5.2. The two files missing are "kcm_konsole.la" and "kcm_konsole.so". Without these, I am unable to configure Konsole.

I then looked in the same package for Dapper, and found that the two files were present in this package. When moving these two files to my "usr/lib/kde3" directory, the problem disappeared.

The package for Dapper with the two files can be found here:
[http://www.kubuntu.org/packages/kde352/pool-dapper/kdebase/konsole_3.5.2-0ubuntu1_i386.deb](http://www.kubuntu.org/packages/kde352/pool-dapper/kdebase/konsole_3.5.2-0ubuntu1_i386.deb)

---

### Post by wanger123 on 2006-04-08
Thanks magnusbb, will try ASAP

wanger

---

### Post by Hygelac on 2006-04-08
I did that with the amd64 packages instead of the i386 ones, and it appears to work; so thanks for that. :mrgreen:

---

### Post by Velvet Elvis on 2006-04-08
Same problem here.

Has anyone filed a bug on this?

---

### Post by z-vet on 2006-04-08
Thanks a load for this solution.

---

### Post by tiere on 2006-04-16
Thanks. That worked

---

