---
title: "sony ebook reader prs 650 touch + adobe digital edition"
date: 2010-11-12
forum: General Help
---

### Post by Gatemaze on 2010-11-12
Hi community,

the issue I am facing is that adobe digital editions does not see my ebook reader (sony prs 650). A bit more info:

1. adobe digital editions runs through wine... the exe was takes from a windows installation and copied to linux as described on another thread. I confirm that it works just fine.
2. My PRS is seen by the operating system and can be browsed as an external storage device.
3. Calibre recognises the PRS just fine.

How can it also be seen by adobe digital editions? Any clues anyone?

Thanks.

---

### Post by Gatemaze on 2010-11-13
bump

---

### Post by Idefix82 on 2010-11-14
Hi Gatemaze,

I am also thinking of buying that reader and I wanted to ask about the compatibility with Ubuntu. I am a total novice when it comes to eBook readers. So my question is: can you just load books onto the reader through nautilus? What exactly is adobe digital editions for?

Thanks! Sorry that I am asking questions instead of helping you with your problem!

---

### Post by Gatemaze on 2010-11-15
No worries mate... To your questions now....

> **Idefix82 said:**
> Hi Gatemaze,
I am also thinking of buying that reader and I wanted to ask about the compatibility with Ubuntu. I am a total novice when it comes to eBook readers. 

Very good reader... totally satisfied so far...

> **Idefix82 said:**
> 
So my question is: can you just load books onto the reader through nautilus? 

Yes very much fine with copying/pasting with nautilus... Also works flawlessly with calibre.

> **Idefix82 said:**
> 
What exactly is adobe digital editions for?

For downloading and loading in one step purchased ebooks with DRM. Other than that not necessary.

I'll post again when I have more news on this.

---

### Post by CbrPad on 2010-12-10
I have a Sony PRS650 which I think is great.  I use Calibre to manage my library but refuse to buy DRM books because of these type of issues.
Anyway, I found this on another website and hope it might be useful and relevant.  


There are a few threads on the web about transferring DRMed books to the Sony reader on a Linux machine. Folks seem to be reporting varying levels of success. This is what worked for me:

The hardware: Sony PRS-350 aka Pocket Edition

The software: Ubuntu Linux 10.04 Lucid Lynx + Wine 1.2 + Adobe Digital Editions 1.7.2 (ADE) + Sony's Library software 3.3 + calibre 0.7.32

The bookstore: Kobo

The process:
1 Borrow, beg or steal a Windows XP machine.
2 Download and install ADE on it.
3 Plug in the reader.
4 Once mounted, go to the SETTINGS directory and run the Install thingy (for the Sony library software).
5 Run ADE
6 Authorize your PC (the tiny arrow next to "Library" has the authorize option)
7 Authorize the reader
8 Exit, unplug, shut down and leave the building (you could probably uninstall your mess first, you only need it this once anyway)
9 Start your Ubuntu machine
10 Download the Sony Library software (from the web this time - on my machine the SETTINGS folder never mounted on Ubuntu)
11 Install it under wine. I don't know if this is necessary but do it anyway, just in case.
12 Download ADE for Windows and install it under wine as well
13 Run ADE
14 Authorize your machine (no need to do the reader again, just the PC)
15 Go to Kobo, register an account and buy a book (the paid ones all have DRM)
16 Click "Download EPUB" to get the tiny acsm file
17 Drag & drop the acsm file on the ADE window. This should download the actual EPUB file.
18 Close ADE
19 Install calibre (NOT through the repositories, it's an old version that doesn't recognize the Sony 350. Go to the website and download the latest version)
20 Run calibre
21 Click on "add book" and find the "my digital editions" folder (should be in your home folder)
22 Click "open" to import it
23 CTRL+D to get the metadata if it's not there already (on my machine the metadata doesn't import with the book it seems)
24 Plug in the Sony
25 Once detected in calibre, select the book and click "send to device"
26 When completed, eject and disconnect the device

---

### Post by Vincentlaborant on 2010-12-16
I just posted an how to manual [here]("http://www.facebook.com/home.php?#%21/notes/vincent-van-den-bergh/how-to-use-an-sony-prs-650-e-reader-in-ubuntu-1010/176957658990463") so the tricky business for the most  E readers is over now. Only Kindle DRM protected books are not working, but I am working to get that working properly as well.

