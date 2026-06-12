---
title: "openoffice"
date: 2011-04-29
forum: General Help
---

### Post by renegade600 on 2011-04-29
I upgrade through the software center and found that ubuntu forgot what the concept of upgrading means.  It does not mean uninstall already installed programs and applications - update them yes, uninstall NO!!.  

 what is the best way to get rid of the poor excuse of an office suite libre and reinstall openoffice.    I already tried uninstalling libre and installing openoffice using the software center but it put libre back on.    I even tried downloading the deb from openoffiice but ubunutu keeps say quality issues so it wont install.  

any help would be appreciated - Thanks

---

### Post by piratebill on 2011-04-29
You do realize that libre office ***IS ***open office right?  After Oracle bought OO the devs left and created libre office (which is a fork from the OO source code).  Open office is pretty much a dead project now.

---

### Post by r-senior on 2011-04-29
LibreOffice is based on OpenOffice. Following the acquisition of Sun by Oracle, there were concerns that OpenOffice would cease to be completely open source. So the development has forked, with LibreOffice going one way and OpenOffice going another. They share the same code base.

I'm not sure why you would come to the conclusion that LibreOffice is such a poor relation of OpenOffice? The fork was quite recent and, for the time being at least, LibreOffice is pretty much just a rebranded OpenOffice.

---

### Post by renegade600 on 2011-04-29
> **piratebill said:**
> You do realize that libre office ***IS ***open office right?  After Oracle bought OO the devs left and created libre office (which is a fork from the OO source code).  Open office is pretty much a dead project now.

I know what libre is and where it came from...imo, it is not needed since openoffice has been turned over.  libre does not have all the features that open office has and I need some of those features.  I want openoffice installed on my computer NOT libre and I am asking for help instead of a debate.

---

### Post by 68pontiac on 2011-04-29
[openoffice.org]("openoffice.org") has a link right on the landing page to download. Click the download button and you're off.

---

### Post by renegade600 on 2011-04-29
> **68pontiac said:**
> [openoffice.org]("http://openoffice.org") has a link right on the landing page to download. Click the download button and you're off.

thanks - unfortunately I already tried downloading that one several times - on two different computers and a windows computer, ubuntu kept giving quality errors  and would not install.

---

### Post by RebateFX on 2011-04-29
LibreOffice is NOT OpenOffice.

The fact that LibreOffice is unable to import a csv file is a showstopper for me. No import dialog like openoffice where you can choose the separation character, and when it does open, I end up with a blank spreadsheet. 

I tried to install openoffice from debs and Ubuntu's installer tried it's best to discourage me.

I'm going to see if Gnumeric handles CSVs.

---

### Post by RebateFX on 2011-04-30
Great. Gnumeric doesn't handle it either. Looks like my only option is to go the MS Office 2007 route in order to continue using Ubuntu in the office. :(

---

### Post by z987k on 2011-04-30
> **RebateFX said:**
> Great. Gnumeric doesn't handle it either. Looks like my only option is to go the MS Office 2007 route in order to continue using Ubuntu in the office. :(

Actually Libre does handle csv just fine.  You had me worried for a second, but it opens csv, tsv, whatever and even gives the dialog box before it opens to ask which one you want.... just like OO.

As far as OO from their website, it does in fact install just fine.

---

### Post by jbrefort on 2011-04-30
Gnumeric handles csv and analogs too. wht made you think the contrary?

---

### Post by ubuntu27 on 2011-04-30
> **renegade600 said:**
> ubuntu kept giving quality errors  and would not install.

Quality errors? Follow [this guide]("http://www.webupd8.org/2011/04/how-to-install-deb-files-when-getting.html") for a solution.

---

### Post by apochry on 2011-04-30
> **RebateFX said:**
> LibreOffice is NOT OpenOffice.

The fact that LibreOffice is unable to import a csv file is a showstopper for me. No import dialog like openoffice where you can choose the separation character, and when it does open, I end up with a blank spreadsheet. 

I tried to install openoffice from debs and Ubuntu's installer tried it's best to discourage me.

I'm going to see if Gnumeric handles CSVs.

[CENTER] [img]http://imgur.com/Qa4JB.png[/img] 

 [img]http://imgur.com/dTAnX.png[/img][/CENTER]

---

### Post by parsim on 2011-05-02
> **RebateFX said:**
> LibreOffice is NOT OpenOffice.

Yes, it's a little frustrating that whenever someone asks, "How can I install OpenOffice instead of LibreOffice?" they get told, "Just install LibreOffice."

I don't want LibreOffice because of the [Page Preview Relocation bug](http://bugs.freedesktop.org/show_bug.cgi?id=35638), which is NOT present in the same version of OpenOffice.

> **68pontiac said:**
> [openoffice.org]("openoffice.org") has a link right on the landing page to download. Click the download button and you're off.
I tried that and got an archive with 48 DEB packages inside. The Ubuntu Software Center warned about low quality packages and kept crashing, so I used GDebi. After a whole lot of trial and error to figure out which packages depend on what (and thus need to be installed first), I get:
```
$ /opt/ooo-dev3/program/swriter 
Missing vcl resource. This indicates that files vital to localization are missing. You might have a corrupt installation.
```

---

