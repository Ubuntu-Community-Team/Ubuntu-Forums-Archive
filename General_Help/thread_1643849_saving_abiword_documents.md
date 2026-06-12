---
title: "saving abiword documents"
date: 2010-12-12
forum: General Help
---

### Post by beacon on 2010-12-12
I have spent four hours writing a document in Abiword and five hours trying to save it. When I tick 'save as' the item is saved with all the instructions, printing symbols, and such like. I can't get just the text. I have never had this problem before and wonder what has gone wrong. I have consulted everything I can think of, especially the Abiword site.

This is a document for a court, with a deadline, and I would be very grateful for help.

---

### Post by mike555 on 2010-12-12
perhaps if you "print" it as a .pdf file ,then print it from the .pdf?

---

### Post by beacon on 2010-12-13
I appreciate the suggestion, but I have been unable to follow it. I seem to be able to print only what is on the screen which is a mixture of computer symbols and jargon and my own text.

Thanks for trying.

---

### Post by migs73 on 2010-12-13
Try going to 'View' and then deselect 'Show Formatting Marks'.

---

### Post by beacon on 2010-12-13
When I go to view there is no option to 'show format marks'.  Once again, however, I am grateful for your suggestions.

---

### Post by beacon on 2010-12-13
I thought I would copy the kind of information that is appearing on the screen in case my description wasn't clear. A bit further on there are interspersed bits of my document, but I can't get the document on its own.

I have managed to open the file in Open Office, copied it to Abiword and tried to save it that way. But the same garbled pages appear. 

xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE abiword PUBLIC "-//ABISOURCE//DTD AWML 1.0 Strict//EN" "http://www.abisource.com/awml.dtd">
<abiword template="false" styles="unlocked" xmlns:fo="http://www.w3.org/1999/XSL/Format" xmlns:math="http://www.w3.org/1998/Math/MathML" xid-max="78" xmlns:dc="http://purl.org/dc/elements/1.1/" fileformat="1.1" xmlns:svg="http://www.w3.org/2000/svg" xmlns:awml="http://www.abisource.com/awml.dtd" xmlns="http://www.abisource.com/awml.dtd" xmlns:xlink="http://www.w3.org/1999/xlink" version="1.9.1" xml:space="preserve" props="dom-dir:ltr; document-footnote-restart-section:0; document-endnote-type:numeric; document-endnote-place-enddoc:1; document-endnote-initial:1; lang:en-GB; document-endnote-restart-section:0; document-footnote-restart-page:0; document-footnote-type:numeric; document-footnote-initial:1; document-endnote-place-endsection:0">
<!-- ======================================================================== -->
<!-- This file is an AbiWord document.                                        -->
<!-- AbiWord is a free, Open Source word processor.                           -->
<!-- More information about AbiWord is available at [http://www.abisource.com/](http://www.abisource.com/) -->
<!-- You should not edit this file by hand.                                   -->
<!-- ======================================================================== -->

<metadata>
<m key="dc.format">application/x-abiword</m>
<m key="abiword.generator">AbiWord</m>
</metadata>
<history version="2" edit-time="1469" last-saved="1292176301" uid="0e0a4bcc-0615-11e0-9d9c-ff198ad22d0e">
<version id="2" started="1292176234" uid="7a293f36-0618-11e0-9d9c-ff198ad22d0e" auto="0" top-xid="78"/>
</history>

---

### Post by migs73 on 2010-12-13
For some reason your document is in XML format (for web publishing).

I have tried to replicate this in Abiword, but have not been able to do so.

Have you tried uninsalling/reinstalling Abiword?

Not a very technical solution but might work.

---

### Post by m_duck on 2010-12-13
I have just done a quick test and saved a document in Abiword and all was fine. If one opens an Abiword document in a text editor, one will see all of the XML markup that Abiword uses to store formatting options etc.

I am not an Abiword user, but it seems as though your document is being opened as a text file, rather than a formatted Abiword document. Perhaps renaming your document with a ***.abw*** extension could resolve the issue?

If not, hopefully this information is useful for someone who knows their way around Abiword better than myself.

---

### Post by beacon on 2010-12-13
I had tried that but tried once again after hearing from you. No joy I'm afraid. 

I am using Ubuntu 10.10 and Abiword 2.8.6. I must have done something odd when I wrote the document, but I can't for the life of me think what it was. I'd have thought I would be able to copy the content of the file and transfer it to a blank Abiword document, but it persists in transferring everything!!

I am grateful for your advice.

---

### Post by m_duck on 2010-12-13
Does the filename of the document in question contain a '.'? A comment [here](http://amplicate.com/hate/abiword) suggests that a dot in the filename can cause Abiword to display the XML document instead of formatted text.

***EDIT:***When you open your document, make sure your "Open file as type:" is set to "Automatically Detected" or "Abiword Documents". If set to "Text" Abiword imports the XML document, rather than the formatted text, as you explained is what is happening to you.

---

### Post by beacon on 2010-12-13
I really am grateful for the help, and I do try out all suggestions. In reply to M_Duck, I created a new document in order to see what happened, and when I saved I still got the full works, and not just the text.

Also I am set to 'automatic detect' and when I save, the box says save file as type: Abiword (.abw,.zabw,abw.gz).

I wonder if this helps.

---

### Post by tredegar on 2010-12-13
You say you can open the document with OpenOffice.
You also say you have a deadline.
So why not open / edit /print the document using OpenOffice? Once the deadline has passed, you can find out what is not correctly set (or, broken) with Abiword

---

### Post by Sef on 2010-12-13
1) How did you download abiword? Through the respositories or through abiword?

2) Could you post a screenshot of your problem.

---

### Post by beacon on 2010-12-13
I'm sorry, M-Duck that I failed to reply to one of your points. The name of the file is 'Court Submission', so there would seem to be no problem as far as the nomenclature.

Thanks, Tredegar. I had in fact decided that I would have to use Open Office, even though I can't get quite the format I wanted.

Sef, I have downloaded Abiword several times, mostly using synaptic package manager, but also trying the Ubuntu software Centre. I have taken a screen shot up to the point at which I am identifiable, but I can't seem to discover how to send it in this message.

---

### Post by migs73 on 2010-12-13
> **beacon said:**
>  I have taken a screen shot up to the point at which I am identifiable, but I can't seem to discover how to send it in this message.

If you save the screen shot to somewhere easy to find (Desktop?) then click on the paper clip sign on the top of the reply text box (you have to select new reply from the bottom of the posts as I don't think the option is there for quick reply) then click 'browse' and browse to the file. Select the file (i think it says 'open' in the box) then click on the upload button. Once done (will take a few seconds) click on 'close this window' at the top of the page.

Then continue with your post as normal.

---

### Post by beacon on 2010-12-14
Thanks migs73. I have followed directions and hope there is an attached screenshot.

---

### Post by beacon on 2010-12-21
I take it the screenshot didn't help. The problem persists. I removed Abiword completely, re-installed and saved it to desktop. That works well, but I then created from it a document 'letterhead', which I also saved to the desktop for writing letters. When I tick on it I still get all the red-lettered information contained in my screenshot.

More help would be appreciated.

---

### Post by beacon on 2010-12-27
The thread seemed to come to a sudden end, but I persevered and found the simple solution I was searching for in a thread from 2008:

The easiest way is to Right Click on that specific file, choose Properties -> Open With. There you can select an application to open that type of files! :D

Just the job.

---

