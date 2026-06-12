---
title: "Open Office 3.4 won't launch: 12.04"
date: 2012-08-04
forum: General Help
---

### Post by Bucky Ball on 2012-08-04
Hi all,

As the title suggests. Click any OO component and nothing happens. Can't launch Office, Writer, Draw; nothing. 

Was thinking Java but then checked system requirements on the OO site and tells me for Linux I need 'glibc2 version 2.11.1 or higher', which I can't find anywhere to install (and is obviously not installed).

This is a fresh install of 12.04 LTS (less than 24 hours) and I installed the OO repository:

[http://launchpad.net/upubuntu.com/office/ubuntu](http://launchpad.net/upubuntu.com/office/ubuntu) precise

Any ideas??? All seemed to install okay but when I issue:

```
ooffice -writer
```... still nothing. Try:

```
soffice -writer
```Ditto.

---

### Post by Bucky Ball on 2012-08-04
Yea, weird stuff happening. I checked Synaptics and Open Office was installed but none of the components or .base! Hmm. So I installed the ones I use - writer, draw, impress - but still the same. When I click them they don't launch. Nothing happens, nor from a terminal.

Here's the strange bit; I now have Libreoffice Base, Draw, and Writer in my Apps>Office menu! I definitely did not install them, though I did see them in Synaptics (and made a point to install the ones from the Office Suite). Are OO and LibreO amalgamating??? Are they the same?

This is odd. 10.04 crashed and burned for no reason I could detect. I install 12.04 and have had nothing but crash reports. Getting there though and once this is sorted almost out of the woods ... I have thought of hardware but Win7 shows no signs. 

;)

PS: Naturally, 'soffice -writer' now launches Libreoffice writer, 'ooffice -writer' still does nothing.

---

### Post by claracc on 2012-08-05
I would try the following:

Remove libreoffice
Remove openoffice

I have heard that they cannot be installed at the same time.

Then, I would try to install openoffice 3.4 through adding the corresponding repository ppa: [http://www.upubuntu.com/2012/05/how-to-install-apache-openoffice-34-via.html](http://www.upubuntu.com/2012/05/how-to-install-apache-openoffice-34-via.html)

---

### Post by vasa1 on 2012-08-05
> **claracc said:**
> I would try the following:

Remove libreoffice
Remove openoffice

I have heard that they cannot be installed at the same time.

Then, I would try to install openoffice 3.4 through adding the corresponding repository ppa: [http://www.upubuntu.com/2012/05/how-to-install-apache-openoffice-34-via.html](http://www.upubuntu.com/2012/05/how-to-install-apache-openoffice-34-via.html)

I've seen this upubuntu.com being mentioned a bit. Anyone know if it is related in any way to Canonical? The impression I get is that it isn't.

Okay, it's a blog.

---

### Post by Bucky Ball on 2012-08-05
Hmm, this is weird. I think I did use that repository originally but have removed Libreoffice and Open Office and all components. I then removed the repository and restarted. There's still all Open Office packages in Synaptics so I installed openoffice.org-writer, and this is the strange part: It installed Libreoffice Writer!

What do people make of that??? I head back to Synaptics and tells me, yes, I installed Openoffice Writer. I check and the whole Libreoffice is now installed again. I mark Libreoffice Writer for removal and it tells me I am about to remove Open Office Writer!!

Can't make much sense of this. How do I remove everything Office? I thought I had but it's back.

PS: Doesn't run from a terminal, either. Same. Why is this so hard? I can't believe I'm such a dunderhead I can't get this happening but perhaps that's self deception ... If I was a first time user I would have given up on Ubuntu well before now; this is just one of 12.04's problems (for me at least). Wish I'd have stuck with 10.04 but that self-combusted ... Better save that for the Testimonials and Experiences sub-forum!

---

### Post by Bucky Ball on 2012-08-06
Okay. Killed everything Libreoffice and Openoffice. Nothing left. Installed Openoffice. All good, even have the entries back in the apps menu. BUT, when I click on Openoffice Writer the machine whirrs as though it is opening it but nothing ever happens. The whirring stops.

At least I've gotten rid of the Libreoffice conflict but ... I would just use Libreoffice but don't like being forced to and it misses one obscure feature. I need to get back to work so going to ditch 12.04 for the moment (two days of figuring out problems) and go back to the obsolete 10.10 to finish what I have to. No time to twiddle with this for the moment. Pity ...

Thanks for the input ... I'll get back to it. ;)

---

### Post by Bucky Ball on 2012-08-06
Hi all,

Nightmarish waste of time. I read somewhere that development on Openoffice has largely stalled so I would advise those switching to 12.04 to stick with what you got: Libreoffice. I reinstalled that and works immediately and is basically ... exactly the same. I'm wondering why there are two different projects but probably a long story ...

I well, live and learn. Back to what I'm supposed to be doing ... ;)

(Issue resolved rather than solved ...)

---

### Post by Hagar Delest on 2012-08-08
Better install AOO with the official packages, see: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68) This way, you can also install LibO so that it runs in parallel.

No problem with AOO 3.4.0 for me on 12.04 since its release in May...
You may have to [reset your OpenOffice user profile](http://user.services.openoffice.org/en/forum/viewtopic.php?p=58403#p58403). Sometimes old configuration files can cause troubles.

---

### Post by Bucky Ball on 2012-08-08
> **Hagar Delest said:**
> Better install AOO with the official packages, see: [[Ubuntu] Installing OOo on Debian and Co.]("http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68") This way, you can also install LibO so that it runs in parallel.

No problem with AOO 3.4.0 for me on 12.04 since its release in May...
You may have to [reset your OpenOffice user profile]("http://user.services.openoffice.org/en/forum/viewtopic.php?p=58403#p58403"). Sometimes old configuration files can cause troubles.

Thanks. Done all that previously to no avail. Happy with Libreoffice and don't have anymore time to screw around with this right now. Cheers. ;)

---

### Post by HippieDave on 2013-01-29
Many people seem happy with Libreoffice as an alternative to openoffice, but some of us NEED open office!  Libre freezes when I try to open up archived Word docs,. which I often need to access for business.  OO was perfect! well, useful at least.

I've tried all the hints Ive found...purged Loffice and installed the correct ver. of OO via the sudo line commands.....nada./ Anyone have any new sources (since last fall?) I'll take either 12.04 or 12.10 compatablity right now as I have both loaded on different drives.

---

### Post by Bucky Ball on 2013-01-29
> **HippieDave said:**
> Many people seem happy with Libreoffice as an alternative to openoffice, but some of us NEED open office!  Libre freezes when I try to open up archived Word docs,. which I often need to access for business.  OO was perfect! well, useful at least.

I've tried all the hints Ive found...purged Loffice and installed the correct ver. of OO via the sudo line commands.....nada./ Anyone have any new sources (since last fall?) I'll take either 12.04 or 12.10 compatablity right now as I have both loaded on different drives.

You would be much better to start a new thread rather than jumping in here. This has been inactive for six months and you will improve your chances of getting help. Good luck.

---

### Post by Hagar Delest on 2013-01-30
What's wrong with the tutorial on the AOO forum?
What went wrong? What error message?

---

### Post by Bucky Ball on 2013-01-30
[B][I]Thread Closed
[/I][/B]
This was resolved for the OP (myself) six months ago. For any further issues, please post a new thread with a descriptive title in the appropriate section. Thanks.

---

