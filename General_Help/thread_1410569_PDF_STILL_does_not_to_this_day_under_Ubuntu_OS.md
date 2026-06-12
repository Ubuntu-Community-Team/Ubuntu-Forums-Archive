---
title: "PDF STILL does not to this day under Ubuntu O/S"
date: 2010-02-18
forum: General Help
---

### Post by wpshooter on 2010-02-18
This is about the 3rd or 4th year that I have tried to fill in my Federal tax return on the IRS website using Ubuntu/Firefox/pdf program(s).

Still to this day the PDF functions found available (or should I say unavailable) (whether using either EVINCE or ACROREAD) for this O/S will not properly function in allowing you to CONSISTENTLY complete a PDF IRS form on their website, print and then save that completed IRS form to the hard drive of your computer.

This is sort of ridiculous !!!

Yes, I have report this as a bug NUMEROUS times and it is still not fixed.

---

### Post by n0dix on 2010-02-18
I dont't think this is the place for this thread. You should know that.

---

### Post by wpshooter on 2010-02-18
> **n0dix said:**
> I dont't think this is the place for this thread. You should know that.

Then what is the correct place.

How is it that you know, what it is that I should know ???

---

### Post by temporos on 2010-02-18
First, please try to remain calm.

Next, if you are running v9.04, then it should have come with Document Viewer (part of the evince project).  When you attempt to open a PDF file in Firefox, it should ask you if you wish to open the document using Document Viewer or save it to your home directory (or whichever directory you set as the Firefox default download location).  If you opt to open it with Document Viewer, the application will open, and you may edit the PDF at-will.  When you're finished, you may print it out, save it, or send it to a contact.

Unless there is a newly-discovered bug I don't know about, then it *should* work...  Check [here]("http://ubuntuforums.org/showthread.php?t=1145967") to see if it's been mentioned in the bug log.

---

### Post by n0dix on 2010-02-18
> **wpshooter said:**
> Then what is the correct place.

How is it that you know, what it is that I should know ???

i mean you have several years with Ubuntu and over 3000 post. you don't post a problem that concerns directly with Ubuntu but the developers of Evince or Acroread. If you have sereval times this problem tried to communicate with them.

---

### Post by SoFl W on 2010-02-18
I don't think it is a bug, if I remember correctly from previous years, the form says on it "Your edits can not be saved."    I believe the form can only be printed. 

My advice is to print it to a PDF file.  You can't edit later but you have a saved file.



UPDATE: I tried it on my Windows boot and you can save it. 
Don't know why I didn't think you could

---

