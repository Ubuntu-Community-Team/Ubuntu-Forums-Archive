---
title: "Beagle search doesn't even work?"
date: 2010-03-31
forum: General Help
---

### Post by kcredden on 2010-03-31
Folks: When I first came onto Ubuntu (Kubuntu 8.04.01) I had Beagle search working. I've upgraded to several versions of Ubuntu since then (I left KDE because of KDE 4), and since the upgrading , I've /never/ had Beagle working. I install it, turn on the daemon, and it /says/ it's running. But come back 24 hours later, and it still can't find files. Even ones I can see with Nautilus.

I just installed it again, and the same. I'm on Gnome/Ubuntu 9.10. I've been using Google search, but only because I can't use Beagle. 

I've read up on their site but I'm totally confused. So does anyone have specific things I can check and post here to see why it is, I can't get Beagle to work? 

Thanks
- Kc

---

### Post by HermanAB on 2010-03-31
Kill the mutt, don't let it suffer...

---

### Post by Ron_ on 2010-04-06
I agree that Beagle is profoundly flawed -- mostly because of an accumulation of problems that the community lacks the resources to address.  (See [http://mail.gnome.org/archives/dashboard-hackers/2009-September/thread.html](http://mail.gnome.org/archives/dashboard-hackers/2009-September/thread.html) .)

Beagle's advertised capabilities were a major factor in my decision to make the leap to Ubuntu last year.  I have never gotten it to work right.  This it is a source of daily frustration to me, based on my work needs.

On my Windows/Firefox/Thunderbird platform, I was accustomed to the capabilities of Copernic -- one stop shopping for indexes of files, e-mails and browsing history (assisted by Slogger.)  On Ubuntu, Beagle never indexed my Thunderbird mail content (only subject lines.)  It stopped indexing my Firefox activity inexplicably a month or so ago.

Canonical should fix it or replace it.

---

### Post by kcredden on 2010-04-06
Ron:

Thanks for the reply. I'm glad I'm not the only one that's had problems. This shows that at least it wasn't me, but there is just something wrong with it. Ok, I'm going back to Google search. 


> **Ron_ said:**
> I agree that Beagle is profoundly flawed -- mostly because of an accumulation of problems that the community lacks the resources to address.  (See [http://mail.gnome.org/archives/dashboard-hackers/2009-September/thread.html](http://mail.gnome.org/archives/dashboard-hackers/2009-September/thread.html) .)


---

### Post by Ron_ on 2010-04-30
The Beagle community (including Novell) seems unable to offer any further support.  Also, I found no evidence that Canonical has changed its support for desktop search apps since introducing Ubuntu 10.04 yesterday.  So after reviewing all of the information I could find comparing strengths and weaknesses, I shut down the Beagle daemon and installed Recoll.

So far, I am very pleased.  Documentation is good.  Installation was a snap.  Minor customization (e.g., setting a parm to enable Recoll to work with the Firefox Beagle add-on) was easy.  The whole conversion was very uneventful.  Creation of the initial index was reasonably fast (under an hour for about 250,000 files.)  The GUI is clean and clear.  All of the stuff that Beagle caught was there.  And all of the stuff that Beagle missed -- like Thunderbird message content -- showed up.

Compare Recoll news...

    * 2010-01-05 : a 1.13.04 is out. It fixes a nasty bug (broken stemming) in 1.13.02.
    * 2010-01-29 : the full Recoll source repository is now hosted on Bitbucket, along with a Wiki and an issues tracking system. Hopefully, this new channel for reporting bugs and make suggestions will increase the feedback rate...
    * 2010-01-05 : a 1.13.02 is out. It brings some nice improvements and new functions. Please try it and report any problems.
    * 2009-12-10 : 1.12.4 is out. It fixes a problem in the preview window search function (qt4 only).
    * 2008-05-22 : we now have a mailing list:
          o Subscription management
          o Archives

... to Beagle news:
21 Jan 2010      Beagle status: Beagle isn't in active development. It is getting some occasional maintenance done by Novell. 
26 Jan 2009      Beagle 0.3.9 released. 
15 July 2008      Beagle 0.3.8 released. 
7 Jun 2008      Added initial support for indexing removable medium. 
21 May 2008      Added read-only RDF overlay on Beagle index. This RDF store can handle RDF queries and supports different query formats like SPARQL, N3 etc. 
14 May 2008      Kio-beagle ported to KDE4. 

The future is Recoll.

---

