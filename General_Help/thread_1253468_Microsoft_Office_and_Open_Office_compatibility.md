---
title: "Microsoft Office and Open Office compatibility"
date: 2009-08-30
forum: General Help
---

### Post by rmcellig on 2009-08-30
I was telling my sister in law all about Ubuntu 9.04. She is very interested in trying it out on her new HP work laptop. Her main concern is that if she is doing anything in OpenOffice, it has to be absolutely compatible with her MS Office users.

I would like to hear back from users who use OpenOffice or something similar in their work environment and how successful they are in working with users who rely on MS Office. Compatibility issues etc...

---

### Post by PorkyPie on 2009-08-30
This article I found on the Tech Republic website might help, [http://articles.techrepublic.com.com/5100-10878_11-5083657.html?tag=sc](http://articles.techrepublic.com.com/5100-10878_11-5083657.html?tag=sc) .

To make it more compatible, you can also install Micro$oft fonts, like Arial, Verdana, Comic Sans MS etc. by running these commands in the terminal

Run...
```
sudo apt-get install msttcorefonts
```...to install, then
```
sudo fc-cache -fv
```to clear the fonts cache ( or you could skip this command and log out, then back in)

Hope this helps

---

### Post by jtravnick on 2009-08-30
is there a quick way to check to see what fonts you have installed? I did a search with Synaptic Package Manager and seen I did not have msttcorefonts but would like a CLI way of knowing what all I have

---

### Post by PorkyPie on 2009-08-30
> **jtravnick said:**
> is there a quick way to check to see what fonts you have installed? I did a search with Synaptic Package Manager and seen I did not have msttcorefonts but would like a CLI way of knowing what all I have
  To see what fonts you have installed, you could try open office. Open Writer, and click on the fonts dropdown menu. Then, it will show you the fonts.

Hope it helps

---

### Post by aphirst on 2009-08-30
Also, if you're using GNOME, you can use nautilus to go to fonts:///

---

### Post by PorkyPie on 2009-08-30
> **aphirst said:**
> Also, if you're using GNOME, you can use nautilus to go to fonts:///

> **jtravnick said:**
> is there a quick way to check to see what fonts you have installed? I did a search with Synaptic Package Manager and seen I did not have msttcorefonts but would like a CLI way of knowing what all I have

Or run this in a terminal or by clicking ALT+F2

```
gksu nautilus /usr/share/fonts
```That will show you the fonts. But, don't do any big changes to it.

I've read about fonts:/// , but it doesn't work for me. Oh well. :)

---

### Post by Topsiho on 2009-08-30
She could try and install the Windows version of OpenOffice in Windows first, and try it out.

Just download the version for her language from the OpenOffice site, and then install as usual. Preferably with Java Runtime Environment.

Topsiho

---

### Post by scouser73 on 2009-08-30
> **rmcellig said:**
> I was telling my sister in law all about Ubuntu 9.04. She is very interested in trying it out on her new HP work laptop. Her main concern is that if she is doing anything in OpenOffice, it has to be absolutely compatible with her MS Office users.

I would like to hear back from users who use OpenOffice or something similar in their work environment and how successful they are in working with users who rely on MS Office. Compatibility issues etc...

