---
title: "Request for comments, suggestions and advice"
date: 2010-07-17
forum: General Help
---

### Post by ptolemytoo on 2010-07-17
Greeting to all.

I have a hardware and software project in mind and would be grateful for any advice and suggestions. It is a personal project which I have been mulling over for years and, now that I have retired, can finally tackle.

Be warned this is going to be a long letter. 

First a bit of background. I have worked in IT since the mid eighties. I'm old enough to have worked in the punch card era but only really got into IT with the arrival of DOS. Most of my working life has been spent working on the UNIX platform but almost always used a Windows PC to access the UNIX back end. I have written a lot of shell scripts, worked in Perl and a bit of PHP and also Oracle and DB2; even Kermit. However in the last 10 or so years of my working life I have written almost no code having been in an administrative position. After 15 years in the USA, I'm back in my native South Africa to enjoy the sunshine and wide open spaces in my golden years.

So now to the project: I think of it as an attempt to create an integrated information and multimedia solution for my home, including security and some home automation. Ubuntu will play a large part.

The hardware part of the project:
My living space consists 3 bedrooms plus the usual lounge/dining/kitchen/bathrooms etc. One bedroom serves as my study and will be the nerve centre of the house. There is also an outdoor space and garage and outbuildings. The objective is to wire the whole house for Ethernet, TV and telephone connectivity. No problem there. Now this is what I would like to implement on the hardware side.
1. Switch from Windows XP Pro to a Mac as my main workstation
2. A Linux based information server for my various databases etc. Details discussed below.
3. Linux based multimedia storage machine to serve the whole house.
4. Security and home automation machine to which are connected 4 security cameras and other sensors.
5. A multimedia computer each for both the living room and the master bedroom.
6. A machine onto which to backup all data.

What I currently have on the hardware side is: 
* An Intel Core Duo 1.8Ghz machine with 2GB RAM, running Windows XP Pro. 
* An old Dell PII 400Mhz, with 512MB running Ubuntu 7.04 Feisty Fawn server edition running headlessly in text only mode. 
* A P4 machine with 512 MB RAM to serve as the security server. This was recently acquired but not yet connected to the LAN.
* I used to have a newish Dell laptop but that was stolen. Occasionaly I use my old Compaq Armada laptop, running Windows 98 with a Netgear WiFi card.
* A Telkom (local telephone monopoly in South Africa) ADSL Modem, router and WiFi access point combination device.


Now for the good stuff. Software.

Software project # 1. -- Although I have mostly used Windows for email and various incarnations of Office over the years, I have always maintained a private UNIX shell account until the company that provided that service in the US was taken over (again) and finally decided to shut down its shell accounts. I used this as a central place to store my personal mail and used Pine to access it on occasion. I mention this because in this shell account I had accumulated close to a GB of email, including attachments, in mbox format. This mail is organised in multiple folders, which as many of you will know are essentially text files; one file per folder. These files are now located on my Ubuntu server and accessed via PuTTY and Alpine, when I want to search for an old piece of email.

What I would like to do is store all this mail in a MySQL database. To that end, I need to go through every mbox file/folder, separating it into individual messages and then break each message into its constituent parts. Then store each message in the database. Question: After I have done this on the old email, what should I do about new mail? Should I try and store new mail directly into the database or should I just run the script again, perhaps on a cron job once a week. I also have Outlook mail on my PC which I need to get into mbox format. I might switch to Thunderbird as part of my transition to the Mac, I believe it will convert Outlook mail to mbox. Any suggestions would be welcome. Eventually, I would like all the mail to live on the server, with current mail, mail not in the database, being synchronised onto a future MacBook.

There are many Perl modules in CPAN to work with email and database interfaces. I have a few questions. Does anybody know of an existing Perl script that will do the above? What should I do with the attachments? Should I separate them out into their own field or just store them with the rest of the body of the message in a large text field? On retrieval of a message or messages-using PHP and a browser-will the re-encoding of a binary attachment happen immediately after the SQL query or as a separate process once the listed attachment is clicked on?

That is my vision of the email project. Alternative viewpoints and solutions are gladly received as well as pointers towards existing software and even snippets of code, should it be offered.

Software Project # 2. I collect articles and information on various subjects. I have been doing this for a long time and now have an enormous number of files in various formats stored mostly in my My Documents folder in my Windows machine. Recently, I have started saving them in PDF format using Adobe Acrobat 6.0 Pro. But there are many in MHT format which can only be opened in Internet Explorer as well as Word and Excel files, besides text files. Ultimately I will convert them all into PDF except those which need to be edited or changed. I have been looking into the possibility of storing my many individual files as blobs in a database. Any suggestions and comment on this? Is this a good idea? If implemented, how will I deal with Word files on my Mac OS X machine? Should I attempt to write my own solution, or try and use an open source document management application like Knowledge Tree? It seems as if most such apps are vastly more complex than I need. I don't need to allow multiple user access or different tiers of permissions. On the other hand, I may permit a few select individuals, who share my interests, to access these files via a web connection. Which of course opens up all sorts of security issues. But I will leave that for another day. Comments, suggestions and advice gratefully received.

Software Project # 3. This is more of a fun project than a burning need. I have a large names and address list, some of it in comma delimited format and more in Outlook Contacts. Ultimately, I would like to write a Mac application as well as a web interface for access to this data. My idea is to have this information readily at hand while I am at my main workstation, my Mac. I thought I might learn Python now that I have the time to do whatever takes my fancy and like the idea of writing a Python app to access a SQLite backend on my Ubuntu server. Because it should be lighting fast, I have been looking at the notion of using tmpfs a virtual memory file system to keep the whole database in memory, as it were. The entire database is likely to be less than 200MB. Or I could write the front end in AppleScript. Let me hasten to add that as of this writing, I have no knowledge to speak of Python or Applescript. Alternative ideas eagerly anticipated.

Software Project # 4. My security machine is equipped with a 4 channel 10 bit DVR card. The 4 cameras that connect to it can be accessed via bundled Windows software. If possible, I would like to convert it to Linux and use ZoneMinder but I have not been able to find any Linux drivers for the card. The card is made by: SecuEasy Electronic Co. Ltd, The box lists the cards as DVR Video Surveillance System, model SR-9104B. If anybody has any knowledge of this card and knows of a Linux driver for it, I would be most grateful. 

Two subjects that combine both hardware and software. I need to keep some limited windows access. One of the prime reasons is so that I can continue to use Mapsource to plan my motorcycle trips into the hinterland and then upload the route to my Garmin GPS. The Mapsource/Garmin gdb file is the format of choice for all my fellow adventurers. I would like to convert my current PC to a media storage machine running Linux, it has a terabyte drive, and then install a virtual machine to run Windows XP in. Do you think it would be up to the task and should I add more RAM? And can I then access Windows from my Mac via Windows Terminal Services? The question arises, where will I plug in my GPS? Will Mapsource be able to recognise it if it is plugged into the Mac via usb? Or would it be better to run Parallels virtual machine directly on the Mac. Would prefer not to use up Mac resources.

Does anybody have an comments on MythBuntu as compared to plain MythTV. Will acquire appropriate hardware. Does anybody in Cape Town, have a functional system up and running?

Finally, I have an out building which I want to use to house a backup server. That means if the whole house burns down, the data will be safe. Any suggestions for a solution? I think I may have read about specialised distros for this. Anybody have comments regarding FreeNAS?

Thanks in advance.

Regards,

Harry.

---

