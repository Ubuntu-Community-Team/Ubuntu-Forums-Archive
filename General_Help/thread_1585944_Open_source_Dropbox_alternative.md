---
title: "Open source Dropbox alternative?"
date: 2010-10-01
forum: General Help
---

### Post by mmickey on 2010-10-01
Hi folks,
 
I'm looking for an open source solution for mirroring some directories on a rented webspace (php, mysql, perl, python, ftp, no ssh). I'm working mostly on ubuntu, so it should have a simple integration like dropbox, set it up and forget, the chosen folders get mirrored automatically... A (php?) web interface on the server side would be very nice. Everything should be password protected, so no open access for others since some documents are private...

I sparkleshare seems do to some of it, but the server side is not clear to me and git hosters are no option. 
For local backup I use rsync, but it seems to be a problem with ftp and automatic integration (mirror on change not with cron).

Any ideas how to do this?

greets mike

---

### Post by andrewthomas on 2010-10-01
If you are used to Dropbox, why don't you just use it?

---

### Post by ean5533 on 2010-10-01
If you're only using Ubuntu, then I recommend using [Ubuntu One]("https://one.ubuntu.com/"). It integrates **exceptionally** well with Ubuntu (it's made by Canonical) and seems to cover all the features you listed.

You can find the install instructions [here]("https://one.ubuntu.com/support/installation/").

---

### Post by hrickh on 2010-10-01
> **ean5533 said:**
> If you're only using Ubuntu, then I recommend using [Ubuntu One]("https://one.ubuntu.com/"). It integrates **exceptionally** well with Ubuntu (it's made by Canonical) and seems to cover all the features you listed.

You can find the install instructions [here]("https://one.ubuntu.com/support/installation/").
He's looking for an open source solution, and the server side in definitely not open source.

R.
==

---

### Post by ean5533 on 2010-10-01
> **hrickh said:**
> He's looking for an open source solution, and the server side in definitely not open source.

R.
==

You're right, I misread his post. In that case, Sparkle is the only one I know about.

---

### Post by hrickh on 2010-10-01
This may be overkill (it involves the use of mono), but Novell released their iFolder platform as open source: 

[http://en.wikipedia.org/wiki/IFolder](http://en.wikipedia.org/wiki/IFolder)

R.
==

---

### Post by mmickey on 2010-10-01
Thank you.

But as far as I understand it, IFolder needs more on the server side than I got...

So I think it should somehow use FTP or it should work with a php interface on the server side and another one connecting from the client... I mean I can upload files with the web interface of my drupal installation... so the client e.g. needs to connect to those php methods used in drupal...

regards mickey

---

### Post by hrickh on 2010-10-01
> **mmickey said:**
> Thank you.

But as far as I understand it, IFolder needs more on the server side than I got...

So I think it should somehow use FTP or it should work with a php interface on the server side and another one connecting from the client... I mean I can upload files with the web interface of my drupal installation... so the client e.g. needs to connect to those php methods used in drupal...

regards mickey
Does you rented space include some sort of webdav service? If so, that would open up some options.

R.
==

---

### Post by mmickey on 2010-10-02
No it doesn't, although it's not cheap they are quite restrictive :-(

I guess a solution mainly has to build on php and ftp...

greets mike

---

### Post by directhex on 2010-10-02
There's SparkleShare. Not packaged yet, but it does what you want. Uses any git server for storing data.

---

### Post by SeijiSensei on 2010-10-02
> **mmickey said:**
> No it doesn't, although it's not cheap they are quite restrictive :-(

I guess a solution mainly has to build on php and ftp...

greets mike

I don't know how much you're paying for shared hosting, but for $20/month you can lease an entire 512MB Linux virtual host from [www.linode.com](www.linode.com).  Then you could use rsync or whatever you'd like for backups and run your webserver as well.

Disk space is the only limitation I've encountered so far.  If you're talking about archiving a few gigabytes of stuff this would work fine.  If you're talking about hundreds, then this isn't a solution for you.

Not affiliated with Linode; just a satisfied customer.

---

### Post by mmickey on 2010-10-02
Thank you, but it's 80 per year so this is too expensive.

How do I set up my own git server for sparkleshare, is this possible with just php and perl on a server? I tought it wasn't, so sparkleshare would not be a solution :-(

greets mike

---

