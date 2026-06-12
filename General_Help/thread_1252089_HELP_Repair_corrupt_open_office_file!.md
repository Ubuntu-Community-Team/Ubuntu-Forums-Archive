---
title: "HELP Repair corrupt open office file!"
date: 2009-08-28
forum: General Help
---

### Post by jkd18 on 2009-08-28
I can see the file sitting there saying 449.1 kb, but when i made a copy and said recover, a BLANK doc shows up, causing me angina attacks! 
Pls pls help!!!!!!!!!!!!! Got too much info there to lose. using 8.04
Thanks.
jkd

---

### Post by SPr on 2009-08-28
To clarify, when you double click this "broken" file Open Office starts and says it wants to recover a file.

Is the file OO wants to recover the same one you double clicked? It's a silly question but sometimes silly mistakes are made.

What happens if you double click the file and choose **not** to recover it?

What does
```

file /path/to/broken_file

```
say?

---

### Post by jkd18 on 2009-08-28
Thanks for replying!
It says 'General input/ output error'... Scary cos i really really need that data! 
It tried to recover, failed, when it repairs the copy i made, its a small blank doc.. 
yikes!:(

---

### Post by SPr on 2009-08-28
> **jkd18 said:**
> Thanks for replying!
It says 'General input/ output error'... Scary cos i really really need that data! 
It tried to recover, failed, when it repairs the copy i made, its a small blank doc.. 
yikes!:(

What says 'General input/ output error'? Please be more specific.

What does
```

lsof /path/to/broken_file

```
report?

Edit: This sounds like an OO error rather than an Ubuntu problem. The file is safe but OO probably has a bug in the recovery routine that means it can't read this particular file.

Edit: Searching Google for "general input/output error" gets a load of hits for OO. One thing that keeps appearing is reading files on a network share. Where is the file?

Edit: Please give full errors and accurate descriptions. We can't see your monitor and need you to tell us what happens as best as you can. We aren't mind readers.

---

### Post by jkd18 on 2009-08-29
Okay, sorry abt the panicky situation. Ok, i dont get ANY path!! What happens is, 
I double click the file (a spreadsheet) to open it. 
It says trying to recover it.
It fails and asks if it should repair the file. 
If i say yes, it 'repairs' it and opens me a COMPLETELY blank document :-( 
If I say No, it pops up a message headed GENERAL ERROR and says, 'Input/output error' 
Should i go into the terminal and try and repair..? Not tried that yet cos dont want to ruin things more! 
Thanks!!

---

### Post by oboedad55 on 2009-08-29
> **jkd18 said:**
> Okay, sorry abt the panicky situation. Ok, i dont get ANY path!! What happens is, 
I double click the file (a spreadsheet) to open it. 
It says trying to recover it.
It fails and asks if it should repair the file. 
If i say yes, it 'repairs' it and opens me a COMPLETELY blank document :-( 
If I say No, it pops up a message headed GENERAL ERROR and says, 'Input/output error' 
Should i go into the terminal and try and repair..? Not tried that yet cos dont want to ruin things more! 
Thanks!!

Don't panic. Have you tried opening the document from within OO?

---

### Post by jkd18 on 2009-08-29
Hey even when i try opening a REGULAR working document, it usually gives me an error- Not valid path or something! This one also Opened a blank doc for me after 'repairing'.. :-(

---

### Post by SPr on 2009-08-29
Open OO and click tools>options expand OpenOffice.org in the side bar then click "paths". Does the info there look correct?

Here's mine.

---

### Post by jkd18 on 2009-08-29
Yes, SPr! Its correct. What else should i check....?!

---

### Post by SPr on 2009-08-29
Well, either there is a major problem with your copy of OO or the file really is corrupt. But it seems strange that other documents created with OO are having the same problems.

```

aptitude reinstall openoffice.org

```

If the file is corrupt read [http://www.andybrain.com/archive/mb/open-office-data-recovery.htm](http://www.andybrain.com/archive/mb/open-office-data-recovery.htm) which shows several tricks to fix OO files. Google will know other pages to fix corrupted files.

I don't know what else to suggest and wish you the best of luck with this but please keep us informed of what my few suggestions do and include any info that could pass a hint to solve your problem.

This is one reason why I left Windows. "General input/output error" with no other information on what went wrong is a very MS-like error - no meaningful feedback at all.

---

### Post by stalkingwolf on 2009-08-29
have you tried "fix broken Packages"?  if not  restart  hit ESC when grub starts, if you dual boot select the recovery choice. it will run then pop up a screen with several choices.  select the fix broken and hit enter.
when that is done continue normal boot.

Hope that helps.

---

### Post by jkd18 on 2009-08-30
Thanks- yea well when i say other files get that error of 'not valid path'.. it opens ALL RIGHT when i go to Places and the directory and folders! Wierd. 
well, have sent it off to a friend who is trying to help. Will definately post an update, regardless of whether the problem is solved or not!....
Thanks!

---

### Post by oboedad55 on 2009-08-30
> **jkd18 said:**
> Thanks- yea well when i say other files get that error of 'not valid path'.. it opens ALL RIGHT when i go to Places and the directory and folders! Wierd. 
well, have sent it off to a friend who is trying to help. Will definately post an update, regardless of whether the problem is solved or not!....
Thanks!

Try moving your /home/user/.openoffice.org to your desktop or some place then restart OO. You'll lose your settings but it may fix your problem.

---

### Post by cguy on 2009-08-30
I've been through this...

That's why I always always always save another copy of the important files on another location; and I don't copy-paste the files but File > Save As... them.

I learned my painful lessons and so should anybody else :)

Good luck with the recovery!

---

