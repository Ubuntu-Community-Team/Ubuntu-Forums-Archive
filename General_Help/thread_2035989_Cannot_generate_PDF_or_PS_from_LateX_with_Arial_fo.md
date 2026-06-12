---
title: "Cannot generate PDF or PS from LateX with Arial font"
date: 2012-07-31
forum: General Help
---

### Post by lenveen on 2012-07-31
Recently I ran 
sudo getnonfreefonts -a
in order to install Arial for use with Latex. At the end of the installations it said
that running updmap-sys failed. I decided to install Arial in the global texmf ( /usr/share/texmf/ )directory, following the instructions on
[http://www.ctan.org/tex-archive/fonts/urw/arial/](http://www.ctan.org/tex-archive/fonts/urw/arial/)
then I ran 
sudo updmap-sys
and tried again. Still, LateX runs fine and locates uarial.sty and t1ua1.fd, xdvi displays the document correctly, but dvips and dvipdfm crash with
mktexpk: don't know how to create bitmap font for ua1ri8r.
kpathsea: Appending font creation commands to missfont.log.

I went through several forums and tried the proposed solutions. In particular, I added a line
Map ua1.map
to /etc/texmf/updmap.d/00updmap.cfg
then ran update-updmap and updmap-sys as root. In the output of updmap-sys, I now see 
updmap: using map file `/usr/local/share/texmf/fonts/map/dvips/ua1/ua1.map'
but still dvips and dvipdfm crash with the same message. In /var/lib/texmf/fonts/map/dvipdfm/updmap/dvipdfm.map I see a line
ua1ri8r 8r ua1ri8a
so it seems that some information about the relevant font is passed to dvipdfm.

Could it be the TexLive is configured correctly but something goes wrong with mktexpk? 

I use a pretty much fresh install of Ubuntu 12.04 and a 32-bit machine.
Any help is very welcome!

---

