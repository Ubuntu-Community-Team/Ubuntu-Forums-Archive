---
title: "How do I make a bootable Vista disc using Ubuntu?"
date: 2010-03-29
forum: General Help
---

### Post by KingNeil on 2010-03-29
Hi. I am on Ubuntu 9.04.

I have a Vista disc which I have slipstreamed some drivers onto. (Basically, you copy them into the "upgrades" or "updates" folder)

I have copied all the files from the Vista disc onto my local Ubuntu drive. I have copied in the new files.

Then, I used Brasero to burn from the local Ubuntu drive to a blank DVD.

So, I checked, and all the files are there.

But when I start up the computer, it does not boot. It boots straight into GRUB, then Ubuntu. Wheras, when I stick in the original Vista disc, it does boot.

How do I get the new disc to boot? It has, surely, exactly the same files as the original....

---

### Post by yetiman64 on 2010-03-29
Hi KingNeil, 
Firstly I'll say my slipstreaming experience is with XP not Vista, done from within XP. It was a manuall (vs. glite) insertion of SP3 (never the less it was successful).

The reason for your lack of booting would most likely be copying the files only doesn't reproduce the original Vista discs boot image. This image has to be extracted with a utility such as Isobuster (a Windows program - which I'm currently using OK under Wine).

When the new disc is to be created, whatever burning program you use must have support for creating bootable discs. Burn the new disc with such a program, ie. burn the files + have the burning program use the original Vista boot image or all you are creating is a data disc with Vistas files on it, hence your lack of a successful boot.

I don't know if what you are attempting is actually possible, but I would be interested to know if this works, so good luck.

BTW I also don't know if Wine supports the .NET framework, but if it does then glite might work under Wine as well. Glite is a far easier way to do slipstreaming in general and can do drivers, updates and service packs, as well as removing Windows components (or a stripped down install).

Nev

---

### Post by KingNeil on 2010-03-30
> **yetiman64 said:**
> Hi KingNeil, 
The reason for your lack of booting would most likely be copying the files only doesn't reproduce the original Vista discs boot image. This image has to be extracted with a utility such as Isobuster (a Windows program - which I'm currently using OK under Wine).


[quote=yetiman64]When the new disc is to be created, whatever burning program you use must have support for creating bootable discs. [/quote]

OK, let me clarify, because I've done something slightly new since my first post.

I use the following to get an ISO from the original Vista disc I bought with my PC:

sudo umount /dev/cdrom
readom dev=/dev/cdrom f=file.iso

This creates an exact copy. Then, I right-click the file.iso, and write to a blank disc. And voila! Perfect. It gives me an exact copy of the original Vista.

However, I am looking to copy my custom drivers that I need into a folder within the Vista disc. This folder is called "upgrades" and the process is called slipstreaming. I have checked that this is the way to do it.

So, I do it by taking file.iso, right-clicking and extracting. Then, I add to the folder, and use the following to convert it back into an ISO:

mkisofs -r -o file.iso /location_of_folder/

Then, I right-click the new ISO and choose, "write to disc".

Now, it DOES boot. However, it says "error on the installation" a little bit into the installation of Vista. This is a new development.

[quote=yetiman64]
Firstly I'll say my slipstreaming experience is with XP not Vista, done from within XP. It was a manuall (vs. glite) insertion of SP3 (never the less it was successful).
[/quote]

Well, how did you do it manually? Copy and paste, like I did?

---

### Post by yetiman64 on 2010-03-30
Good to see you got an exact copy with those commands, can see how your burning method would work now.

Yes manually basically means the way you are doing it, as compared to the Windows program that  I checked out at the time Glite - a gui that does all the alterations needed to show XP or Vista the new inserted service pack and -what you need- details for your drivers added in to the folders, "copy and paste" as you referred to. When doing the process manually you need to edit certain text files with driver information or the installer won't "see" or use the new drivers you've put in.

Sorry I can't be more specific, as been quite a while since I did it, and only rarely use Windows nowdays. Plus AFAIK there are quite a lot of differences between the slipstreaming process for XP and Vista from a technical standpoint.

I've Googled around a bit a can only seem to find references to nlite and vlite, but nothing like the process I used (and you are now attempting).

Its a project that sounds very interesting, but probably would be easier to achieve with either nlite or vlite (both for Windows) under Windows. Possibly with a Virtual Machine install of Win in Virtualbox?.

---

### Post by KingNeil on 2010-03-30
First of all, with Vista, I believe they've set it up so you only need to stick the driver folder straight into the "updates" or "upgrades" folder.

Now, as for vLite or nLite, aren't these only for Service Pack slipstreams? Or, is it possible to slipstream in drivers?

OK, forget that question. Turns out you can slipstream drivers. Thank you anyway. I was thinking all this time that vLite is only for service packs..

---

### Post by yetiman64 on 2010-03-30
> First of all, with Vista, I believe they've set it up so you only need to stick the driver folder straight into the "updates" or "upgrades" folder.I don't really know for Vista, even though I have Vista installed in a dual boot setup, I've never bothered with slipstreaming it, as with broadband connection nowdays have let the auto updates install them.

nlite can do sp's, drivers, updates addins (KB******), and component removal (stripped down installs) for XP and I suspect in Vista as well.

---

### Post by KingNeil on 2010-03-30
> **yetiman64 said:**
> 
nlite can do sp's, drivers, updates addins (KB******), and component removal (stripped down installs) for XP and I suspect in Vista as well.

According to nLite's website, nLite supports Windows 2000, XP x86/x64 and 2003 x86/x64 in all languages.

So, I'll be using vLite.

Thank you for all your help.

ALSO, just to note, for anyone reading this, I noticed vLite 1.2 needs the following:

Runtimes

    * [.NET Framework 2.0 SP1 (x86) | 23.6 MB (Vista already has it)]("http://www.microsoft.com/downloads/details.aspx?FamilyID=79bc3b77-e02c-4ad3-aacf-a7633f706ba5&DisplayLang=en")
    * [.NET Framework 2.0 SP1 (x64) | 46.9 MB (Vista already has it)]("http://www.microsoft.com/downloads/details.aspx?FamilyId=029196ED-04EB-471E-8A99-3C61D19A4C5A&displaylang=en")
    * [Automated Installation Kit (AIK) for Windows Vista SP1 | 1375.9 MB (recommended)]("http://www.microsoft.com/downloads/details.aspx?FamilyId=94BB6E34-D890-4932-81A5-5B50C657DE08&displaylang=en")
    * [URL="http://www.microsoft.com/downloads/details.aspx?familyid=C7D4BC6D-15F3-4284-9123-679830D629F2&displaylang=en"]Windows Automated Installation Kit (AIK) | 992.2 MB (previous WAIK version)
[/URL]

---

