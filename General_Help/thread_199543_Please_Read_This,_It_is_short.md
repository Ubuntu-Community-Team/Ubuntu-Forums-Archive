---
title: "Please Read This, It is short"
date: 2006-06-18
forum: General Help
---

### Post by Drifter on 2006-06-18
I crossover office worth paying for, I need something to run Quicken with.

---

### Post by digimars on 2006-06-18
Have you tried Wine?  The guys who work for Crossover Office are pretty good at contributing code back to the Wine project.

---

### Post by Fred Doolie on 2006-06-18
Must it be Quicken? There are many very fine free Linux applications (Open Office  and NVU come to mind) that are somewhere between 90-120% (yes, I do mean 120%) as good as commercial Windoze software. Many of them (like O.O.) can read/write the official formats of the commercial applications so you don't lose compatabilty. So MUST it be Quicken? Maybe there is a free Linux application that is like Quicken and can read/write Quicken files.

What *IS* Quicken? Sounds like a hybred cross between quail and chicken.
Remember "Beefalos"? Funny looking animals. So are Ligers and Tigrons for that matter.

If you must run Winslows software, do you still have your Winblows install CDs? You could run VMWare Server (it's free) and install Windows and Qucken inside a virtual computer inside your Ubuntu. That way you can run Windows stuff inside a "real" Windows System while using Linux.
 
Just a thought but my two cents is look for a Ubuntu Linux Quicken-like app and forget Windoze if possible.

---

### Post by digimars on 2006-06-18
There is GnuCash, but I'm not sure if it supports Quicken files.  I did see something on the main page about QIF files, and if that's the file format that Quicken uses, it's worth a shot.

---

### Post by Drifter on 2006-06-19
I have tried gnucash but I can't get it to read or take my quicken files, must be a compatibilit issue between the two.  I will use a linux program if I can find one that will let me transfer my quicken files to it.

---

### Post by aysiu on 2006-06-19
The description for *gnucash* in Synaptic reads: > **A personal finance tracking program**
Gnucash can track finances in multiple accounts, keeping running
and reconciled balances. It has an X based graphical user interface,
double entry, a hierarchy of accounts, expense accounts (categories),
and _can import Quicken QIF files_ and OFX files. The description for *kymymoney2* reads: > **Personal finance manager for KDE**
KMyMoney2 is specifically aimed at the typical home user at present. The
current version, provides the basis for manipulating accounts that contain
transactions. Each account belongs to an institution and can be reconciled to
balance your transactions.

_Quicken QIF import and export is supported_ within accounts so KMyMoney2 can
read files exported from other programs and when downloaded from online
banking institutions.

KMyMoney2 is still under development, so a lot of cool features are yet to
come. It's quite usable already, nevertheless. **Edit**: On a lark, I installed Gnucash and ran it. I don't have any Quicken files, as I've never used Quicken, but the first thing I got when I ran it was a little dialogue asking if I wanted to import Quicken files. Later, there was a little "tip of the day" that told me how to import Quicken files.

Now is that you didn't know how to import Quicken files, or that you tried to import them and the import failed?

**Edit again**: > I have tried gnucash but I can't get it to read or take my quicken files I guess the import failed. Maybe it was an older version of Gnucash. Can we assume you tried Gnucash in Dapper, as opposed to Breezy? Also, have you given KMyMoney2 a try?

---

### Post by Drifter on 2006-06-19
I have Dapper, I tried to import quicken files but failed, It is my fault I just.  I have not tried Kmymoney yet, I do like gnucash if I could get my qfiles to import, I will try again, let u know, thanks.

---

### Post by aysiu on 2006-06-19
Why is it your fault? I don't understand that remark.

Well, do try KMyMoney2. Let us know how it goes.

---

### Post by ltmon on 2006-06-19
We love you using Linux native programs :) But if it does not work out you can run quicken with wine.

The following link gives the best information:

[http://appdb.winehq.org/appview.php?appId=107](http://appdb.winehq.org/appview.php?appId=107)

---

### Post by Drifter on 2006-06-19
It is my fault because I don't know yet how to use cd drives, like mount and unmount etc.  If they give an error or what ever I don't know enough to know what it means yet.

---

### Post by aysiu on 2006-06-19
So the Quicken files are on a CD?

---

### Post by Drifter on 2006-06-19
when I tried to import my quicken file from my backup cd it said it seens to not be a QIF file, is this because I have quicken 2002 maybe.  This is in gnucash I Just installed it.

---

### Post by aysiu on 2006-06-19
You know, honestly, I don't know much about Quicken or Gnucash or QIF or different versions. I'm sorry. Maybe someone else who *does* use Gnucash can give you some tips on the import.

Have you tried KMyMoney2, though?

---

### Post by cjm5229 on 2006-06-19
Hi, I use KMyMoney2, I transfered my files from Microsoft Money  to it as QIF  files. You need to get into Quicken and Export your files into a QIF file first. Then put that file on your desktop and Import it to either Gnucash or KMyMoney. You should find Import and Export commands in "file" in both Apps. You can also download your bank info as a QIF file and import that into KMyMoney if you wish. I tried both Gnucash and KMyMoney and KMyMoney seemed a lot easier to use, but then I'm just balanceing my checkbook. Try both, see which suites you better.:D Good Luck.

---

### Post by Drifter on 2006-06-19
I just can't seem to get kmymoney2 or gnucash to put my qif file into ot it correctly.  I used export and import, gnucash put it in for me but the amounts were all wrong, the account was always in the red or - .  Kmymoney I could not get it to put the info in from the import disk.

---

### Post by forrestcupp on 2006-08-24
> **Drifter said:**
> I just can't seem to get kmymoney2 or gnucash to put my qif file into ot it correctly.  I used export and import, gnucash put it in for me but the amounts were all wrong, the account was always in the red or - .  Kmymoney I could not get it to put the info in from the import disk.

The reason for this is that it only imports the transactions for the current year.  I don't know if that is a problem with gnucash or with exporting to a qif.  So the problem is that it doesn't import the balance you had at the beginning of the year.  You'll have to figure out what your balance was, and go back and add a deposit on Jan. 1.  That is what I had to do, and everything was right after that.

My problem now is that I want to go to something other than gnucash (not because I don't like gnucash; I don't want to get into my reasons).  But I can't export my account into something that another program can import.  I have tried using the java program that converts a gnucash xml file to a qif, but it didn't work.  I don't think gnucash exported the xml file correctly.  Anyone have any suggestions?

---

