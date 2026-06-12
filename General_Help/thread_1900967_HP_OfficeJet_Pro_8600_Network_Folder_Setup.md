---
title: "HP OfficeJet Pro 8600 Network Folder Setup"
date: 2011-12-27
forum: General Help
---

### Post by SyntheticShield on 2011-12-27
I hope I put this in the right place, I didnt see forum section that dealt with printing specifically.

I just bought an HP OfficeJet Pro 8600 Multi-Function printer.  I was trying to set up the Network folder access so I could copy and scan directly to the folder.  However, the set up process is geared towards Windows of course and Ive been unable to find any info on how to set this up under linux, specifically Ubuntu or Xubuntu.

It seems the network path isnt working but Im not sure how to format it.  Ive tried \\home\me\my\path\to\folder and Ive also tried \\IP Address\home\me\my\path\to\folder but neither is working.

If anyone has any ideas I would appreciate the input.

---

### Post by SyntheticShield on 2012-01-30
Well, its been a month, so I thought I would bump this up and see if anyone had any new information.

---

### Post by phylae on 2012-02-17
You need to set up your computer as a samba (aka cifs) server. That protocol is compatible (enough) with windows file sharing that your printer will be able to talk to it.

This is a starting point: [https://help.ubuntu.com/11.04/serverguide/C/samba-fileserver.html](https://help.ubuntu.com/11.04/serverguide/C/samba-fileserver.html)

Once that is set up, then the format of \\IP Address\sharename\some\path\to\folder should work, except that instead of being relative to your system's root, it will be relative to the "share" (which in my example was "sharename").

I'm no expert, but I hope that's enough to get you going.

---

### Post by SyntheticShield on 2012-02-17
Its funny you should post your reply when you did.  I literally, just last night got this all figured out after all this time.  What, six weeks or something like there.

I have scoured the internet trying to find some tidbit of information in order to make this work.  Even HP's own how to on the matter was not good and wrote for Ubuntu 8.04 if I remember correctly.  And this post in such a large commmunity of users is probably more evidence of the lack of information out there.

At any rate, I did get it figured out and below is what I did for the sake of anyone else that may run across this issue.

First, I had to download HPLIP as there is no native support in Ubuntu for the OfficeJet 8600.  The current version is 3.12.2.  The install instructions that HP provides for the installation is very good and accurate.  And let me digress for a moment to say thank you to HP for supporting the Linux community.  I have not used any of their products for many many years because they refused for so long to go to individual ink cartridges.  When I found they had done so in the OJ 8600 and were so compatible with Linux I finally abandoned Canon which was not.

Anyway.  Once you have HPLIP installed and working and your printers set up you are ready to set up the Network scanning.  Now, you also need to be aware that if you install HPLIP, not only do you have to set printer settings there, but it seems you have to also set printer settings in System > Printing, as they do not carry over.  Im not 100% sure but I think that was part of the issue I had initially with duplex printing.  Just something to keep in mind.

Now, in your home directory (or wherever you wish, though my steps are based on creating a folder in the Home directory.  And of course I am using Xubuntu, so things may be slightly different.  For this example, I made a folder called 'ScanDocs'.

Once that is done, right click on folder and select the properties tab.  You HAVE to give 'Other' Read & Write permission.

Open up the printers web interface by going to the IP address for your printer.  Click on the Scan tab and then select Network Folder Setup.

Once there click on New for the Network Folder List

Give your folder a display name.  This is what you will see on the Printer display panel when selecting the folder to scan to.

Now, here is the kicker.  HP's instructions say you have to format the address to the network foder like this:

\\Printer IP Address\Path\To\Folder

I tried every concievable combination.  I had SAMBA installed and everything set correctly because I could access the folder everywhere else EXCEPT from the blasted printer/scanner.  I tried every suggestion I could find for folder sharing in Xubuntu/Ubuntu and nothing worked.  So I then though well let me set up Win 7 Ultimate in a VB environment, install the actual HP drivers from the provided CD and see if I can get it to work there.  Why it took me so long to try that is beyond me.

Even after all that, I STILL could not access a folder either in the Windows environment using either a folder in windows itself or a folder on Xubuntu, even when I followed the HP Wizard.  But it was then I realized where the major mistake was.  When I used the HP Windows set up Wizard for access to a Network Folder it was not using the IP address of the Printer or even the computer that the folder was on.  It was, instead, using the computer name.  Why it could not resolve to that Im not sure, but that was apparently the hang up.  The other difference is that in Windows you have to authenticate (at least in the test I did I had to) to access the folder, in Linux you apparently do not.

So after all that I found that the format for the path to the network folder is actually:

\\PC Name\Path\To\Folder

Again, working from Xubuntu, using the example ScanDocs as the folder name and a PC Name of Xubuntu-01, this is how the path would be formatted:

\\Xubuntu-01\ScanDocs

Now, of course, if you bury the folder deeper into the file directory then your path will be different, but using the machine name gives you sight to the home directory on Xubuntu.  Once that was done the rest was simple.  Continuing on with the process.

Once you have entered in the path to the folder you can move to the next step, you do not need to enter Username or Password for Xubuntu so click on Next

You are next faced with the option to enter in a PIN to prevent unauthorized scanning to the folder.  I skipped it and clicked on Next.

The next step is the set up of the Scan Settings you want to use.  Set everything as you would like it to be.  Dont worry, you can change them later if they are not what you would like.  Click on Next.

The next screen is a summary of everything.  Make sure it is correct and then you click on Save and Test.  That will test access to the folder and make sure it can get to it and then finalize the set up.  Click OK when it gives you the message that the test has completed successfully.

You will be taken back to the starting screen and you will notice on the right hand side a link to 'edit' your settings if the need should arise.  This is where you can go back and change your scan settings or the whole set up if you like.

Now, you can insert a document to be scanned in the document feeder on top of the printer and from the control panel on the printer select Scan, then Select Network Folder and then you should see the folder you just set up.  You can set up multiple ones if you like.  Select the folder you want to scan to.  You will then see a screen where you can set scan settings and a filename.  Once you have everything as you like, just touch scan.

I went through all this for no other reason than to learn how to do it, then to be able to share the information but also because scanning this way produces, to me, a much cleaner scan than manually laying it on the scan bed and using the Simple Scan interface.  It works, but its just not as good to me.  You do loose the ability to scan single pages at a time and scan them to a single document like Simple Scan gives you the option to do, but I can deal with that for now.  You can feed multiple pages, but not stop and flip over if the page that you are scanning is double-sided.

Once you have scanned a document, check your folder and you will see it there.  The only other drawback is that setting the filename from the printer control panel is a bit of a convuluted mess and not particularly easy to do.  So I just rename them from the folder and use the default, set up scan name.  Virtually every document that comes into my house is digitized so I end up with some long file names to keep everything easy to identify and its just easier to rename them for my purposes.

I guess I will eventually have to look into some kind of utility that can join multiple pdf's together at some point.

There you go, thats how you set up Network Scanning in Xubuntu for the HP OfficeJet 8600 (N11a).  I hope this saves someone all the frustration I went through.

---

### Post by phylae on 2012-02-17
> **SyntheticShield said:**
> You do loose the ability to scan single pages at a time and scan them to a single document

I have "scan to network" set up on my HP Officejet Pro 8600, and I am able to scan single pages at at time into a single file. After each page, it asks me if there is another page, and I select "Yes".

If you provide some more details, I may be able to help troubleshoot.

---

### Post by SyntheticShield on 2012-02-17
O Really!!  Well you just became my new best friend, LOL

What information do you need?  Im going to the scanner right now so I can run some pages through it to see what if any messages are displayed.  But I cannot recall seeing any nor anything asking if I wanted to scan another page.

---

### Post by SyntheticShield on 2012-02-17
Okay, I just checked and it definitely does not ask if I want to scan another page.  It simply tells me how many pages it scanned and saves it.  Now it should also be mentioned that I have not been able to get the 'Scan to Computer' function to work.  It keeps telling me:

You cannot use this function because it has been disabled. For more information, contact your network administrator or the person who set up the printer.

For the life of me I cannot find out where the setting is to enable it.  I only have the Scan to Network Folder set up at this time.

---

### Post by phylae on 2012-02-17
> **SyntheticShield said:**
> Now it should also be mentioned that I have not been able to get the 'Scan to Computer' function to work.  It keeps telling me:

You cannot use this function because it has been disabled. For more information, contact your network administrator or the person who set up the printer.

For the life of me I cannot find out where the setting is to enable it.  I only have the Scan to Network Folder set up at this time.

Scan to Computer requires a special HP utility to be running on the computer you are going to scan to. AFAIK HP only offers a Windows (and possibly Mac) version of this. You may be able to use this in a virtual machine, but I found it too much effort to figure it out.

To be clear, I am using the "flatbed" part of the scanner. I'm NOT using the paper feeder.

I'm also assuming you have already set up scan to network using the web UI of the device. (i.e. visit "http://<ip of printer>" and click "scan" and click "network folder setup")

Can you tell me exactly which buttons you are pressing? I use the following:
* Scan | Network folder | <name I chose in network folder setup>
* click "Start Scan"

---

### Post by SyntheticShield on 2012-02-17
I am using the ADF to scan, but am using the same buttons as you are; Scan > Network Folder > Folder name, then hit scan.

---

### Post by SyntheticShield on 2012-02-17
Okay, nevermind.  When I scan from the flatbed rather than feed it throught the ADF, it does ask me if I have another page to scan.

Well crap, I much prefer the cleaness of the scans from the ADF than I do from manually putting it on the scanner bed.

---

### Post by phylae on 2012-02-17
Yeah. I just checked the ADF, and I'm getting the same behaviour as you are. I guess HP just assumes that if you are using the ADF you'll put all your papers in at once. But that doesn't work if you have different sized things to scan.

---

### Post by SyntheticShield on 2012-02-17
Agreed.  It also doesnt work if what you are scanning is already double sided.  I would have been nice, I suppose, to have a duplexer for the ADF as well.  Oh well.

I want to take a moment, though, to thank you for your help and trying to help.  It is very much appreciated.

---

### Post by phylae on 2012-02-17
> **SyntheticShield said:**
> I would have been nice, I suppose, to have a duplexer for the ADF as well.

I think that one of the next models up has this feature. I remember reading about some "two-sided scan" feature. But I'm pretty sure my device can't do that.

---

### Post by SyntheticShield on 2012-02-17
I will have to wait for Black Friday this year I guess to get that then.  I love this printer it just seems they did not think some things through or either I am one of the weird ones that comes up with whacky ways to use things that were never intended, LOL.

I have a Canon USB flatbed scanner as well that works, and of course the flatbed on the printer, but I just love the way the ADF on the printer gets everything perfectly placed and scans so much nicer.  I guess I will have to toss my anal tendencies aside and just deal with it.

---

### Post by SyntheticShield on 2012-02-18
> **phylae said:**
> I think that one of the next models up has this feature. I remember reading about some "two-sided scan" feature. But I'm pretty sure my device can't do that.

phylae, I thought I would come back and post up I discovered something for the ADF scans.  I set the filename to be at the time of scan to be the name 'scan_'.  When the first document is scanned it is saved as scan_.pdf.  Well I scanned a single sided document that got twisted some during the scan process, so instead of deleting the scanned file I just left it to be overwritten.  When I scanned the document again it saved it as scan_0001.pdf.  So just to confirm I ran it through again and it saved it as scan_0002.pdf.  So it seems that if you scan separate pages, one at a time, rather than running several pages of a document through at one time, it will save it using incrementing numbers.  Which is perfect because I found a program called pdfsam that will effortlessly stitch them all together in one document.

So, it ends up being little different than manually putting them on the scan bed and telling it repeatedly that I have another document to scan and I still get the nice clean scans.  I just have the added, yet relatively quick step of stitching them back together.

Hope this helps in some way.

---

### Post by phylae on 2012-02-18
> **SyntheticShield said:**
> When I scanned the document again it saved it as scan_0001.pdf.  So just to confirm I ran it through again and it saved it as scan_0002.pdf.  So it seems that if you scan separate pages, one at a time, rather than running several pages of a document through at one time, it will save it using incrementing numbers.

Oops. I guess I misunderstood your previous post. I could have told you that was its behaviour. In fact, it doesn't matter how many pages you put in the ADF. If you put in 3 pages and press "scan", then you will get scan.pdf with three pages. Then if you put in 4 pages and press "scan", you will get a new file called scan_0001.pdf that has 4 pages. It will just keep incrementing that number. It will never overwrite a file, regardless of the number of pages in that file.

In fact, I have never edited the name using the web UI. I just throw all my scans into the same directory and let the device worry about the names. I just copy/move the files I care about and rename them using Nautilus.

---

