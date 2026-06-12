---
title: "Quanta vs. SMB"
date: 2006-06-16
forum: General Help
---

### Post by FilipeAC on 2006-06-16
After installing a fresh and new copy of Ubuntu 6.06, I installed Quanta for web development... The thing is Quanta wouldn't work with smb protocol... When I typed 'smb:/' or 'smb:/computer/sharedfolder/' on the location bar, it displayed an error message (don't remeber what message, 'Bad address' or something).

So after trying a couple of times and reinstalled Ubuntu another couple of times, I installed the whole kubuntu package (please note that I already had Ubuntu running and installed kubuntu through apt) and it worked fine with Quanta right after it... So I guess Quanta needs a kde package that is listed neither on its dependences not on its recommendations.

Anyone knows which package should I install for Quanta to recognize smb protocol without having to install the whole kubuntu?

Thanks in advance.

P.S.: I know that I can mount smb, but there're lots of shared folders and it's always changing, so it'd be a pain to mount them all and keep track of all the changes. ;)

---

### Post by jak on 2006-06-16
samba (or smbclient..) should be all you need. if it doesn't recognise SMB paths after installing the samba client then it's probably not been catered for in the programming. it's probably a good idea to file a bug, or request that feature on the Quanta website.

---

### Post by FilipeAC on 2006-06-16
I forgot to mention I tried that before installing kubuntu-desktop, sorry.

But anyway that didn't help either (samba or smbcliente). As I said, it only started working after installing kubuntu-desktop...
So the answer lies in some unknown kde package and not in Quanta itself, probably.

I just want to know that because I don't wanna download 400MB just for Quanta to work fine next time. :) 

Thanks anyway, jak.

---

### Post by lefthand on 2007-02-25
I installed the package 'smb4k' and that did the trick for me. It installed a few other packages with it, 50 some MB. It's a lot for one small feature, but way better than 400mb.

---

