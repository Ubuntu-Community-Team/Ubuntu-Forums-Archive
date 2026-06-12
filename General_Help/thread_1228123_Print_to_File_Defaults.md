---
title: "Print to File Defaults"
date: 2009-07-31
forum: General Help
---

### Post by dstein on 2009-07-31
I searched for this but was surprisingly unable to find an answer.

How can I change the default settings of the "Print to File" option in the print dialog? I would like the default file type to be PDF instead of PS, and I would also like to change the default location. Please let me know how I can modify these settings. Thanks.

---

### Post by oldfred on 2009-07-31
Install  CUPS-PDF in Synaptic
it says - Documents are written to a configurable directory (by default to ~/PDF)

---

### Post by dstein on 2009-08-08
Thanks oldfred. I've installed CUPS-PDF in the past, after it was no longer included in the distribution. However, I'm looking for a way to modify the settings of the "Print to File" option in the print dialog.

---

### Post by kaibob on 2009-08-08
> **dstein said:**
> ...How can I change the default settings of the "Print to File" option in the print dialog? I would like the default file type to be PDF instead of PS, and I would also like to change the default location...
See post 2 in the following thread:

[http://ubuntuforums.org/showthread.php?t=1043339](http://ubuntuforums.org/showthread.php?t=1043339)

This worked in Hardy; I assume (but don't know) that this would also work in Intrepid.

---

### Post by davegk on 2009-09-01
No, that didn't work in Jaunty 64-bit. Changed the values suggested, plus the page size in both locations, but the "Print to File" still defaults to ps file format, /user_name/ location, and most annoyingly, to US Letter size page of resulting [pdf] file. 

Why is the whole pdf handling subject is almost totally ignored in Ubuntu? Solutions available are remarkably primitive and inflexible: CUPS-PDF with no file name and location choice, not to mention font handling, resolution, CMYK-RGB etc; "Print to File" with no apparent way to change default file type and location). 

I think that PDF handling is a very important matter, especially for those of us, recently converted :) , who are accustomed to production and editing of pdf files of various quality/size/purpose - from pre-press to low-res for email etc. We really need something like Acrobat Pro for Linux :P

Still, on a more down to Earth note - lets get back to the OP question: how do we change the default file type and location for the "Print to File"?

---

### Post by Camilia on 2009-09-01
I am a newbie thus might be wrong, but can't you change the end before you save it manually?

---

### Post by davegk on 2009-09-03
> **Camilia said:**
> I am a newbie thus might be wrong, but can't you change the end before you save it manually?

Of course, you can. But that wasn't the question :D

Actually, I have found a way to do this (after a lot of digging and cursing)

Here's what I did (step-by-step, for someone like myself):
1. In Firefox, type "about:config" in address bar
2. Type "file" in Filter bar - you will see all your printers listed with option "Print to File"
3. Change print_to_filename - output location/file_name.extension for ALL of your printers to be the same - your desired file type and destination, in my case: /home/user_name/Documents/web.pdf  Changing this for just printer_PDF and printer_Print_to_File won't work (well, it didn't in my case).

While we're on the subject of printing defaults, here's how I corrected paper size (from US Letter to A4) for the pdf prints:
1. Same as above
2. In Filter, type "paper"
3. Change print.postscript.paper_size from "Letter" to "A4"
4. Further down the same page, there will be settings for all your printers in the format: print.printer_ABCD.print_paper_name - change "na-letter" to "iso-a4". 
5. If the values for paper width and height are wrong, correct them too - i.e. 210 and 297 instead of 215 and 279. In my case these values were correct, but Print to File would still print in US Letter size, until I changed those mentioned in No.4

---

### Post by krivine on 2009-11-28
Thanks; for me on Jaunty, running FF 3.0.15, I can change the default location only if I specify the file type as 'PDF'. In other words, specifying **~/PDF/mozilla.pdf** works, but if I specify ~/PDF/mozilla.ps, FF ignores it, and defaults to **~/.ps**. 

Bizarre, and annoying.

---

### Post by Ubuntist on 2009-12-16
Thanks a lot, davegk!

This had been driving me crazy for quite a while.  The default behavior is something worthy of Microsoft, I hate to say.

Now I just wish we could get a better file browser built into the print-to-file command.  The current one is fine if you want to print to a file in one of the default directories, but to print to another directory you first have to select "Other..." and *then* you can start browsing to the directory you want.  Why can't it just be like Nautilus?

---

### Post by airtonix on 2010-05-30
> **davegk said:**
> Of course, you can. But that wasn't the question :D

Actually, I have found a way to do this (after a lot of digging and cursing)

Excellent.

Now do it again for google chrome and it's variants.
:P

---

### Post by davegk on 2010-05-30
> **airtonix said:**
> Excellent.

Now do it again for google chrome and it's variants.
:P
No can do - not using [yet?] Chrome/ium ... :P
I generally don't like messing about with my system - once it's all setup and running as I wanted, I just keep it going until it's time to change the laptop ... which is now and I wish I didn't have to do it ...

---

### Post by JustinR on 2010-05-30
Of course you guys can always use Opera which supports print to file formats. :P

---

### Post by quadra on 2010-06-18
Just changing the default pdf filename, when printing from Firefox:
It seems that we must change the preference for ALL printers in Firefox about:config:
[http://ubuntuforums.org/showpost.php?p=7890849&postcount=7]("http://ubuntuforums.org/showpost.php?p=7890849&postcount=7")

However, a general solution working in all applications is still missing.

---

### Post by blitzter47 on 2011-07-16
@dstein : I think it's time to write [SOLVED] in the title...

---

