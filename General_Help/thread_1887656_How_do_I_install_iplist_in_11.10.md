---
title: "How do I install iplist in 11.10"
date: 2011-11-27
forum: General Help
---

### Post by radiors on 2011-11-27
I am trying to install iplist (aka IpBlock) in 11.10. I have searched just about everywhere I can think of but cannot find the correct repository for Ocelot.  

Please help!

---

### Post by oldtimer7777 on 2011-11-27
> **radiors said:**
> I am trying to install iplist (aka IpBlock) in 11.10. I have searched just about everywhere I can think of but cannot find the correct repository for Ocelot.  

Please help!

Don't use that __ program. Use moblock mobloquer instead.  Iplist is a pain.

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

It is on this list. Install it from the PPA..

---

### Post by radiors on 2011-11-27
Okay. Tried this but I was unable to get moblock either.  The name has evidently been changed to pgl (Peer Guardian Linux, I guess).  However, I did get pgl and managed to configure it so it doesn't block my whole Internet access. Don't know if there is a GUI for this yet.

Thanks.

---

### Post by oldtimer7777 on 2011-11-27
> **radiors said:**
> Okay. Tried this but I was unable to get moblock either.  The name has evidently been changed to pgl (Peer Guardian Linux, I guess).  However, I did get pgl and managed to configure it so it doesn't block my whole Internet access. Don't know if there is a GUI for this yet.

Thanks.

Moblock has more comprehensive lists.  The one you are using now is insufficient.
You not blocking the latest IPs with it and you are completely vulnerable, just so you know that.  Moblock works if you install it from the PPA on the above link.  If you cut and paste the PPA into terminal, what does it say? It can't find Moblock repo?  

Moblock is really the only one that has all of the IPs you need to block.  Just saying

---

### Post by jre on 2011-11-28
pgl is the successor of moblock/blockcontrol/mobloquer. It allows to use the same set of blocklists. So (on current systems) definitely use pgl.
The GUI is called pgl-gui (separate package from the same (my) repository).

greets

---

### Post by radiors on 2011-11-28
Package mobloquer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  pgl-gui

Package blockcontrol is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  pglcmd

Package moblock is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  pgld

E: Package 'moblock' has no installation candidate
E: Package 'blockcontrol' has no installation candidate
E: Package 'mobloquer' has no installation candidate

---

### Post by williamdemeo on 2011-11-29
[Edit] Please ignore my post below.  I found the latest iplist package and it seems to work fine with ubuntu 11.10.  It's here: 
[http://sourceforge.net/projects/iplist/files/iplist/0.29/](http://sourceforge.net/projects/iplist/files/iplist/0.29/)

[Previous post]
I used to use iplist in 11.04 and it worked great.  When I used deluge I could see that iplist was successfully blocking all US ip address, and when one was getting through, I could just add it manually to the ip lists loaded into ipblock.  

Now I have 11.10, so I took your advice and installed pgl.  It seems to work in the sense that it blocks many ip addresses, however, even after I have loaded the US ip lists I was using with ipblock, pgl still lets through tons of US ip addresses when I'm using deluge.

So, I would really love to go back to iplist.  Has anyone used it successfully with 11.10?

Thanks for any advice!

(P.S. I'm having so many problems with 11.10 as compared to 11.04, I'm about ready to downgrade... ):

---

### Post by radiors on 2011-11-29
[I]I found the latest iplist package and it seems to work fine with ubuntu 11.10. It's here:
[http://sourceforge.net/projects/ipli...s/iplist/0.29/](http://sourceforge.net/projects/ipli...s/iplist/0.29/)[/I]
[/I]
Hi Williamdemeo:  I found this too, but I wasn't sure how to install it and didn't want to go through the trouble unless I knew it worked.  How did you install it?

rrs
rrs

---

