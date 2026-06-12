---
title: "Amsn 0.95 and chinese support"
date: 2006-04-08
forum: General Help
---

### Post by fei on 2006-04-08
I'm using Ubuntu 5.10. The problem is amsn 0.95 can't display some of the chinese charaters. And I also used amsn 0.95 on Fedora core 5 and it doesn't has this problem on Fedora. I think it might be the font problem. But not sure what to do extaclly. Can someone help???

Thanks!!!!!

---

### Post by jazzi on 2006-04-09
It's not about the OS,it's about the fundation of the aMSN.
aMSN is a tcl/tk based program,and tcl/tk donesn't surport Asian charaters very well,include the Chinese character.
but you can find some way to resolve the problem from [www.linuxfans.org ]("http://www.linuxfans.org") The program name is aMSN&#20013;&#25991;&#36755;&#20837;&#20276;&#20387;&#12290;but it donesn't work perfectly!

There is another place that maybe  help you:[Tcl/Tk 8.5 for Linux &#30340;&#20013;&#25991;&#36755;&#20837;]("http://spaces.msn.com/nemo2050/")

---

### Post by jazzi on 2006-04-09
[QUOTE=fei] And I also used amsn 0.95 on Fedora core 5 and it doesn't has this problem on Fedora. 
Thanks!!!!![/QUOTE]
Why the problem doesn't come out in Fedore core 5 ???

---

### Post by fei on 2006-04-09
I'm not too sure. The Fedora machine belongs to the lab, and I don't have root access to it. But, I checked the tcl/tk version, which is also the latest version (8.4.9). Can't think of anything else.

---

### Post by fei on 2006-04-09
Thanks for your help. The chinese input (aMSN&#20013;&#25991;&#36755;&#20837;&#20276;&#20387;) is for old amsn versions only. I can't use with amsn 0.95.

I also digged into the amsn forum, and found out that the lateset cvs version supports scim input. I'm too lasy to try the cvs version. Hope a new version will release soon.

---

### Post by jazzi on 2006-04-09
[QUOTE=fei]

I also digged into the amsn forum, and found out that the lateset cvs version supports scim input. .[/QUOTE]

Is that true?so great a news
how about have a try?

---

### Post by fei on 2006-04-10
Well, if you are going to try the CVS verison. Is that possible to make a Ubuntu package, so everyone can use it.  : - )

---

