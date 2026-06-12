---
title: "Card in CAC Card not recognized in Firefox"
date: 2010-07-08
forum: General Help
---

### Post by tallmtt on 2010-07-08
Hi,

I have a Sun Microsystems SCR3310 CAC card reader.

It has worked in previous distributions (Arch) and versions of Ubuntu.  I have only recently tried to install it in Lucid.

I followed the following instructions: 
  [https://help.ubuntu.com/community/CommonAccessCard](https://help.ubuntu.com/community/CommonAccessCard)

I verified pcsc is running with "ps -A | grep pcsc"

I have restarted it anyways just to make sure :)

Running pcsc_scan gives:
  Reader 0: SCM SCR 3310 00 00
  Card state: Card inserted,

As well as correctly identifying the card as:
  	DoD CAC card issued Jan 14, 2010

In Firefox, Edit -> Preferences -> Advanced -> Encryption -> Security Devices shows the CAC Reader with the correct lib file but Status says "Not Present"

The only changes from when this card reader worked before is running Lucid 32 bit and that I got a new CAC card (the card works at work btw)

This is the card potentially mentioned here in the 2nd to last comment by PhillB:
[http://ubuntuforums.org/archive/index.php/t-1221961.html](http://ubuntuforums.org/archive/index.php/t-1221961.html)

I worry that the new CAC card is the issue.  I switched from the previous "white" CAC's to the newer version.  The gold area may be slightly different.  

I don't understand why pcsc_scan can tell the card is inserted but firefox cannot.  This sounds like a firefox issue but where else can I test it?

Any ideas?  How could I debug this?

---

### Post by gordintoronto on 2010-07-08
Actually, it's an SCM Microsystems card reader.

But I don't understand what the issue is.

---

### Post by tallmtt on 2010-07-09
Ok - figured it out - or rather, re-read the documentation.

On this site: [https://help.ubuntu.com/community/CommonAccessCard](https://help.ubuntu.com/community/CommonAccessCard) there is a sentence about the "new" CAC cards - one's labeled as 144 K

The statement is regarding coolkey not working in Lucid - which I think is false but the second half of the statement says "and/or with 144K cards"

You can tell what kind of card you have by looking at the back of it.  It will have "144" among other in small letters above the magnetic stripe on the back of the card.

It just so happens that the solution posted works, though I had to find the library file.

Go to this site: [https://software.forge.mil/sf/frs/do/viewRelease/projects.community_cac/](https://software.forge.mil/sf/frs/do/viewRelease/projects.community_cac/) and download the most recent .deb file there.

Install it along with pcscd and pcsc-tools and the "new" CAC will work.

To clarify, my problem was essentially firefox could not obtain my personal certificates off of my CAC card using either coolkey or opensc (though opensc allowed me to login to my CAC, but still no personal certificates)

Hope that clears up the mud - will change this to solved.

---

### Post by Boondock5 on 2010-10-17
Does anyone have a copy of this add on?
[https://software.forge.mil/sf/frs/do/viewRelease/projects.community_cac/](https://software.forge.mil/sf/frs/do/viewRelease/projects.community_cac/)

The link is dead, or atleast I can't get there from here. I really need to get my CAC working.

Thanks Matt

---

### Post by rochaud on 2011-05-19
The CACKey community page can be found at: [https://software.forge.mil/sf/go/projects.community_cac/frs.cackey](https://software.forge.mil/sf/go/projects.community_cac/frs.cackey).
 
Hope this helps!

---

### Post by addux on 2011-09-01
> 
Re: Card in CAC Card not recognized in Firefox
The CACKey community page can be found at: [https://software.forge.mil/sf/go/pro...cac/frs.cackey](https://software.forge.mil/sf/go/pro...cac/frs.cackey).

Hope this helps!

This would help, however you need a CAC to use this site. From [https://help.ubuntu.com/community/CommonAccessCard](https://help.ubuntu.com/community/CommonAccessCard) there is a link and a tutorial how to fix the issue with the newer 144k cards.  I got this to work on 32 bit Maverik and amd 64 bit.  The ubuntu link pretty much has everything for you except for the firmware.

---

### Post by perro68 on 2012-02-16
will try this tomorrow

recieved new cac card ....now nothing works

---

