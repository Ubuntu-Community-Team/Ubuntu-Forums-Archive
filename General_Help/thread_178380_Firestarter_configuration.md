---
title: "Firestarter configuration"
date: 2006-05-17
forum: General Help
---

### Post by kriding on 2006-05-17
I have installed firestarter, however, whenever I have it running I cannot access my network.

The network consists of two machines, Mine (Ubuntu) and my girlfriends (Windows XP), without the firewall, no problems at all..with it...nothing, although both machines can still access the internet via the router.

My network is a powerline network.

Any suggestions on what I should check? I have gone through the preferences tab and have tried everything, even setting up the policies to allow access to the server, and now I'm outta ideas.](*,) 

Cheers

Kev

---

### Post by drpaul on 2006-05-17
You need to set up some policies to allow access from the other machine.

For example, I have the following Inbound traffic allowed in Firestarter

192.168.2.1/24

which means anything with a 192.168.2 address [my home network]

Also have Samba service allowed for the two machines on my network.

HTH

Paul

---

### Post by kriding on 2006-05-17
thanks for the reply, all is working now:p

---

### Post by Malac on 2006-05-18
I'm not sure where to post this as it's got me right confused.

I finally got my USB Modem working and connected to the internet and can now network between my Ubuntu box and my girlfriends XP box.

:-? I set up the Ubuntu box as gateway to the internet and fired up the XP's browser.
It would connect to [www.yell.com](www.yell.com), [www.dogpile.com](www.dogpile.com) but not to [www.google.co.uk](www.google.co.uk). :-?

Thought it might be the .co.uk extension but [www.bbc.co.uk](www.bbc.co.uk) worked fine.
[www.google.co.uk](www.google.co.uk) was definitely up as on the Ubuntu machine it just clicked straight there.

It just seems completely random to me.

Anyone got any ideas?

---

### Post by Malac on 2006-05-18
Forgot to mention running Firestarter with ICS enabled.
Ubuntu box and XP box on fixed I.P. addresses.

---

### Post by AndyCooll on 2006-05-18
[QUOTE=Malac]Forgot to mention running Firestarter with ICS enabled.
Ubuntu box and XP box on fixed I.P. addresses.[/QUOTE]

A local (to me) Linux user! Yey :D  

Are you able to ping a Google address?

:cool:

---

### Post by Malac on 2006-05-18
Hi AndyCooll,

Thanks for reply.

Problem is now fixed it seemed it was just a DNS foul up. i.e. I wasn't getting any DNS at all but XP must have cached the I.P.'s for the ones I could get to.

Anyway all up and running. Just in time for Dapper then start again.:)

=D>Aw Stockport, Town of my Birth.=D>

---