OpenOffice is an excellent office suite, as well as having the ability to save work in the **.odt** format, data can be saved in the standard Microsoft format; **.doc**/**.xls** but currently not **.docx**, which I believe a current format for saving data in Microsoft.

Your sister should be very happy with using OpenOffice as I know I am.  OpenOffice get's updated regularly and as of Monday 31st August 2009 there will be a new release: 3.1.1.

---

### Post by PorkyPie on 2009-08-30
Your sister could also just install Micro$oft Office on ubuntu, using Wine or CodeWeavers Crossover Office. I would choose wine.

For more information on using Office on Wine, visit this ubuntu help page, [https://help.ubuntu.com/community/Microsoft_Office](https://help.ubuntu.com/community/Microsoft_Office)

---

### Post by Liolikas on 2009-08-30
Kinda not friendly to M$ users way, but MS office 2007 service pack 2 opens odt files. So give them odt and then give them options:
1)Use the latest version of Open office (free download)
2)Use the latest version of Microsoft office (buy)
Also Sun provides MS office plugins for odt:
[http://www.windowsreference.com/ms-office/how-to-open-odt-files-in-microsoft-word-20072003/](http://www.windowsreference.com/ms-office/how-to-open-odt-files-in-microsoft-word-20072003/)

Also Open office can save work in .doc etc. ancient file types, but mistakes may appear as warning says. But this is only possibility to deal with older than 2003 MS office users.

---

### Post by Elisavet on 2009-08-30
Just wanted to add that OpenOffice is an excellent and totally user friendly replacement for MsOffice but if you have documents that contain equations compiled with MathType or EquationEditor, they might end unreadable under OpenOffice.
There is, however, a way to write and edit equations under OO (it's called Math) but you won't be able to see already existing MathType or EquationEditor objects :(
That's my 2 cents for it, but overall OpenOffice is a brilliant Office Suite which uniquelly offers the possibility to write a document and export it quickly as pdf.

---

### Post by JAYCEE1 on 2009-08-30
> **PorkyPie said:**
> This article I found on the Tech Republic website might help, [http://articles.techrepublic.com.com/5100-10878_11-5083657.html?tag=sc](http://articles.techrepublic.com.com/5100-10878_11-5083657.html?tag=sc) .

To make it more compatible, you can also install Micro$oft fonts, like Arial, Verdana, Comic Sans MS etc. by running these commands in the terminal

Run...
```
sudo apt-get install msttcorefonts
```...to install, then
```
sudo fc-cache -fv
```to clear the fonts cache ( or you could skip this command and log out, then back in)

Hope this helps

I'm running 8.04 (Hardy) on an IBM T41. I need TNR or arial for college assignments. I followed these instructions and they worked great. Thanks PP!

---

### Post by PorkyPie on 2009-08-30
> **JAYCEE1 said:**
> I'm running 8.04 (Hardy) on an IBM T41. I need TNR or arial for college assignments. I followed these instructions and they worked great. Thanks PP!

You're very welcome! :)

---

### Post by lswb on 2009-08-30
For word processing documents open office is pretty good at reading and creating MS Word compatible files. (Aruguably better than older Word versions are at reading docs created with newer versions of Word!) BUT, if you use spreadsheets with any non-trivial formulas or macros, expect much trouble!

---

### Post by siemenslee on 2009-12-20
OK, there are many office softwares, we can not just focus on Openoffice! Others' compatibility may be better!!!

---

### Post by judge jankum on 2009-12-20
Will text docs made in MS Office be readable in Open office? Without an xp user going through hell in terminal to make it work? For people to switch from one system to another, you have to be able to make the switch without hell to pay.... I love Ubuntu, but I know many people who'd be lost if they couldn't point, click and go...

---

### Post by Dougie_Fresh on 2009-12-20
> **JAYCEE1 said:**
> I'm running 8.04 (Hardy) on an IBM T41. I need TNR or arial for college assignments. I followed these instructions and they worked great. Thanks PP!

same thanks.. with openoffice and these fonts should i even bother downloading word/excel etc.?

---

### Post by Speckled_Jim on 2009-12-20
It is certainly possible to switch from Office to Open Office (I've done it for my personal use), but I don't think it is possible to exchange documents between the 2 without some risk that important elements will be changed. For example, formatting in Word is not always faithfully retained in OO. With Excel it can be even more of a pain. It's not just formulae that can be changed, simple things like cell high-lighting colours are not always transferred correctly (this may or may not matter, it depends on the significance of the colouring), pivot tables just don't translate and graphs often end up looking fairly poor. None of this is a problem for a one-off switch, assuming a willingness to put the effort in to fix any problems or cosmetic irritations, but could be a total pain if it's necessary to exchange documents with other people who are still using the MS product. For example, Client facing documents that need to have a particular corporate "look & feel" are best done entirely within one office product, so that all the formatting is retained at every edit.

---

### Post by Hagar Delest on 2009-12-21
Pivot tables work with OOo but the number of fields is limited to 8. There is an enhancement request for that.

Basically, if you need to exchange documents with other MS Office users with a good level of reliance, better keep doing it with MS Office. Remember that .doc, xls, ... formats were secret until last year. Import/export filters have been made by reverse engineering. That's why the main point using OOo is the ODF, a true documented ISO file format.

The core issue with MS Office is that MS has to keep its vendor lock-in policy to keep its share market. As long as users will focus on the compatibility with MSO instead of interoperability through the file format, this situation will remain.

Even the standardized ISO version of OOXML (.docx, ...) is not the version supported in MS Office 2007. That was a marketing operation to make the customers believe that MS trusts open formats!

As for the ODF plugin, the Sun version is better than the one delivered in the last service pack from MS.

---

