---
title: "Outlook"
date: 2012-03-27
forum: General Help
---

### Post by Billy Ng on 2012-03-27
Here's the deal.  I currently use Windows 7 at work but would love to move completely over to Linux for a few reasons, the best of which being the fact that our actual production environment and product is 100% linux based including the GTK-based GUIs.

The reason I'm on Windows is for a few key pieces of software that I essentially can't do without:

[LIST]
[*]Outlook
[*]Internet Explorer
[/LIST]

Our company has almost 1000 employees, all using Windows, and we are very heavily integrated with Outlook.  Calendar, Mail, Contacts, Shared Folders .... I cannot use a POP or IMAP based equivalent, I need something that either fully integrates with MS Exchange/Outlook Server or I need to run Outlook directly.

All Intranet sites are coded to IE only and while I detest IE with a passion (I tend to run Chrome everywhere), there are web-based tools I need to run to do my job and I've tried these tools in other browsers (Firefox, Chrome) without success.  So I'll need IE to render these properly and run the correct Active-X controls.

I've run Linux as my desktop at work before, and the way I previously did it was to use VBox to run IE and Outlook - but there were drawbacks to that arrangement.  Since they were both in the same VM, I couldn't separate them out onto different screens for instance.

First - is there an equivalent to Outlook out there that fully integrates with Exchange the way I'd like it to?   If not, what options do I have for running Outlook natively (Ubuntu 11.10)?

---

### Post by Frogs Hair on 2012-03-27
I currently use a similar setup for collage . I can access Exchange and send mail via online login . I don't know of any way to install as client on Ubuntu except V Box or possibly Wine . I have not found  any compatible equivalent for Linux , but I dual boot so it has not been a priority .

---

### Post by dcstar on 2012-03-27
> **Billy Ng said:**
> 
..........
First - is there an equivalent to Outlook out there that fully integrates with Exchange the way I'd like it to? 

Evolution with the current MAPI plugin or the new OWS plugin can do most of what Outlook does.

The OWS plugin should be available after 12.04 is released.

---

### Post by solocommand on 2012-03-27
Watching this to see if anything comes of it...I tried using evolution for exchange access in 11.10, but wasn't able to get contacts/calendars working correctly. Everything I read about running IE under wine made my skin crawl, so I decided against it.

My second partition contains my Win7 environment, so I cloned that and run it as a VM under virtualbox when I need access to MSSQL workstation, Outlook, or IE.

I'd like to have a full featured email client running natively, but havent found anything that works quite as well yet. Dunno if a VM is an option for you, but it's working alright for me in the meantime.

Cheers!

---

### Post by mastablasta on 2012-03-28
>  
the fact that our actual production environment and product is 100% linux based including the GTK-based GUIs.



 
Then why are you using windows on all computers?

---

### Post by dcstar on 2012-03-28
> **Billy Ng said:**
> Here's the deal.  I currently use Windows 7 at work but would love to move completely over to Linux for a few reasons, the best of which being the fact that our actual production environment and product is 100% linux based including the GTK-based GUIs.
.........
First - is there an equivalent to Outlook out there that fully integrates with Exchange the way I'd like it to?   If not, what options do I have for running Outlook natively (Ubuntu 11.10)?

Actually Outlook Web Access still has most of the functionality of the Outlook client now, so simply running that in Firefox will probably do 98% of what most people need.

---

### Post by Mark Phelps on 2012-03-28
Just so you know -- IE doesn't work well in Wine, either.  Recently, an article raved on about CrossOver Linux and how it installed IE -- but in the FINE PRINT, you could see it was version SEVEN!

Most Windows shops use IE 9 these days -- and Win8 is being based off IE 10.

So, if folks ask about using IE under Linux, like Outlook it is basically a no go.

---

### Post by collisionystm on 2012-03-28
> **Billy Ng said:**
> Here's the deal.  I currently use Windows 7 at work but would love to move completely over to Linux for a few reasons, the best of which being the fact that our actual production environment and product is 100% linux based including the GTK-based GUIs.

The reason I'm on Windows is for a few key pieces of software that I essentially can't do without:

[LIST]
[*]Outlook
[*]Internet Explorer
[/LIST]

Our company has almost 1000 employees, all using Windows, and we are very heavily integrated with Outlook.  Calendar, Mail, Contacts, Shared Folders .... I cannot use a POP or IMAP based equivalent, I need something that either fully integrates with MS Exchange/Outlook Server or I need to run Outlook directly.

All Intranet sites are coded to IE only and while I detest IE with a passion (I tend to run Chrome everywhere), there are web-based tools I need to run to do my job and I've tried these tools in other browsers (Firefox, Chrome) without success.  So I'll need IE to render these properly and run the correct Active-X controls.

I've run Linux as my desktop at work before, and the way I previously did it was to use VBox to run IE and Outlook - but there were drawbacks to that arrangement.  Since they were both in the same VM, I couldn't separate them out onto different screens for instance.

First - is there an equivalent to Outlook out there that fully integrates with Exchange the way I'd like it to?   If not, what options do I have for running Outlook natively (Ubuntu 11.10)?


Sounds like the problem I had at my old job.

You either 
A) Run Windows and use something like mRemote to access your servers.
B) Run Linux, but use Vmware Player because it can do a drag and drop function instead of a shared folder between host and vm.

---

### Post by Billy Ng on 2012-03-28
> **mastablasta said:**
> Then why are you using windows on all computers?

Because that's how desktop system's work in the real world.  We have accountants, lawyers, secretaries, managers, business people, software developers ... all people that have a much better time working with MS Office, Outlook, Blackberrys, and know Windows from previous jobs and environments.

Most of the in-house systems here are Windows based, it's only our product that is fully Linux based and only our small team of 8 people (there are 800+ in the company) along with a few of our users actually use Linux.  And even then, no one needs Linux as a desktop.  Our product isn't GUI-based.  99% of the time our team or our users simply ssh's to server, greps through some logs or vim's some configs, maybe we setup a few crons .... we're done.

Windows still rules as a corporate OS in a company filled with a standard allotment of non-geek people.  If we were a software shop whose only products were Linux based, that would be one thing - we're not.

---

### Post by collisionystm on 2012-03-29
> **Billy Ng said:**
> Because that's how desktop system's work in the real world.  We have accountants, lawyers, secretaries, managers, business people, software developers ... all people that have a much better time working with MS Office, Outlook, Blackberrys, and know Windows from previous jobs and environments.

Most of the in-house systems here are Windows based, it's only our product that is fully Linux based and only our small team of 8 people (there are 800+ in the company) along with a few of our users actually use Linux.  And even then, no one needs Linux as a desktop.  Our product isn't GUI-based.  99% of the time our team or our users simply ssh's to server, greps through some logs or vim's some configs, maybe we setup a few crons .... we're done.

Windows still rules as a corporate OS in a company filled with a standard allotment of non-geek people.  If we were a software shop whose only products were Linux based, that would be one thing - we're not.

Well said.

---

### Post by dcstar on 2012-03-30
> **Billy Ng said:**
> Because that's how desktop system's work in the real world.
.........

Your original post misled people into believing that you wanted a Linux Desktop for ALL 1000 people. That is (probably) why that question was asked.

---

### Post by Billy Ng on 2012-03-30
Ah, I see.  I don't read it that way since I used "I" everywhere, but I can see the confusion.

---

