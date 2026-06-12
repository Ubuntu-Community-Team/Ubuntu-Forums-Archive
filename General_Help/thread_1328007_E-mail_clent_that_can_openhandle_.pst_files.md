---
title: "E-mail clent that can open/handle .pst files?"
date: 2009-11-16
forum: General Help
---

### Post by Raven2k360 on 2009-11-16
I did a forum search with a few different phrases, but can't seem to get any results.  My main question is this: is there an e-mail client for Linux that can open/manipulate/handle Office Outlook's .pst files?  I'd like to start using my .pst files again instead of living off of the mail server like I have for the past year or so, but I don't like the setup that Thunderbird uses (individual files for each subfolder) and don't want to hassle with importing/converting.  I find the .pst files to be the cleanest and easiest way to handle e-mail, especially if I want to copy/update the file between my desktop and laptop...just as simple as copy and paste/overwrite for the update.

As a sidenote, I do have MS Office 2007 installed with Crossover, and Outlook itself opens up, but when I try to setup my e-mail account, it times out when trying to connect to the server.  I read one post on here that mentioned that codeweavers haven't gotten the SSL porting to work or something, so I can't just use Outlook.

If anyone has any options for either fixing the issue with Outlook/cxoffice or knows of a linux-based e-mail client that will directly handle the .pst files, I'd appreciate the input.

Thanks!

Oh, and if it helps at all or makes any difference, I'm runnign Ubuntu Studio 9.04 on the desktop, and regular Ubuntu 9.10 on the laptop...both 64-bit.

---

### Post by JoelOl75 on 2009-11-16
I believe Thunderbird can import .pst files and convert them to .mbox

If this is no longer true look into [http://www.five-ten-sg.com/libpst/](http://www.five-ten-sg.com/libpst/)

This is a command line utility to take a .pst and make it .mbox

Also try googlin' convert .pst to .mbox  I know I had to do this many years back when I dumped Windows and I definatly accomplished this as I still have email from 2001 (Yepp... I save it all)

---

### Post by Raven2k360 on 2009-11-16
So is a .mbox file like a .pst in that all of your e-mail folders are contained within a single file?  Last time I checked the file structure in Thunderbird (granted, this was the windows version), it had a separate file fore each folder in the client just like Outlook Express uses. (example, inbox.xxx, outbox.xxx, deleted.xxx, etc.)

---

### Post by Raven2k360 on 2009-11-17
Bump...

---

### Post by emigrant on 2009-11-17
hope this helps:
[https://answers.launchpad.net/ubuntu/+source/evolution/+question/79615](https://answers.launchpad.net/ubuntu/+source/evolution/+question/79615)

---

### Post by Raven2k360 on 2009-11-17
> **emigrant said:**
> hope this helps:
[https://answers.launchpad.net/ubuntu/+source/evolution/+question/79615](https://answers.launchpad.net/ubuntu/+source/evolution/+question/79615)

I've seen those methods in other posts, I'd like to find a client that will open/manipulate the .pst file directly like Outlook does....or get Outlook to connect to my mail server with cxoffice.  Thanks for the input though.

---

### Post by sgage on 2009-11-17
Outlook 2007 (under Crossover) can be made to work with SSL connections by using stunnel. Works perfectly here. See the following:

[http://danielcolquitt.blogspot.com/2009/08/ssl-outlook-2007-crossover.html](http://danielcolquitt.blogspot.com/2009/08/ssl-outlook-2007-crossover.html)

---

### Post by Raven2k360 on 2009-11-29
> **sgage said:**
> Outlook 2007 (under Crossover) can be made to work with SSL connections by using stunnel. Works perfectly here. See the following:

[http://danielcolquitt.blogspot.com/2009/08/ssl-outlook-2007-crossover.html](http://danielcolquitt.blogspot.com/2009/08/ssl-outlook-2007-crossover.html)

I tried that, still can't get it to work.  When testing the connection when setting up the account, it times out.  I followed that tutorial to the letter, but it doesn't seem to work.

---

