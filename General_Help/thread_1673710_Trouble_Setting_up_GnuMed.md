---
title: "Trouble Setting up GnuMed"
date: 2011-01-22
forum: General Help
---

### Post by xaegis on 2011-01-22
I am using GnuMed from the reops and am unable to setup a working localhost postgresql server.
Can someone please talk me through this?

Thanks,

-e

---

### Post by j.r.busser on 2011-01-23
Hi!

A good general resource page is on the GNUmed wiki
	[http://wiki.gnumed.de/bin/view/Gnumed/GnumedManual](http://wiki.gnumed.de/bin/view/Gnumed/GnumedManual)

whose Administration section will indirectly take you to
	[http://wiki.gnumed.de/bin/view/Gnumed/ConfigurePostgreSQL](http://wiki.gnumed.de/bin/view/Gnumed/ConfigurePostgreSQL)

so if you care to give that a try & report any questions / trouble… :-)

-- Jim

---

### Post by xaegis on 2011-01-23
I have been trying to follow the tutorials on the wiki with no success. I apparently have not setup my localhost server and cant figure out what I did wrong.

---

### Post by j.r.busser on 2011-01-23
We might get more helpful suggestions if I post over at the devel list where, on account of SPAM, the list allows subscriber-only posting. However, if you post anyway, it will bounce to me and I can always then email you or you can look at the thread 

Trouble Setting up GnuMed - local postgres server

which should soon populate here

[http://lists.gnu.org/archive/html/gnumed-devel/2011-01/index.html](http://lists.gnu.org/archive/html/gnumed-devel/2011-01/index.html)

-- Jim

---

### Post by xaegis on 2011-01-23
apparently my client will only connect to _v14< and my system is running a _v12 and _v13 client. I am checking on how to update my backend to _v14 now. I will post on the list. Thanks!

:D

---

### Post by clockwork885 on 2011-01-23
Did you install GNUmed from the Canonical Repo's or GNUmed PPA? It is really worth using the PPA, in my experience.

---

### Post by xaegis on 2011-01-23
I installed from the repos but maybe I should reinstall and reinstall with the ppa.

---

### Post by xaegis on 2011-01-23
It appears I was already installed from the ppa. the client and server versions appear out of sync for the pre packaged (.deb) versions. I guess I'll just go with openEMR till development on the GNUMed advances a bit. I was able to get that running much more quickly and if I use prism it doesn't even look like a web app.
Ultimately I would love to use GNUMed but my I have been unable to find answers to my questions about HIPPA compliance and server setup. I tried to register on the site but there was some kind of error so I couldn't even do that properly. I will keep my eye on this piece of software but for now I have to go with something else in my practice.

Thanks everyone for the help!

-e:)

---

### Post by clockwork885 on 2011-01-23
Choose what works best for you, of course. I have been using GNUmed for a year or so now, and am very content with it. But I agree, the installation and setup did require more fiddeling than OpenEMR (for example). However, the developers are working very hard and when GNUmed is working, it is very solid. Did you subscribe to the developers mailinglist?

---

### Post by shilbert on 2011-01-23
For every client a specific database version is needed

Install from the PPA as per
[http://wiki.gnumed.de/bin/view/Gnumed/InstallerGuideHomeShort#ubuntu](http://wiki.gnumed.de/bin/view/Gnumed/InstallerGuideHomeShort#ubuntu)

You need client 9.8.5 and server 14.5

There are various log files which you can provide to aid in diagnosing.

bootstrap-latest.log 
and a bunch of client log files in .gnumed

If you cannot find them let us know so I can look up the exact locations.

1.) GNUmed has not been checked for HIPAA compliance.

2.) We would like to hear the exact problem that led to the installation problem. We have many successful reports from Ubuntu users and most of the time installation problems (due to postgresql and system configuration) lead to the misperception that GNUmed needs fiddeling.
You might want to check out the installation guide video and follow it to get a working GNUmed.

3.) Registration is disabled due to constant spam registrations. However all content is available without registration.

4.) If you are looking for a billing solution GNUmed might not be for you as it provides no billing whatsoever.

In any case please report any problems you have so we can improve the user experience.

I hope you have a better experience with openEMR.

---

### Post by xaegis on 2011-01-23
Nope, I will tho.:)

---

### Post by shilbert on 2011-01-23
gnumed --help
-----------------
GNUmed client launcher.

This is the launcher for the GNUmed GUI client. It takes
care of all the pre- and post-GUI runtime environment setup.

<snip>

--hipaa
 Enable HIPAA functionality which has user impact.                                                                   

</snip>                                                                                 
Hope this helps.

---

### Post by j.r.busser on 2011-01-23
> GNUmed has not been checked for HIPAA compliance.

It has not been externally evaluated (if that's what is meant above) however it does have minimum support, as hinted in the man page per

[INDENT][http://manpages.ubuntu.com/manpages/maverick/man1/gnumed.1.html](http://manpages.ubuntu.com/manpages/maverick/man1/gnumed.1.html)[/INDENT]

and the wiki

[INDENT][http://wiki.gnumed.de/bin/view/Gnumed/HipaaImplementation](http://wiki.gnumed.de/bin/view/Gnumed/HipaaImplementation)[/INDENT]

> Registration is disabled due to constant spam registrations. However all content is available without registration.

This disabling is in respect to the wiki… the mailing list, AFAIK, still allows new subscriptions.

> If you are looking for a billing solution GNUmed might not be for you as it provides no billing whatsoever.

	but external billing or accounting solutions, with minimum effort from a co-operative vendor, can allow the writing of a tiny file identifying the active-in-billing-program patient and this file can drive a "slave" instance of GNUmed to auto-navigate to the patient in GNUmed or (if the patient does not yet exist in GNUmed) facilitate creation of the patient.

---

