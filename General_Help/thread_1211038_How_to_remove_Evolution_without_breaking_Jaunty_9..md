---
title: "How to remove Evolution without breaking Jaunty 9.04"
date: 2009-07-12
forum: General Help
---

### Post by dj-toonz on 2009-07-12
Hi all, is there anyway to remove Evolution without breaking Jaunty 9.04? as I never use Evolution. I use Thunderbird for all my email & news-groups So don't need Evolution on my system taking up hard drive space what I could use for other programs. Cheers

---

### Post by lordofallhearts on 2009-07-12
Hi
Simply go to System > Administeration > Synaptic Package Manager
In quick search enter Evolution. Select the appropriate. All associated programs will automatically be marked. Right click and select 'mark for complete removal'

---

### Post by Copernicus1234 on 2009-07-12
This got me thinking of how Microsoft made msn messenger run automatically on Windows and made it nearly impossible to remove. :) And then how they forced IE 6 to be a part of the operating system so you had no protection from internet links.

You never get tired of the freedom of Ubuntu.

---

### Post by dj-toonz on 2009-07-12
Thanks for that. I'm getting lost now as there's loads of conflicting applications what Evolution needs :( I've marked Evolution to be removed & still loads left in i.e Evolution-webcal but mark that & that ones going to remove other things aswell like ubuntu-desktop & other things. is there a safer way to remove Evolution from the system & the other things aswell

---

### Post by lordofallhearts on 2009-07-12
This is strange because it did work for me.

I would suggest you to not remove it. Synaptic is the safest way to remove an app without hurting any other app in anyway.If you do with terminal window, dependent apps are likely to be crashed. You can also not remove by Applications > Add/Remove Programs if not by synaptic.

You can check out this link from forums 
[http://ubuntuforums.org/showthread.php?t=1158042](http://ubuntuforums.org/showthread.php?t=1158042)

I think it will be helpful

---

### Post by ajgreeny on 2009-07-12
You can get rid of most of it, but you should leave **evolution-data-server-common** or you will loose all sorts of necessary utiltiies, even gnome-panel & gnome-applets which you probably need to keep.  If you use ekiga, that will also go with one of the evolution apps, but if you don't use it, no problem.

---

### Post by DeMus on 2009-07-12
> **ajgreeny said:**
> You can get rid of most of it, but you should leave **evolution-data-server-common** or you will loose all sorts of necessary utiltiies, even gnome-panel & gnome-applets which you probably need to keep.  If you use ekiga, that will also go with one of the evolution apps, but if you don't use it, no problem.

So, if I understand you correctly, Ubuntu is the same as Windows: integrating programs into the OS.
Why do they do this? I also don't use Evolution, but Thunderbird instead, and I also would like to get rid of Evolution but I did this once in Hardy and I could start all over again installing the OS.
I always thought Ubuntu (Linux) was better than Windows but in the end it is all the same. Shame on you Ubuntu.

---

### Post by dj-toonz on 2009-07-12
Thanks for that, I'm going to not bother removing it now as even when I select evolution to be removed it says it's going to remove evolution-data-common & all the other bits what people have said not to remove in bold. so don't want to take the chance and break the system as I've got it working like I want. Thanks any way for the advice

---

### Post by jskandhari on 2009-07-12
Hey if you want to delete all the related packages of evolution goto 
Applications>Add/Remove

select all Installed application
and after that deselect the evolution mail and calendar
and it will remove all the related data and evolution itself

---

### Post by ajgreeny on 2009-07-12
The only real problem to remove is evolution-data-server-common, as I said above.  You can get rid of evolution-common and evolution-data-server with no problem. Note the difference!

The question is, why bother?  Ubuntu does not slow down as windows usually does just because you have lots of applications installed, because there is no huge registry file to be read each time you open a program, and therefore there are no redundant entries in that registry either.

---

### Post by VastOne on 2009-07-12
> **DeMus said:**
> So, if I understand you correctly, Ubuntu is the same as Windows: integrating programs into the OS.
Why do they do this? I also don't use Evolution, but Thunderbird instead, and I also would like to get rid of Evolution but I did this once in Hardy and I could start all over again installing the OS.
I always thought Ubuntu (Linux) was better than Windows but in the end it is all the same. Shame on you Ubuntu.

Evolution:

Evolution is the personal information manager (PIM) of _Gnome_. Evolution is the Gnome app you would use to sync with a mobile phone or PDA. Also of note, Evolution is probably the best application for working with an Exchange server at this point.

Featuring:

    * Email (POP, IMAP, Exchange, more)
    * Calendar (local, ical, Exchange)
    * Contacts (local, Exchange)
    * Memos
    * Tasks 

Note Gnome! Definition: Desktop Environment (Not the OS)

Now, if you were looking to convert a Windows user and try to get them to a non Windows environment (like in your tag line), you would want to give them something standard that they are used to. 

Obviously Firefox is the web browser of choice and it is "a part of the OS" (at least from a new user perspective") but it is not the OS

IF you look at he definition of Evolution again, it is exactly what MS Outlook provides for a hefty cost.

So, new user checking out Ubuntu, (not at all jaded yet by the promises of open source) sees Firefox for the first time and a free Outlook replacement that oh by the way imports everything from Outlook and connects to his Exchange server, maybe he is a little bit happy?  If you have ever worked in a corporate environment, these are the things that will promote change, a secure replacement that is license free.  

So home user may not need Evolution, but there is huge need for it and I for one really appreciate the fact that I do not have to install it on a new install for my corporate clients.

So I do not express shame on Ubuntu, I say bravo for this intelligence of thinking of all users.

Ubuntu is not just for the individual user!

---

