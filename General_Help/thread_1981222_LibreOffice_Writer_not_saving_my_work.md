---
title: "LibreOffice Writer not saving my work"
date: 2012-05-16
forum: General Help
---

### Post by eulu on 2012-05-16
My Ubuntu12.04x64 locked up yesterday  and I had hours of text that I had written open in a LOW session of my docx file... 

I noticed that the file size was 14.5kb when I went to reopen my docx file. 

After restarting my computer and launching my work, LOW prompted me for file recovery, which I regrettably went ahead and allowed. This time I lost hours of writing. The file size went back to around 12kb.

[I have used the LOW file recovery feature in the past when my Ubuntu locked up and it had always worked before (the few times that it has occurred), so I didn't even hesitate this time...]

After some cursing and frustration, I regrouped and proceeded to redo the hours of writing that I had lost, while saving my work every couple minutes.

When I finally got caught up to what I had lost, I was tired, so I did a last save and closed out my document. Just to be sure, I reopened my document to make sure my work was there, and NO IT WAS GONE! ARGH! Once again, hours of my dutiful writing is gone, lost into the ether.

The weird thing is, the file size this time is still at 14.6KB, but it is back to where it was after the first fateful file recovery as far as the content goes, so it should theoretically be around 12kb in size.. 

Bizarre, and ultra lame for me. Not sure what to do from now on, other than copy my text into another non docx file as backup periodically. 

Now it's time for me to muster my energies back up to do all this work again... 

Fellow LOW users beware! Do some backups.

---

### Post by eulu on 2012-05-16
I guess I have been skewed by my suffering, but I did think to try emailing the doc to a windows pc and it wouldn't open in Word 2010 there, even with file recovery, so there was apparently some file corruption that happened and given that possibility I shouldn't have redone my work without testing that.. Live and burn...

---

### Post by eulu on 2012-05-16
I can't help but wonder though if there is some way to recover the data in this file. I made a copy of the corrupted 14.6KB file then edited it with just a few added words, and saved it and the size is 13kb. So my corrupted file must have some kind of recollection to my work in there..

---

### Post by rai4shu2 on 2012-05-16
> **eulu said:**
> Fellow LOW users beware! Do some backups.

That's good advise when using any editor. Not just LO. I periodically go to my file manager and make a zip file of my work which I then store on an external drive. It saves a lot of headaches.

Of course, you really should fix whatever is causing those lockups. I don't know if I would put up with that.

---

### Post by eulu on 2012-05-16
I tried a recovery tool in windows on the only bak file that was in the backup folder and it couldn't recover the missing text.. 

Then I read through this thread and am not sure I am going to be using LOW anymore..  

[http://ubuntuforums.org/showthread.php?t=1749111](http://ubuntuforums.org/showthread.php?t=1749111)

---

### Post by scouser73 on 2012-05-16
> **eulu said:**
> I can't help but wonder though if there is some way to recover the data in this file. I made a copy of the corrupted 14.6KB file then edited it with just a few added words, and saved it and the size is 13kb. So my corrupted file must have some kind of recollection to my work in there..

I would suggest deleting your LibreOffice profile, this can be done by going to your home folder, press Ctrl & H and hidden files will appear.  Then click on the file named **.config**, look for the **libreoffice** folder and delete it.

Deleting that folder will not result in you losing your work, once you restart LibreOffice you will see that the folder is back, and in theory LibreOffice should function normally.

---

### Post by eulu on 2012-05-16
> **rai4shu2 said:**
> Of course, you really should fix whatever is causing those lockups. I don't know if I would put up with that.

Yeah.. I['ve thought about it but not sure what to do. They are entirely random. The only thing I have noticed at all is that either every time or most of the time when the lockups happen, I am streaming something in Firefox using Flash.. If that is the culprit, then I am at a loss what steps to take from there..

---

### Post by eulu on 2012-05-16
> **scouser73 said:**
> I would suggest deleting your LibreOffice profile, this can be done by going to your home folder, press Ctrl & H and hidden files will appear.  Then click on the file named **.config**, look for the **libreoffice** folder and delete it.

Don't worry, this folder will reproduce itself once you restart LibreOffice.

Will do thanks

---

### Post by bryncoles on 2012-05-16
Can't help with your problems I'm afraid... But I can offer my 2 pence worth.  I have noticed poor file fidelity with .docx (and .rtf) -- they are unreliable in LO, in my experience.  As such, I recommend people save as .odt files (or whatever the open document format standard is) while they're working on the document, and only bother saving it as .doc or .docx when it's finished and ready to send to collaborators.  

Hope you fix your freezing issue!

---

### Post by eulu on 2012-05-16
> **bryncoles said:**
> Can't help with your problems I'm afraid... But I can offer my 2 pence worth.  I have noticed poor file fidelity with .docx (and .rtf) -- they are unreliable in LO, in my experience.  As such, I recommend people save as .odt files (or whatever the open document format standard is) while they're working on the document, and only bother saving it as .doc or .docx when it's finished and ready to send to collaborators.  

Hope you fix your freezing issue!

Thanks! I have had that thought myself about working in ODT as I am preparing to move forward..

---

### Post by forrestcupp on 2012-05-16
> **bryncoles said:**
> Can't help with your problems I'm afraid... But I can offer my 2 pence worth.  I have noticed poor file fidelity with .docx (and .rtf) -- they are unreliable in LO, in my experience.  As such, I recommend people save as .odt files (or whatever the open document format standard is) while they're working on the document, and only bother saving it as .doc or .docx when it's finished and ready to send to collaborators.  

Hope you fix your freezing issue!

Great advice. 

LibreOffice's .docx compatibility is dismal. If you need it to be compatible with MS Word, you would be better off saving the finished document to a .doc, and converting it to .docx in Word. LibreOffice's .docx formatting won't match up very well at all in MS Word.

---

### Post by eulu on 2012-05-16
I can already tell that ODT is more stable, even just while writing in it. I don't get the little pauses I was getting occasionally, and I am also able to do more successful copying and pasting in and out of it, compatibility wise..  I feel better now :-)

---

### Post by bryncoles on 2012-05-17
Good!  I believe recent versions of MS Office support the .odt format too (though I don't know how well).  

Hopefully, that's one problem resolved at least!

---

