---
title: "Abiword doesnt open .abw"
date: 2012-01-03
forum: General Help
---

### Post by mrbambocha on 2012-01-03
Dont know why it wont open any abw-files anymore. I just closed the document, fotgot something and now it says it probaly not a real file (says the same about all abw files).

---

### Post by xc3RnbFO8P on 2012-01-03
Open Abiword in Terminal:
> abiword
open some .abw files and post the output from Terminal here.

---

### Post by mrbambocha on 2012-01-03
Sorry, im totally bew with linux, how do i "check the output from Terminal "?

---

### Post by xc3RnbFO8P on 2012-01-03
> **mrbambocha said:**
> Sorry, im totally bew with linux, how do i "check the output from Terminal "?

In Dash type terminal

Hope this will help
just type abiword 
return
and open a .abw file

---

### Post by mrbambocha on 2012-01-03
Ok, dont know if its the same, didnt find anything about dash in lubuntu, but googled it and found LXTerminal. So in LXTerminal I wrote abiword, abiword opened and I tried to open a document, but nothing happend in the terminal. I just got a popup saying abiword couldnt open the file (inkl the file path) and saying its probably not a real document. I tried to take a print screen but I cant paste it into MTPaint.

---

### Post by xc3RnbFO8P on 2012-01-03
In your home folder is hidden folder ./config/**AbiSuite**
delete the AbiSuite folder 
and restart Abiword, see if that helps.

---

### Post by mrbambocha on 2012-01-03
> **Ringi said:**
> In your home folder is hidden folder ./config/**AbiSuite**
delete the AbiSuite folder 
and restart Abiword, see if that helps.

Didnt work. 
Also tried to install libreoffice and that didnt work either.

---

### Post by xc3RnbFO8P on 2012-01-03
Hmm, fresh install of Lubuntu I think

---

### Post by mrbambocha on 2012-01-03
Is there no way to solve it? What happend? 
How do I make a partition to save all my files?

---

### Post by xc3RnbFO8P on 2012-01-03
Dont you have Hard Disk, Usb Key, write it on a cd or dvd. UbuntuOne, Dropbox?
Maybe install it side by side with the old Lubuntu.

---

### Post by mrbambocha on 2012-01-03
Ok, will have a look at the other options, asked because im new to linux and didnt know what options there were, since I dont have an external drive. 

But how can it be so drastic that I need to reinstall it all again?

---

### Post by xc3RnbFO8P on 2012-01-03
Maybe you don't have to, if only got this problem you don't.
How did you install Abiword (ubuntu software center or synaptic package manager)

---

### Post by mrbambocha on 2012-01-03
It came preinstalled with lubuntu? I could reinstall it, but that doesnt explain why they cant be opened with libreoffice. Myabe abiword did something to the files? 

I tried to create a new abi document now, close it and reopen it and that worked fine. But files older then yesterday doesnt work.

---

### Post by xc3RnbFO8P on 2012-01-03
> **mrbambocha said:**
> > but that doesnt explain why they cant be opened with libreoffice.

LibreOffice doesn't open .abw like Abiword  

it would look somthing like this:
[QUOTE]<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE abiword PUBLIC "-//ABISOURCE//DTD AWML 1.0 Strict//EN" "http://www.abisource.com/awml.dtd">
<abiword template="false" styles="unlocked" xmlns:fo="http://www.w3.org/1999/XSL/Format" xmlns:math="http://www.w3.org/1998/Math/MathML" xid-max="5" xmlns:dc="http://purl.org/dc/elements/1.1/" fileformat="1.0" xmlns:svg="http://www.w3.org/2000/svg" xmlns:awml="http://www.abisource.com/awml.dtd" xmlns="http://www.abisource.com/awml.dtd" xmlns:xlink="http://www.w3.org/1999/xlink" version="0.99.2" xml:space="preserve" props="dom-dir:ltr; document-footnote-restart-section:0; document-endnote-type:numeric; document-endnote-place-enddoc:1; document-endnote-initial:1; lang:en-US; document-endnote-restart-section:0; document-footnote-restart-page:0; document-footnote-type:numeric; document-footnote-initial:1; document-endnote-place-endsection:0">
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
<rdf>
</rdf>
<history version="1" edit-time="33" last-saved="1325613912" uid="67a469e6-3635-11e1-8c35-c9f4503e2998">
<version id="1" started="1325613912" uid="7b6aa5a8-3635-11e1-8c35-c9f4503e2998" auto="0" top-xid="5"/>
</history>
<styles>
<s type="P" name="Normal" followedby="Current Settings" props="font-family:Times New Roman; margin-top:0pt; color:000000; margin-left:0pt; text-position:normal; widows:2; font-style:normal; text-indent:0in; font-variant:normal; font-weight:normal; margin-right:0pt; font-size:12pt; text-decoration:none; margin-bottom:0pt; line-height:1.0; bgcolor:transparent; text-align:left; font-stretch:normal"/>
</styles>
<pagesize pagetype="Letter" orientation="portrait" width="8.500000" height="11.000000" units="in" page-scale="1.000000"/>
<section xid="4" props="page-margin-footer:0.5in; page-margin-header:0.5in">
<p style="Normal" xid="5"><c>kljflksdjflksdfj sdjflk</c></p>
<p style="Normal" xid="1"><c>lkdjfkldjflkd</c></p>
<p style="Normal" xid="2"><c></c></p>
<p style="Normal" xid="3"><c>lifjisdfjsdjfisdoifusdio</c></p>
</section>
</abiword>

---

