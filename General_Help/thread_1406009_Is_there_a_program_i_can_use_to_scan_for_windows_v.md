---
title: "Is there a program i can use to scan for windows virus in linux?"
date: 2010-02-13
forum: General Help
---

### Post by Jameshardy88 on 2010-02-13
Is there a program i can use to scan for windows virus in linux?

my friends windows pc was hit by a virus that totally ruined his pc, we were able to save some of his files, is there any way i can scan them on my ubuntu computer to check for windows viruses?

---

### Post by bruno9779 on 2010-02-13
Yes, all virus scanners for linux, are actually used only to scan for windows viruses.

They are mainly used in linux servers that redirect windows mail and for cases like yours.

ClamAV (properly updated) should do the trick

---

### Post by Jameshardy88 on 2010-02-13
Thankyou very much =)

---

### Post by colobix on 2010-02-13
SInce you already have windows installed on your computer, you probably have an AV on that windows as well.
I suggest you check the Wine program list to see if there are any AV programmes that can be run by wine.
Here: [http://appdb.winehq.org/](http://appdb.winehq.org/)
And have you tested your AV program in ubuntu yet?
But I don't think there's any professional AV programs for linux but some email scanners.

---

### Post by jrusso2 on 2010-02-13
Use clamav if you want a lot of false positives.  Use a free version of a commercial virus scan if you want something good like avast or bitdefender.

---

### Post by colobix on 2010-02-13
> **jrusso2 said:**
> Use clamav if you want a lot of false positives.  Use a free version of a commercial virus scan if you want something good like avast or bitdefender.

Hmm, I use the full version of avast but Wine doesn't support it, so that can't be right.
But try the free version of SUPERAntiSpyware. It works like a charm with Wine.
You can download it from download.com.
I Know it's called anti spyware but it takes trojans and shït like that as well.

---

### Post by kio_http on 2010-02-13
Microsoft Security Essentials installed on Windows not only detects viruses but also fixes harm done.

---

### Post by Alexanderypema on 2010-02-17
I have a debian based file server at home, which hosts files for several windows PCs (Files including torrents!), and i was wondering if there's any good virusscanner that takes out the virusses in the torrent files (Included in rar archives, zips, etc) without completely deleting the archives.
 
I'm SURE there's virusses on my file server (As i get warnings with my windows box) but clamAV doesn't give me anything (clamscan -i -r --detect-pua), except for a lot of false positives from my joomla web directory.
The box is purely console based, thus the solution must be console based aswell.. 
 
Anyone suggestions?

---

### Post by intermentals on 2010-02-17
**Avast**


 [I]wget [http://files.avast.com/files/linux/avast4workstation_1.3.0-2_i386.deb](http://files.avast.com/files/linux/avast4workstation_1.3.0-2_i386.deb) && sudo dpkg -i avast4workstation_1.3.0-2_i386.deb
[/I]
Access it through Accessories &#8594;  avast! Antivirus .

---

### Post by Alexanderypema on 2010-02-17
> **intermentals said:**
> **Avast**
 
 
*wget [http://files.avast.com/files/linux/avast4workstation_1.3.0-2_i386.deb](http://files.avast.com/files/linux/avast4workstation_1.3.0-2_i386.deb) && sudo dpkg -i avast4workstation_1.3.0-2_i386.deb*
 
Access it through Accessories &#8594; avast! Antivirus .
 
Is it console usuable? (i'll try, thanks!)
**EDIT:** It works fine in the console, though it needs a registration key and it works only for 1 year according to the website.
Anyway, scanning now, let's hope i can get trojans out, also, it seems to scan within archives! yay.
 
I'll bring out an update about this here later (my god it's hot and lacks oxygen here, brain = bluh)

---

### Post by Mark Phelps on 2010-02-17
Viruses are far more likely to attach themselves to system files (or their substitutes) than to data files.  They also have a nasty habit of hiding inside "user" folders in MS Windows -- folders you're not likely to find if you're just copying over data files.  So, if the files you copied over are data files, you're most probably wasting your time scanning them.

If you friend has a machine that can boot from CD, do a Google search for free Antivirus scanners for Windows. Look for those that offer disk images downloads (.ISO files) that you can burn to CD and then boot OUTSIDE of MS Windows to run an AV scan.

Last time I checked, both Avira and Kaspersky were offering free downloads.  There may be others, now.

---

### Post by dcstar on 2010-02-17
> **bruno9779 said:**
> Yes, all virus scanners for linux, are actually used only to scan for windows viruses.

They are mainly used in linux servers that redirect windows mail and for cases like yours.

ClamAV (properly updated) should do the trick

ClamAV will tell you of e-mails with bogus links and the like, which has nothing whatsoever to do what platform you are running.

I scan all of my incoming Evolution e-mails with clam, and apart from the notifications of the Windows viri that get past my ISP I am warned about all the bogus links that are in them.

If you don't at least do that on your system then you deserve what you get whenever you click one of these links.........

---

