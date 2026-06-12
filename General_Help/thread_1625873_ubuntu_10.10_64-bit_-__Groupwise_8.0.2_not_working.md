---
title: "ubuntu 10.10 64-bit -  Groupwise 8.0.2 not working."
date: 2010-11-19
forum: General Help
---

### Post by cucu007 on 2010-11-19
Dear all,
I just loaded my machine with ubuntu 10.10 64-bit desktop, any clues how to load the groupwise client in this thing. I try a few tricks and so far have been unsucesful, please advise.

---

### Post by michaeljp on 2010-12-30
I haven't had any luck with this either.  In the interim I've been using the Evolution client to access my Groupwise POA via SOAP.  It works...but I'd rather be using the Groupwise client.  If I happen to find something or figure it out I'll make sure to post it.

---

### Post by Yellow Pasque on 2010-12-30
Is it a 32-bit program? What happens when you start it from a terminal?

---

### Post by Yellow Pasque on 2010-12-30
Ok. So it looks like the Linux client is a 32-bit Java app. You will need to start Synaptic and select 'Repositories' under the 'Settings' menu. Then enable the Canonical Partner repo: [https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20Canonical%20Partner%20Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20Canonical%20Partner%20Repositories)

After that, update/reload your software sources info (click 'Reload' in Synaptic) and install ia32-sun-java6-bin

---

### Post by DouglasAWh on 2011-08-22
I'm using a 32-bit OS and I still can't get this working.  I'm on Linux Mint, but the internals shouldn't be too different.  I have partners enabled, but there is no ia32-sun-java6-bin for me to download...and since I'm using 32-bit I don't think I should need that anyway (maybe that's why it's not being offered?).

I have also been unable to get Evolution to work.  Here is the information I have about our GroupWise servers: [http://law.unh.edu/it/downloads.php](http://law.unh.edu/it/downloads.php)

The Groupwise client works great on Fedora, but I had problems with Evolution on Fedora as well.

---

