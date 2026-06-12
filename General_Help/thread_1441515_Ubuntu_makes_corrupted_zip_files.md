---
title: "Ubuntu makes corrupted zip files"
date: 2010-03-28
forum: General Help
---

### Post by acidblue on 2010-03-28
I can make and unzip zip files.
But when i make and then pass on a zip file on to a Windows user 
they can't open the zip file cause it's corrupted.:confused:

I like to use the gerber viewer at circuitpeople.com, but they only 
accept zip files.
So I have to log into Windows to make a zip file and pass it along
to their server.

Whats up with Ubuntu and zip files???
Using x86_64 9.10 Karmic.
Anybody else experience this problem?

---

### Post by Kevinator on 2010-03-28
Never seen this. How exactly are you making the zip files? It might not say much, but can you run the 'file' command on a zip files you've created and post the results?

---

### Post by cjhabs on 2010-03-28
> **acidblue said:**
> I can make and unzip zip files.
But when i make and then pass on a zip file on to a Windows user 
they can't open the zip file cause it's corrupted.:confused:

I like to use the gerber viewer at circuitpeople.com, but they only 
accept zip files.
So I have to log into Windows to make a zip file and pass it along
to their server.

Whats up with Ubuntu and zip files???
Using x86_64 9.10 Karmic.
Anybody else experience this problem?

How big are the zip files? I have seen something similar on Windows for big zip files (database backups), where you have to be very particular with which zip program you use to create the zip files.

---

### Post by acidblue on 2010-03-28
This is the result of "File" command:

Gerber.zip: Zip archive data, at least v2.0 to extract

I simply right click on file and choose "Compress"
Then choose .zip for compression.
I think It's using Xarchiver.

---

### Post by Kevinator on 2010-03-28
Ah, yes. I hadn't noticed that option. I wonder if v2.0 isn't widely supported? I'll investigate a bit more and let you know if I find anything.

---

### Post by Kevinator on 2010-03-29
It looks like the context-menu option uses File Roller (at least on my system). From what I can tell, tihs creates zip files with DEFLATE compression. That's pretty standard, and I think it should work fine with most software. You can double-check my results by running zipinfo on the file. The sixth field should be "defN" for DEFLATE, normal level.

File Roller uses the zip program to create .zip files, and that claims to be compatible with PKZIP. I don't know why this would not be working.

---

### Post by acidblue on 2010-03-29
zipinfo returns:


Zip file size: 14577 bytes, number of entries: 8
-rw-r--r--  2.0 unx     2832 bx defN 10-Mar-27 22:32 LM386 Amp.GBL
-rw-r--r--  2.0 unx       92 bx defN 10-Mar-27 22:32 LM386 Amp.GBO
-rw-r--r--  2.0 unx     1255 bx defN 10-Mar-27 22:32 LM386 Amp.GBS
-rw-r--r--  2.0 unx     8972 bx defN 10-Mar-27 22:32 LM386 Amp.GTL
-rw-r--r--  2.0 unx    48466 bx defN 10-Mar-27 22:32 LM386 Amp.GTO
-rw-r--r--  2.0 unx       92 bx defN 10-Mar-27 22:32 LM386 Amp.GTP
-rw-r--r--  2.0 unx     1255 bx defN 10-Mar-27 22:32 LM386 Amp.GTS
-rw-r--r--  2.0 unx      679 bx defN 10-Mar-27 22:32 LM386 Amp.TXT
8 files, 63643 bytes uncompressed, 13739 bytes compressed:  78.4%

---

### Post by acidblue on 2010-03-29
I just tried using Xarchiver instead of right clicking and choosing "compress", and that worked.

I don't know what program is being used in the right click menu
but it's doing something to the zip archives that makes them not open 
under windows.

Is there a way to change the right click menu so it uses Xarchiver?

---

### Post by Kevinator on 2010-03-29
It looks like Xarchiver and File Roller both just use zip in the background. There should be no difference, except possibly in the options they use.

That makes me think the actual problem is something more basic, like the file paths. If you make two identical archives, one using Xarchiver and one using File Roller, do they behave the same in Windows or on that web site?

---

### Post by acidblue on 2010-03-29
Xarchiver works fine.
File roller does not.

---

### Post by Kevinator on 2010-03-29
> **acidblue said:**
> Xarchiver works fine.
File roller does not.

My point is that neither of them actually create .zip files. Both invoke the external "zip" program for that purpose, so whatever problem you have with .zip files could affect both. It's clearly not File Roller that creates the problem, because in both cases the actual program creating the files is "zip".

---

### Post by Kevinator on 2010-03-29
I did a test compressing the same file with Xarchiver and File Roller. The resulting .zip files are bit-for-bit identical. The problem you are seeing has to be the result of something aside from the programs themeselves. It could be configuration differences, for example, or file paths that Windows doesn't like.

---

### Post by acidblue on 2010-03-29
It has to be File Roller.
I can make the exact same file in the exact same folder and
File Roller will will fail and Xarchiver will not.

Can I get rid of File Roller and use Xarchiver?
There's gotta be a way to add Xarchiver to my right click menu.

---

### Post by lisati on 2010-03-29
> **cjhabs said:**
> How big are the zip files? I have seen something similar on Windows for big zip files (database backups), where you have to be very particular with which zip program you use to create the zip files.
I've seen this too, when using Windows to archive folders with a large amounts of data. The annoying thing I've found is that often there's no obvious indication of an error when creating the file in the first place.
> **acidblue said:**
> It has to be File Roller.
I can make the exact same file in the exact same folder and
File Roller will will fail and Xarchiver will not.

This suggests to me that as others have suggested there might be some difference in the settings being used. No idea on what to look for, sorry.

---

