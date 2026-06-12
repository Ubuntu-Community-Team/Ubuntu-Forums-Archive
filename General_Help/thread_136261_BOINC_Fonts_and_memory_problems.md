---
title: "BOINC Fonts and memory problems"
date: 2006-02-25
forum: General Help
---

### Post by kseise on 2006-02-25
I get the following error messages while trying to run a BOINC session on a fresh install of Breezy and BOINC.
> Sat 25 Feb 2006 03:43:50 PM EST||Starting BOINC client version 5.2.13 for i686-pc-linux-gnu
Sat 25 Feb 2006 03:43:50 PM EST||libcurl/7.14.0 OpenSSL/0.9.8 zlib/1.2.3
Sat 25 Feb 2006 03:43:50 PM EST||Data directory: /home/kseise/Desktop/BOINC
Sat 25 Feb 2006 03:43:50 PM EST||Processor: 1 AuthenticAMD AMD Sempron(tm) 2300+
Sat 25 Feb 2006 03:43:50 PM EST||Memory: 1.48 GB physical, 1.54 GB virtual
Sat 25 Feb 2006 03:43:50 PM EST||Disk: 35.17 GB total, 30.60 GB free
Sat 25 Feb 2006 03:43:50 PM EST|rosetta@home|Computer ID: 169429; location: home; project prefs: default
Sat 25 Feb 2006 03:43:50 PM EST||No general preferences found - using BOINC defaults
Sat 25 Feb 2006 03:43:50 PM EST||Remote control not allowed; using loopback address
Sat 25 Feb 2006 03:44:41 PM EST|rosetta@home|Resetting project
Sat 25 Feb 2006 03:44:41 PM EST||request_reschedule_cpus: exit_tasks
Sat 25 Feb 2006 03:44:41 PM EST||request_reschedule_cpus: project op
Sat 25 Feb 2006 03:46:53 PM EST|rosetta@home|Sending scheduler request to [http://boinc.bakerlab.org/rosetta_cgi/cgi](http://boinc.bakerlab.org/rosetta_cgi/cgi)
Sat 25 Feb 2006 03:46:53 PM EST|rosetta@home|Reason: To fetch work
Sat 25 Feb 2006 03:46:53 PM EST|rosetta@home|Requesting 8640 seconds of new work
Sat 25 Feb 2006 03:46:58 PM EST|rosetta@home|Scheduler request to [http://boinc.bakerlab.org/rosetta_cgi/cgi](http://boinc.bakerlab.org/rosetta_cgi/cgi) succeeded
Sat 25 Feb 2006 03:46:58 PM EST|rosetta@home|Message from server: No work sent
Sat 25 Feb 2006 03:46:58 PM EST|rosetta@home|Message from server: (there was work but you don't have enough disk space allocated)
Sat 25 Feb 2006 03:46:58 PM EST|rosetta@home|Message from server: Not enough disk space (only 100.0 MB free for BOINC). Review preferences for minimum disk free space allowed.
Sat 25 Feb 2006 03:46:58 PM EST|rosetta@home|No work from project


I also can't connect through the manager to the BOINC websites. It tells me that > 
BOINC could not determine what your default browser is.  Please verify thatyou have either the 'mailcap' package installed or 'mime' packag installed, aand that the texthtml mime type is  configured foryour favorite browser


The other problem is that the fonts are not correclty registered.  I can't find the file to change the font.  Can anyone help me?

---

### Post by dcstar on 2006-02-25
[QUOTE=kseise]I get the following error messages while trying to run a BOINC session on a fresh install of Breezy and BOINC.


I also can't connect through the manager to the BOINC websites. It tells me that 

The other problem is that the fonts are not correclty registered.  I can't find the file to change the font.  Can anyone help me?[/QUOTE]
Firstly, they are **not** error messages, they are information messages.

As far as the Boinc manager goes, it depends on the version you have installed, if it is an old version then it may not work that well (or at all).

---

### Post by xtacocorex on 2006-02-25
It did say that you don't have enough disk space allocated to store the files that are downloaded for BOINC, so you might think about changing that.

I don't remember how to change the disk space usage, but I'm sure the BOINC site has info on that.

---

### Post by kseise on 2006-02-26
Sorry, they were in red, so I assumed that meant an error message.  After soem additional snooping, I found that I had to add the line:

> BROWSER=/usr/bin/firefox; export BROWSER

To the run_manager file.  That seemed to fix my "error messages" and let me connect to a project and it also seems to have let me connect to the other pages such as My Profile, Statistics,Project page, etc.

Now I just have to fix the fonts issue.

---

