---
title: "boinc in 10.04"
date: 2010-05-11
forum: General Help
---

### Post by Warthaug on 2010-05-11
I have been running boinc (seti@home and rosetta@home) for years.  It has always installed and run fine from the ubuntu repo's for as long as I've been running ubuntu - until now.

I installed boic client/manager as per usual, selected my projects, and for a few days things ran fine.  But apparently spontaneously, ubuntu decided to stop running boinc anymore.  No clients appear as processes under system manager, nor is the CPU load anywhere near where it is normally when boinc is running, nor am I accumulating credit, and the boinc manager cannot connect to the local host.  Boinc also does not appear under startup programs, which if I remember correctly, it used to.

I tried starting boinc from /usr/bin, using the command boinc, and I got an error saying boinc was already running.

I then tried the command boinc --show_projects, and I get the same error as above (another instance of boinc is running).

Oddly, although it doesn't appear in the System->Admin->system monitor list of processes, the command line command "pgrep boinc" returns "1963".

Any ideas what is occuring, and how to fix it?

---

### Post by Warthaug on 2010-05-11
Fixed it - had the same problems with my printer (they all disappeared).  Somehow, in the update, things got misconfigured.  Reinstalling (boinc) fixed the boinc issue; reinstalling cups fixed the printers.

Bryan

---

