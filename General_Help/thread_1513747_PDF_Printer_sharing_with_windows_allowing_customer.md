---
title: "PDF Printer sharing with windows allowing customer location"
date: 2010-06-20
forum: General Help
---

### Post by rensell on 2010-06-20
Hi all. I'm very new to the world of Linux, and it has become my new hobby. I'm in the process of converting my was XP Pro "server" that was used for file and print sharing in my home into a xUbuntu file\print server using Samba. Some great software at my disposal and I'm loving the new learning...

Anyway, I've managed to jumped the many hurdles I've came across thanks to this forum and the all-mighty Google, however I'm have 2 primary issues right now and 1 leads me here. On my XP server, I have cutePDF writer installed as a shared printer and every computer on my network can use it to print anything to PDF, I've installed cups to share my printer and just installed cups-PDF and it works both server and client side, however I do not like a couple things and am hoping there is a setting I can change that I have not been able to find online.

1- It does not say if the job was completed successfully when printing something and it doesn't open the file when it does complete

2(MOST important) - It does not allow the user to specify the location to place the pdf, for instance using cutePDF the user "prints" whatever it is and a dialog pops up asking where to save the file, it "prints" and opens the PDF, very useful for saving them locally (on the client).

I've found ways to specify where to save all pdf using the conf file, and how to "print to file" while at the server.

If cups-pdf can not allow the user to specify the location, can anyone recommend another program that allows PDF printing and user specifications.

Thank you so much,

-RE

---

### Post by rensell on 2010-06-20
Anyone have any idea? I'd really like to get this setup completed and this is all I'm waiting on :)

---

### Post by pytheas22 on 2010-06-20
I can't offer you a really great answer, but here's a thought: could you perhaps create a file share between your various computers using samba and edit the CUPS configuration file to tell it to save the files there?  This wouldn't exactly save the file locally, but it would put it in a place where each local computer would have access to it.

---

### Post by rensell on 2010-06-21
That is true, and that is what is step up as of now, however I do not like it. Mostly because it's not as "user friendly" as we have been used to. I have to get this server running well at home before implementing a change in my work network. I'm hoping someone out there has some great software that can accomplish this that will wander over and let me know about it.

---

### Post by pytheas22 on 2010-06-21
I did some googling but couldn't find any software that does exactly what you're looking for.  The cups-pdf people [seem insistent]("https://bugs.launchpad.net/ubuntu/+source/cups-pdf/+bug/158406") that this is outside their purview, as their project is strictly a printer driver, not a GUI interface for printing (actually that seems reasonable).

Also, if you've tried Ubuntu desktop you probably noticed that the option to "Print to File" comes built-in, so for Linux users (or at least Gnome users) this is a non-issue--meaning that there's probably little interest in developing a feature like this.

You could try installing CutePDF using wine.  I have no idea whether it would work at all (printing-related stuff in wine is usually tricky), and the [wine database]("http://wiki.winehq.org/PDF") lists it as untested, but it wouldn't hurt to try.

---

### Post by rensell on 2010-06-21
I understand what you are saying, and it is somewhat of a shame that a "gui" won't be created for something like this. CUPS-PDF is a create "printer" but with homer servers rising in popularity, PDF printer as I'm searching for would be a HUGE benefit. If they didn't think so, the cups-pdf wouldn't have been create. I'm not being disrespectful, I'm just saying I think it would be worthwhile to be created for installing on any type of server. I know in my house online shopping receipts, online bill payments, etc. are using all my ink and paper and I use cute-pdf on my laptop and XP server, but the other's don't use it, but if I could implement it in Linux, they'd not have a choice lol

Thanks again for your input.

-R

---

