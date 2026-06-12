---
title: "command line email client"
date: 2009-09-23
forum: General Help
---

### Post by Esthellin on 2009-09-23
Looking for a command line replacement for thunderbird. Thunderbird is good but too slow, plus I am wanting to be a Terminal junkie :D

Needed components:
IMAP/POP3 support.
Multiple accounts (settings for both server.in and server.out).
Fast.
TLS/SSL encryption.

I have looked at mutt and cone so far. Cone looks allright but I dont know how to get multiple "server.out" for the different mail accounts.
Mutt I had no luck with.

Any idea how nmh works?

EDIT: Starting to use cone. It is good. But I have no idea how to set up separate smtp servers for each account (if possible) because I have one IMAP account and one POP3 account. Also, how can you setup passwords for each account to be saved so you dont have to enter them everytime you open cone?

---

### Post by jonobr on 2009-09-24
Hello


Lot of people I know use mutt.

I dont use it myself.

Regarding command line, my definition on that would be using commands that an application would use to do the function required.

Eg to send email using command line.

telnet smtp.mail.com 25
helo mail.com
rcpt to:you@there.com
etc.....

Where as I think your more referring to an application that is text driven, such as mutt. Is that right?

Semantics I know, but Im feeling a little persnickety this morning.... :P

---

### Post by Lars Noodén on 2009-09-24
I can't give any command line recommendations.  mail is the only one I know of.  That would be in the package 'mailutils'

However, for text-based UIs, there are a few worth mentioning.  As mentioned by jonobr above, [Mutt](http://packages.ubuntu.com/jaunty/mutt) is widely used and highly thought of.

I know also people that use Emacs for mail.  Emacs does all kinds of stuff.  

Another to look at is [Alpine](http://packages.ubuntu.com/jaunty/alpine).  I'm a fan of Alpine.  

Nmh is ok, but I find difficult to use.  Exmh was probably the best client I've used as far as the UI goes, especially for working with multiple lists and multiple open messages, but Exmh is graphical.

---

### Post by ddrichardson on 2009-09-24
+1 Alpine. Been using it since Pine in 1994.

---

### Post by e24ohm on 2009-09-24
MUTT and PINE combind with PICO is great.

---

### Post by e24ohm on 2009-09-24
> **ddrichardson said:**
> +1 Alpine. Been using it since Pine in 1994.

Does PICO still come packaged with PINE?

---

### Post by ddrichardson on 2009-09-24
It looks like pico (nano) but this is on an Arch box and nano is in the core packages.

---

### Post by ddrichardson on 2009-09-24
Looking at Ubuntu's packages, it would be alpine-pico

---

### Post by openfly on 2009-09-24
mutt ftw!

---

### Post by Finalfantasykid on 2009-09-24
Linus Torvalds uses Pine \\:D/

---

### Post by Esthellin on 2009-09-24
In response to jonobr, I was thinking of more of the text-based mail client (like mutt and cone) that use ncurses (for instance) to have an interface within the terminal window.

I would use the command line type (sendanemail to@person) etc but I haven't found any good ones. 
Nmh installation crashed :(

My main concern is speed. Thunderbird took ages to get the mail and load everything up.
Cone so far is pretty good, but pretty slow.

I am going to try mutt this morning, and see how that goes.
EDIT:I loaded up mutt, but have no idea how to create the mailboxes. I need one for an IMAP account and one for a POP3 accocunt; no idea where to start

---

### Post by dcstar on 2009-09-25
> **Esthellin said:**
> In response to jonobr, I was thinking of more of the text-based mail client (like mutt and cone) that use ncurses (for instance) to have an interface within the terminal window.

I would use the command line type (sendanemail to@person) etc but I haven't found any good ones. 
.......

```
man mailx
```

---

### Post by abhilashm86 on 2009-09-25
mutt works superfast, it has IMAP support also.......

---

### Post by andrew.46 on 2009-09-25
Hi Esthellin,

> **Esthellin said:**
> In response to jonobr, I was thinking of more of the text-based mail client (like mutt and cone) that use ncurses (for instance) to have an interface within the terminal window.

If you want a headstart with mutt you could have a look at a guide I wrote a while back that deals with accessing gmail with mutt:

[Howto] Use Mutt with Gmail
[http://ubuntuforums.org/showthread.php?t=1021746](http://ubuntuforums.org/showthread.php?t=1021746)

A lot of the basics are covered there and it should certainly get you started with mutt, even if you don't plan on using gmail. An omission from this guide is IMAP, simply because I prefer the old ways :).

Andrew

---

### Post by Esthellin on 2009-10-09
You know how you can set the default mail reader (gnome-default-applications-properties)? How can this be switched to cone? 
As far as I know, cone (as the command) doesnt have an argument like thunderbird (eg thunderbird --compose).
I tried putting just "cone" into the line under custom for mail reader, but it still wants to try and find thunderbird (my previous email program).

---

### Post by Chronon on 2009-10-09
> **Finalfantasykid said:**
> Linus Torvalds uses Pine \\:D/

He opts for proprietary Pine over free Alpine?  Interesting.

---

### Post by stillious on 2009-10-09
> **Chronon said:**
> He opts for proprietary Pine over free Alpine?  Interesting.

No, he uses Alpine; from Wikipedia:-

*Linus Torvalds, the primary force behind the development of Linux, has stated in an interview published by the Lifehacker weblog on 31 January 2008 that he uses Alpine as his email client.[3] E-mail headers confirm this.[4]* :guitar:

---

### Post by CatKiller on 2009-10-09
Another vote for (AL)Pine.

---

### Post by Esthellin on 2010-03-17
Alpine WINS!

I finally managed to get Google Apps working with it. It is very good :)

Thanks everyone.

---

