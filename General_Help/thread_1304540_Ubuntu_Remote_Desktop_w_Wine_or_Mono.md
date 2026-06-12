---
title: "Ubuntu Remote Desktop w/ Wine or Mono"
date: 2009-10-29
forum: General Help
---

### Post by dmcdaniel on 2009-10-29
Hello Everyone,

This is what I need:

Remote desktop w/ TS Gateway support. Currently, nothing on Ubuntu supports this (That I am aware of). 

Does anyone know of anything that will work on Ubuntu or that will work on Wine or Mono?

It is VERY important that I get it to work in Ubuntu/Wine or Mono and tsclient nor rdesktop work. 

Thanks,
dmcdaniel

---

### Post by dmcdaniel on 2009-10-29
Anyone have any ideas? Google search returns nothing. :/

---

### Post by BQAggie2006 on 2009-10-29
Not sure if it's what you're looking for, but check out FreeNX for remote desktop and OpenVPN for gateway access. Or you could try RealVNC's Java VNC Viewer through a web browser.

---

### Post by dmcdaniel on 2009-10-29
Nope. That doesn't help at all. Has to go through the terminal service gateway. They wont enable VPN connectivity.

---

### Post by Lars Noodén on 2009-10-30
Should be able to run your legacy software under WINE.  Installing it and see if it works.  

It looks like it is a web-based front-end and might work under Firefox or Opera?
[http://blogs.techrepublic.com.com/networking/?p=773](http://blogs.techrepublic.com.com/networking/?p=773)

The company that makes the TS, however, does not ever help with interoperability nor does it usually use the normal names for anything so you'll 1) have to cross-map technical terms from two separate, parallel vocabularies to find anything in the search engines, 2) look at sites [not affiliated](http://www.theopensourcerer.com/2009/10/29/how-to-remove-mono-from-ubuntu-9-10-karmic-koala/) with the vendor or its partners.  

If you work with VNC server on the Ubuntu machine, you can share that desktop with people on legacy systems.  I've tested that and it works.  It should be able to share the legacy system with Ubuntu, can you get them to use VNC?

---

### Post by dmcdaniel on 2009-10-30
Sorry but I think you misread. 

I am trying to reach a TS Gateway from a Ubuntu station. rdesktop nore tsclient support the Gateway function that rdp 6.0 supports. They only support RDP 5.0 standards. 

I need to use something in Wine or Mono to do my remote desktop into a  TS Gateway. This gateway is NOT on the same network so we have to use RDP 6. 

Trying to make RDP 6 on wine.

---

### Post by Lars Noodén on 2009-10-31
> **dmcdaniel said:**
> 
I am trying to reach a TS Gateway from a Ubuntu station. rdesktop nore tsclient support the Gateway function that rdp 6.0 supports. They only support RDP 5.0 standards. 
... This gateway is NOT on the same network so we have to use RDP 6. 

Trying to make RDP 6 on wine.

On the surface at least, [rdp](http://wiki.wireshark.org/RDP) looks like the embrace, extend phases of the infamous embrace, extend, extinguish strategy.  If you want out of that, you'll have to find a way to get the MS TS gateway managers to find a middle ground or you'll have to find a way around them completely.  But the nature of RDP and your stated requirement to use RDP 6, constrains your options.  

Ok.  There are ways to properly set up a network gateway, independent of RDP or other high-level protocols, but the managers of the gateway sound unhelpful.  However, they may have provided you with a windows-only client application to use their gateway using RDP 6.  

Have they?

If the answer is yes and if you are asking about WINE, then you are asking about running a Windows program under WINE.  That's what WINE does.  Try installing WINE, then inside WINE, try installing the gateway client that the managers have provided you.  

If that does not work, but you are sure the program does work on Windows, then you can look to WINE-variants Cediga or Crossover.

---

### Post by dmcdaniel on 2009-11-03
Lars Nooden,

Thank you for the information. Sounds like you know exactly what I need. 

Problem: I have installed WINE and RDP6 does not work on it. TBH I can't even get Remote Desktop to install on it properly. Keeps telling me it already has a remote desktop program but I can't seem to find that either. I will look at the crossover platform and see if that will work. 

Thanks,
dmcdaniel

---

### Post by Lars Noodén on 2009-11-05
Can you provide a link to the download page of the specific program you are trying to run?  Include Name, version, system requirements info.  

Once you are inside Wine, you are for all practical purposes running Windows. So might also want to head in to discussions areas for such grey activities:

[WINE forum for Ubuntu](http://ubuntuforums.org/forumdisplay.php?f=313)

[WINE help forum @ winehq](http://www.winehq.org/help/)

---

### Post by dmcdaniel on 2009-11-05
Hello,


This is the link that I am trying to use. 

[http://www.microsoft.com/downloads/details.aspx?FamilyId=26F11F0C-0D18-4306-ABCF-D4F18C8F5DF9&displaylang=en]("http://www.microsoft.com/downloads/details.aspx?FamilyId=26F11F0C-0D18-4306-ABCF-D4F18C8F5DF9&displaylang=en")

---

### Post by Lars Noodén on 2009-11-06
> **dmcdaniel said:**
> Hello,


This is the link that I am trying to use. 

[http://www.microsoft.com/downloads/details.aspx?FamilyId=26F11F0C-0D18-4306-ABCF-D4F18C8F5DF9&displaylang=en]("http://www.microsoft.com/downloads/details.aspx?FamilyId=26F11F0C-0D18-4306-ABCF-D4F18C8F5DF9&displaylang=en")

Thanks.  That's this program, not ubuntu remote desktop:

[INDENT]"[I]Remote Desktop Connection (Terminal Services Client 6.0) for Windows XP (KB925876) 
Brief Description
This version of Remote Desktop Connection (Terminal Services Client 6.0) can be installed on client computers running Windows XP Service Pack 2.[/I]..."[/INDENT]

Unfortunately the paucity of technical information there is a problem.  You might find someone who has run into and solved the same problem you have over on the the [WINE support category](http://ubuntuforums.org/forumdisplay.php?f=313).  

Be sure to include an exact quote of the error message you get when you try to install the "Remote Desktop Connection (Terminal Services Client 6.0) for Windows XP (KB925876)" in WINE.

---

### Post by abbbottt on 2011-08-10
I have been banging my head against the wall for weeks trying to look for any solution to get connected to work network through a damn TS Gateway. In the end I found a solution that I'm not 'idealistically' happy with but am just bloody glad IT FINALLY WORKS.

If you're in a similar position and can live with a small diversion from your FOSS ideals then it's 20 Euros well spent!

[http://itap-mobile.com/desktop/rdp](http://itap-mobile.com/desktop/rdp)

Think this is fairly new...? Hope this helps some of you guys out!

Chris

---