---

### Post by Jazzy_Jeff on 2010-12-16
Just start downloading from torrent sites until they start supporting Linux :).

---

### Post by Connyank on 2010-12-18
> **Vincentlaborant said:**
> I just posted an how to manual [here]("http://www.facebook.com/home.php?#%21/notes/vincent-van-den-bergh/how-to-use-an-sony-prs-650-e-reader-in-ubuntu-1010/176957658990463") so the tricky business for the most  E readers is over now. Only Kindle DRM protected books are not working, but I am working to get that working properly as well.

Good to know Vincent but is there another venue other than facebook I can view that info?

Thanks,

jg

---

### Post by spegru on 2010-12-27
> **Vincentlaborant said:**
> I just posted an how to manual [here]("http://www.facebook.com/home.php?#%21/notes/vincent-van-den-bergh/how-to-use-an-sony-prs-650-e-reader-in-ubuntu-1010/176957658990463") so the tricky business for the most  E readers is over now. Only Kindle DRM protected books are not working, but I am working to get that working properly as well.
An important note to that guide that is important for DRM encumbered books.
The Sony Reader software that comes inside the device (PRS-350 in my case) did not run under wine. Although the Calibre ebook management package does run fine it cannot deal with DRM content unless the reader device is authorised, which it cannot do for you. 
It is only the Sony Reader software that can Authorise the device (not the PC, the reader device), not Adobe Digital Editions. So you need to run Sony Reader on a windows machine - just one time.
When you download a DRM book you get a download.acsm file (at least that is what it is called at waterstones). In windows, Sony Reader is the recommended choice to open it. Sony Reader gives the option to Authorise device (if it is not already). Once you have authorised the device you can download into it from Calibre on linux and DRM is ok

---

### Post by spegru on 2011-02-24
In fact I missed out a stage in my explanation.
After authorising the ereader device one time on windows you dont need windows anymore.
You need to install adobe digital editions using wine (as it's a windows app). Works perfectly, but you cannot download from adobe using a linux pc because it thinks it cannot work, but it's easy to find another download site and use that.   

When you install, it even appears as a desktop shortcut or from your menu.
Start it up and you get a very brown looking application space

When you do the download from waterstones you get a download.ascm file.Drag and drop that file into Digital Editions and it will do the download for you. You can even read the book within Digital Editions if you want.

To transfer to the ereader, use calibre. Start calibre & tell it where your library is. Then just plug in your ereader, select the book, right click and select transfer to device. Wait a few seconds and it's done!

Yes I know I duplicated what someone else wrote above, but for sure I hadn't realised what ADE was! Maybe mine is a little clearer?

---

### Post by Alessandro Pedarra on 2011-03-27
Is it possible to read books without touching a Windows machine?
I'm not interested in DRM protected books but I read in the manual that, in any case, one must run a Windows software at least one time to make the device working. That seem pretty absurd for a manufacturer to make a device Windows-bound.

I need a device that I just plug to mine Ubuntu machine from which I transfer mine books and begin to read immediately (just eBooks with watermarks or unprotected, not interested in Adobe). Is it like this or not?

Thanks

---

### Post by Iwneferi on 2011-05-12
> **Alessandro Pedarra said:**
> Is it possible to read books without touching a Windows machine?
I'm not interested in DRM protected books but I read in the manual that, in any case, one must run a Windows software at least one time to make the device working. That seem pretty absurd for a manufacturer to make a device Windows-bound.

I need a device that I just plug to mine Ubuntu machine from which I transfer mine books and begin to read immediately (just eBooks with watermarks or unprotected, not interested in Adobe). Is it like this or not?

Thanks

Yes it is. People make windows-bound devices all of the time. Apparently, linux users are a minority that many companies aren't interested in marketing to. But despite their lack of help we do just fine on our own. I have been using my PRS 600 (sony touch) for quite a while now and haven't touched a Windows machine in years. I just use calibre, but you don't even need that for basic book transfers and whatnot.

---

### Post by Alessandro Pedarra on 2011-05-13
Thanks, appreciated.

---