### Post by lovinglinux on 2010-02-19
Try [gPDF](https://addons.mozilla.org/en-US/firefox/addon/14814) extension for Firefox. It scan webpages for pdf links and set them to open with Google PDF viewer.

---

### Post by wpshooter on 2010-02-19
> **SoFl W said:**
> I don't think it is a bug, if I remember correctly from previous years, the form says on it "Your edits can not be saved."    I believe the form can only be printed. 

My advice is to print it to a PDF file.  You can't edit later but you have a saved file.



UPDATE: I tried it on my Windows boot and you can save it. 
Don't know why I didn't think you could

You're exactly correct.  All of this works extremely fine under M/S windows but STILL after all these years will not work correctly under Ubuntu !!!

---

### Post by mechro on 2010-02-19
Probably none of my business since I'm in UK but I've downloaded a Form 1040 through Firefox (disabled Adobe Reader so I get the download option) and also through Opera. I can edit and save this PDF form. What am I doing wrong? :???:

---

### Post by SoFl W on 2010-02-19
> **mechro said:**
> Probably none of my business since I'm in UK but I've downloaded a Form 1040 through Firefox (disabled Adobe Reader so I get the download option) and also through Opera. I can edit and save this PDF form. What am I doing wrong? :???:

What reader are you using?

---

### Post by SoFl W on 2010-02-19
This is important to me also but haven't run across it as much because up until a few months ago I still used Windows primarily. Will this help you?

[http://www.cyberciti.biz/tips/open-source-linux-pdf-writer.html](http://www.cyberciti.biz/tips/open-source-linux-pdf-writer.html)

---

### Post by philinux on 2010-02-19
Saves to desktop fine here.

Karmic 32 bit
Acroread 9.3
Firefox 3.5.7

---

### Post by SoFl W on 2010-02-19
Just so there is no confusion, he is talking about saving after filling out the PDF not saving it from a website.  (The browser doesn't matter)

---

### Post by mechro on 2010-02-19
> **SoFl W said:**
> What reader are you using?

Evince.

To clarify, I'm saying it works for me. I don't know the exact procedure for filing IRS returns via editable PDF's as I have enough problems with the UK tax system, but if it's possible to download the PDF form, edit it, save it, print it then it works fine.

Is there some IRS rule that says you have to complete the form online and then save it?

---

### Post by SoFl W on 2010-02-19
[http://www.irs.gov/](http://www.irs.gov/)
forms are on the left side.

I can download a form and save it locally. I can open it up, fill out the form, I can save the form, but the data I entered is not saved.  The blank opens up when I click on the form I saved. 
There are no rules to completing it on-line.  The same form will allow you to edit and save your edits in Windows.

Document Viewer 2.28.1
Using poppler 0.12.0 (cairo)
© 1996–2009 The Evince authors

---

### Post by AudioDef on 2010-02-19
I'm not sure you can save it along with the entered data. You have to fill out the form and print it. 

Government web sites are also generally not Linux-friendly, at least not in the US. Some things may work, but not because Linux was considered.

---

### Post by mechro on 2010-02-19
Evince 2.26.1 in jaunty does save the data entered.

---

### Post by hugmenot on 2010-02-20
Saves fine in Lucid too.

---

### Post by luigi_mb on 2010-02-20
Check whether Evince may have saved the modified file in a different folder !

/luigi

---

### Post by wpshooter on 2010-02-21
> **mechro said:**
> Evince 2.26.1 in jaunty does save the data entered.

Problem with Evince is that is just a shot in the dark (works sometimes but most of the times you can not even get the information typed into the fields) as to whether you can get the information typed into the form if you are attempting to do it directly from/on the IRS website.

And also on my Jaunty machine at least Evince does NOT save the filled in  information to the hard drive ONLY the form in it's original state as per the IRS website.  Yes, I know how to lookup and find the form on my hard drive once it is saved.

It appears that the only way to get this to work is to save the form to the hard drive then open it using ACROREAD (not Evince) and you can then fill it in and save the filled in changes once you are finished.

You do not have to jump thru these hoops if you are trying to do this on a M/S windows machine using IE.  You just call up the form on/at the IRS website, fill it in, print it if you wish, then save it to your hard drive and then you can print out a copy of the filled in form at a later time if you wish.

UBUNTU and Firefox and perhaps even the IRS need to get together and fix this so it can work proper on a Ubuntu computer.

It is embarrassing to recommend Ubuntu to your family and friends and then have them tell you that I could do this fine on my Windows machine, why can't I do it under Ubuntu if it is supposed to be such a superior O/S over M/S windows !!!

And P.S., I don't care if Evince, Acroread and Firefox are not a direct part of Ubuntu, they are the tools that are provided to accomplish this task under Ubuntu, so they need to be fixed if this O/S is going to be considered to be used instead of M/S windows.  And no, I am not going to use both M/S and Ubuntu, I am going to use one or the other.

Thanks.

---

### Post by mcduck on 2010-02-21
> **wpshooter said:**
> Problem with Evince is that is just a shot in the dark (works sometimes but most of the times you can not even get the information typed into the fields) as to whether you can get the information typed into the form if you are attempting to do it directly from/on the IRS website.

And also on my Jaunty machine at least Evince does NOT save the filled in  information to the hard drive ONLY the form in it's original state as per the IRS website.  Yes, I know how to lookup and find the form on my hard drive once it is saved.

It appears that the only way to get this to work is to save the form to the hard drive then open it using ACROREAD (not Evince) and you can then fill it in and save the filled in changes once you are finished.

You do not have to jump thru these hoops if you are trying to do this on a M/S windows machine using IE.  You just call up the form on/at the IRS website, fill it in, print it if you wish, then save it to your hard drive and then you can print out a copy of the filled in form at a later time if you wish.

UBUNTU and Firefox and perhaps even the IRS need to get together and fix this so it can work proper on a Ubuntu computer.

It is embarrassing to recommend Ubuntu to your family and friends and then have them tell you that I could do this fine on my Windows machine, why can't I do it under Ubuntu if it is supposed to be such a superior O/S over M/S windows !!!

Thanks.

So, even in Windows you have to print the form or save it to your hard drive, but saving it *before* you edit it is a problem to you? :D

What's the big difference between saving it first or saving it after editing?

---

### Post by Swagman on 2010-02-21
No probs here too.

Did I do something wrong ?  I downloaded the form (no extra progs installed), filled it in and saved to the desktop.

opened it on the desktop and it's still filled in ?

[**Screengrab**](http://www.upload3r.com/serve/210210/1266762198.jpeg)

Is that not what the OP is trying to do ?

---

### Post by temporos on 2010-02-21
**Swagman: **:lol:  I like the names of your kids.

**wpshooter: **One more time: calm... down...  Anger helps no one, yourself included.

---

### Post by wpshooter on 2010-02-21
> **Swagman said:**
> No probs here too.

Did I do something wrong ?  I downloaded the form (no extra progs installed), filled it in and saved to the desktop.

opened it on the desktop and it's still filled in ?

[**Screengrab**](http://www.upload3r.com/serve/210210/1266762198.jpeg)

Is that not what the OP is trying to do ?

No it is not.

In Windows you can fill out this form DIRECTLY when on the IRS website, without downloading, saving or anything else.  If you have a windows computer go to the IRS website find the 1040 form, start filling it in, you do not have to download, save or do anything else **_PRIOR_** to properly fill out this form and then printing it.  After having done so, I can save it if I choose or I can just close the website, in which case I do not windup saving this filled in form that I just printed.  This is the same way it should work under Ubuntu.

---

### Post by wpshooter on 2010-02-21
> **temporos said:**
> **Swagman: **:lol:  I like the names of your kids.

**wpshooter: **One more time: calm... down...  Anger helps no one, yourself included.

I am not angry, just want someone to fix this, so I can recommend this O/S without being embarrassed.

Thanks.

---

### Post by Seq on 2010-02-21
What, nobody checked for bugs yet?

According to [Ubuntu bug 153428]("https://bugs.edge.launchpad.net/evince/+bug/153428") and [Gnome bug 480668]("https://bugzilla.gnome.org/show_bug.cgi?id=480668") poppler can indeed save forms, and evince supports it. However, according to [Ubuntu bug 307459]("https://bugs.edge.launchpad.net/ubuntu/+source/poppler/+bug/307459") and [Freedesktop.org bug 19915]("https://bugs.freedesktop.org/show_bug.cgi?id=19915"), they can not save form contents on encrypted forms. The bug is marked fixed as it was previously writing corrupted files.

I tried it with the Passport Canada renewal form in evince and get an error about the document being encrypted when I select 'Save a Copy', although I can view and edit it.

(Nevermind the entire benefit of filling out the passport is to have Adobe's javascript support build a QR code matrix based on the data you entered, thus removing the need for the clerk to enter that data. This is something Evince doesn't do.)

---

### Post by mechro on 2010-02-21
> **wpshooter said:**
> Problem with Evince is that is just a shot in the dark (works sometimes but most of the times you can not even get the information typed into the fields) as to whether you can get the information typed into the form if you are attempting to do it directly from/on the IRS website.

And also on my Jaunty machine at least Evince does NOT save the filled in  information to the hard drive ONLY the form in it's original state as per the IRS website.  Yes, I know how to lookup and find the form on my hard drive once it is saved.

It appears that the only way to get this to work is to save the form to the hard drive then open it using ACROREAD (not Evince) and you can then fill it in and save the filled in changes once you are finished.

You do not have to jump thru these hoops if you are trying to do this on a M/S windows machine using IE.  You just call up the form on/at the IRS website, fill it in, print it if you wish, then save it to your hard drive and then you can print out a copy of the filled in form at a later time if you wish.

UBUNTU and Firefox and perhaps even the IRS need to get together and fix this so it can work proper on a Ubuntu computer.

It is embarrassing to recommend Ubuntu to your family and friends and then have them tell you that I could do this fine on my Windows machine, why can't I do it under Ubuntu if it is supposed to be such a superior O/S over M/S windows !!!

And P.S., I don't care if Evince, Acroread and Firefox are not a direct part of Ubuntu, they are the tools that are provided to accomplish this task under Ubuntu, so they need to be fixed if this O/S is going to be considered to be used instead of M/S windows.  And no, I am not going to use both M/S and Ubuntu, I am going to use one or the other.

Thanks.

Ah, right! I guess in Windows you're using the Adobe IE plugin. You can do the same in Ubuntu... get the "official" Adobe plugin for Firefox and it should do all that you ask. I've just tested it with Opera browser and as long as you use the File Save button in the Adobe Plugin window then it saves the form and any data you've entered.

Edit... er... OK, you have Acroread... as I said try using the buttons in the Plugin window rather than your browser's menu/buttons.

Edit again... tested in Firefox... OK... button thingy again.

---

### Post by hugmenot on 2010-02-21
> **wpshooter said:**
> No it is not.

In Windows you can fill out this form DIRECTLY when on the IRS website, without downloading, saving or anything else.  If you have a windows computer go to the IRS website find the 1040 form, start filling it in, you do not have to download, save or do anything else **_PRIOR_** to properly fill out this form and then printing it.  After having done so, I can save it if I choose or I can just close the website, in which case I do not windup saving this filled in form that I just printed.  This is the same way it should work under Ubuntu.

I think you’re being anal retentive about this. Please don’t waste our time. There are more pressing matters to solve than this.

---

### Post by ridgeland on 2010-02-21
Are you using an AMD processor?
I started a similar thread
[http://ubuntuforums.org/showthread.php?t=1411966](http://ubuntuforums.org/showthread.php?t=1411966)
My problem is AMD only.  Intel works fine here.
I tried evince (Document Viewer) but it was hard to go from field to field.
I tried Okular.  Seemed to work but save and open and won't open ... huh?  Still trying.

---

### Post by wpshooter on 2010-02-21
> **mechro said:**
> Ah, right! I guess in Windows you're using the Adobe IE plugin. You can do the same in Ubuntu... get the "official" Adobe plugin for Firefox and it should do all that you ask. I've just tested it with Opera browser and as long as you use the File Save button in the Adobe Plugin window then it saves the form and any data you've entered.

Edit... er... OK, you have Acroread... as I said try using the buttons in the Plugin window rather than your browser's menu/buttons.

Edit again... tested in Firefox... OK... button thingy again.

Yes, I have all of the proper plugins.  Still does not work properly.

And thanks, at least you have the correct attitude and are willing to try to help (unlike some others here who appear to be to important to try to help or to be bothered by this).

And no am not using AMD processor, using Intel on all of my computers.

Thanks again.

---

### Post by mechro on 2010-02-21
I'm out of suggestions.

It's probably something to do with the version of Acroread you have installed combined with the source and method of installation. In my own case I can't remember whether I got Acroread from a Ubuntu partner repository or whether I clicked and installed direct from Adobe. :neutral:

I notice that the IRS recommends that you follow the download first, edit after method, even for Windows...

[http://www.irs.gov/formspubs/article/0,,id=98121,00.html](http://www.irs.gov/formspubs/article/0,,id=98121,00.html)

Good Luck in your taxing adventures! :D

---

### Post by ridgeland on 2010-02-21
Interesting.
I download "fill-in and save" pdfs from the IRS site from:
[http://www.irs.ustreas.gov/app/picklist/list/formsInstructions.html](http://www.irs.ustreas.gov/app/picklist/list/formsInstructions.html)
With an Intel PC and acroread I fill in the form, save it, open it again, edit some more, print it and mail it in.  (with AMD this is broken)
From the hints you have given you are using some kind of on-line form.  What is the link?  Why do you even say it is pdf if it is an on-line form?
Free-file takes me off to third party land.  So I abort and choose the privacy of pdfs on my PC.

---

### Post by mechro on 2010-02-21
> **ridgeland said:**
> Interesting.
I download "fill-in and save" pdfs from the IRS site from:
[http://www.irs.ustreas.gov/app/picklist/list/formsInstructions.html](http://www.irs.ustreas.gov/app/picklist/list/formsInstructions.html)
With an Intel PC and acroread I fill in the form, save it, open it again, edit some more, print it and mail it in.  (with AMD this is broken)
From the hints you have given you are using some kind of on-line form.  What is the link?  Why do you even say it is pdf if it is an on-line form?
Free-file takes me off to third party land.  So I abort and choose the privacy of pdfs on my PC.

It's a PDF that opens in the Adobe/Acroread browser plugin rather than "download". So technically I suppose it's not "on-line", it just looks that way 'cos you're still in your browser.

---

### Post by SoFl W on 2010-02-24
WP, I was able to get it to save with "acroread" and it is available in the package manager.  I believe it is an Adobe product.

---

### Post by wpshooter on 2010-02-26
> **SoFl W said:**
> WP, I was able to get it to save with "acroread" and it is available in the package manager.  I believe it is an Adobe product.

If you got it saved to the hard drive (along with your typed in changes to the forms fields) **_AFTER_** having filled in the form, then there must be something different between your Ubuntu O/S and the Acroread that is on my computer because mine will **_NOT SAVE THE FILLED IN CHANGES_**.  Will save the form but not what I typed into the form !!!

Thanks.

---

### Post by ridgeland on 2010-02-26
I've got a mixed bag.
I saved the blank forms to the hard drive.  Then I used evince (Document Viewer) because acroread refuses to open fill-in forms with AMD.  I running along fine until I found that Schedule D and Form 8606 that I had filled in were blank.  Testing some more they only save as blank, data is always lost.  I did get 1040 and Schedule B to save the data. I want a form I can edit again if needed.  My solution was to open the pdf, like Sch D, in the gimp at 300 dpi.  Crop away the borders (about 1/2 inch) then save it as a jpg 7.5" x 10".  Use open office with borders of 1/2 inch and set the page -> background to the jpg and type on it.
For the Wisconsin state form another odd thing.  It must use some java or such that evince doesn't like.  The number on the bottom of page 1 should go to the top of page 2.  But it doesn't and refuses to let me type there too.  So I wrote in those fields.
The biggest user interface dislike with evince is I cannot move from field to field with tab.  So I click each field.  Maybe there is a key stroke but I don't know it.

---

### Post by ridgeland on 2010-02-26
One quick thought.
Try as root and see if it's a permissions issue.  Verify you have full read+write rights.

---

### Post by SoFl W on 2010-02-26
> **wpshooter said:**
> If you got it saved to the hard drive (along with your typed in changes to the forms fields) **_AFTER_** having filled in the form, then there must be something different between your Ubuntu O/S and the Acroread that is on my computer because mine will **_NOT SAVE THE FILLED IN CHANGES_**.  Will save the form but not what I typed into the form !!!
Thanks.

I was having the wont save the changes problem just like you with "document reader" (evince)  but when I used "acroread" I was able to save the changes.  You are saying that it wont save the changes with both acroread and evince?

---

### Post by wpshooter on 2010-02-26
> **SoFl W said:**
> I was having the wont save the changes problem just like you with "document reader" (evince)  but when I used "acroread" I was able to save the changes.  You are saying that it wont save the changes with both acroread and evince?

Yes, that is what I am saying.

Thanks.

---

### Post by wpshooter on 2010-02-27
After all of this, I have pretty much come to the conclusion, that this is a problem with FIREFOX browser and not problem with either Evince, Acroread, or full version of Adobe Reader.  Because if you save the original IRS form to the hard drive and then open it from there in either Evince, Acroread, or full version of Adobe Reader, (which means that FIREFOX is out of the picture) then the form can be opened, filled in and saved perfectly.

Thus someone needs to discover what the shortcomes of FIREFOX is, because like I said earlier, this problem does not exit on a M/S windows computer using the IE browser.

I will be reporting this as a FIREFOX bug.

Thanks.

---

