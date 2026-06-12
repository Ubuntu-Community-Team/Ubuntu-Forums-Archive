---
title: "CUPS Server Excessively High CPU Usage on Certain Print Jobs"
date: 2012-10-10
forum: General Help
---

### Post by Kirk Schnable on 2012-10-10
I am currently managing a Linux desktop deployment in an educational environment, and we are experimenting with migrating from our Windows print server (which has had numerous performance and reliability issues) to a Linux CUPS print server.

We currently have a CUPS deployment of version 1.4.3 running on Ubuntu 10.04 LTS.

Here is the PDF file I am using in this troubleshooting process.  It is a normal PDF document that came from one of our staff members.  It prints up to page 3, then stops.

[http://www.epecweb.com/pub/ubuntu-cups-cpu-issue_document.pdf](http://www.epecweb.com/pub/ubuntu-cups-cpu-issue_document.pdf)

When printing PDF files, the process "pdftopdf" runs, then the process "pdftops" runs.

When printing these "problem" documents, the pdftops process appears to be the problem.  It slams the CPU on the server.  The process will run for indefinite amounts of time until we kill it, and after one or two of them start up, they impair the ability of other users to use the print server in a timely manner.

[IMG]http://www.epecweb.com/pub/ubuntu-cups-cpu-issue_pdftops_100percentcpu_cups1.4.3.png[/IMG]


We thought maybe this issue would be fixed in an update, so we installed CUPS 1.5.3 on a test server running Ubuntu 12.04 LTS.

We encounter an identical issue, with this document.  When printing it, it also prints up to page 3 then stops.  "pdftopdf" runs, then instead of "pdftops", it runs "gs".  However, "gs" is now slamming the server.  

[IMG]http://www.epecweb.com/pub/ubuntu-cups-cpu-issue_pdftops_100percentcpu_cups1.5.3.png[/IMG]


I am not really sure how to proceed with troubleshooting this problem... can someone from the community see if they can reproduce it?  (The link to one of the problem documents is above).

The problem occurs to varying degrees with different PDF files, it seems to be exclusively an issue with PDF files thus far.  The document I provided is simply 1 example, but it is the most obvious\best example of the problem I have seen so far.

I'd appreciate any input you folks might have on this issue.  If you need more information, let me know.

Thanks!
Kirk

---

### Post by Kirk Schnable on 2012-10-16
This is becoming an issue in our organization, where documents are jamming up the print queue for 10-20 minutes and causing huge delays on everyone's print jobs.  We are receiving enough complaints about it that we may be forced to switch everything back to our Windows print server... or look for other alternatives...

I'd really rather not do that... can someone please see if they are able to reproduce our issue on their server, and maybe get the ball rolling with troubleshooting this problem?

Thanks
Kirk Schnable

---

### Post by Kirk Schnable on 2012-10-17
We have changed our drivers from the HP Drivers to Generic PCL drivers.  The printers still work, but I am not convinced that they perform any better or worse with these new drivers.

In our research, we've found that this might actually be an Evince problem, not a CUPS problem.  It seems that Evince has caused a lot of other users these same headaches, with high print server CPU load and long wait times for print jobs.

We are investigating it from this front, and it seems that using Adobe Reader instead of Evince "solves" the PDF printing problem, at least with the sample document in this thread.

I'll keep you guys posted...

Kirk

---

