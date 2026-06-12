---
title: "Lucid  cups pdf error"
date: 2010-05-01
forum: General Help
---

### Post by LaughingHorse on 2010-05-01
I just upgraded from the previous version to Lucid.
I tried to print a page in Firefox as a pdf.

getting the printer selection screen up, it shows me PDF and PDF1 both have the smae message
"Backend /usr/lib/cups/backend/cups-pdf does not exist!"

Any ideas on how to get it to exist?

I tried re-installing CUPS PDF and still no luck.

Thanks in advance for your suggestions.

---

### Post by oldfred on 2010-05-01
I just installed Lucid to my beta partition for testing and my reinstall script includes these commands. I have that file on both Karmic & the test lucid. I have on tried printing in Lucid yet and am back in my Karmic right now.

sudo apt-get install cups-pdf
sudo aa-complain cupsd
#chmod 777 ~/PDF
#sudo chmod 700 /usr/lib/cups/backend/cups-pdf

I do not know know why I commented out the last two lines. I think my /PDF does not need chmod as it is a link to my data partition, but do not know about chmod on cups-pdf.

---

### Post by LaughingHorse on 2010-05-03
I got it solved.

Here is what I did

alt+f2 and type "gksudo browsername"
(firefox in my case)
So it would be "gksudo firefox"

Once logged in as root, I went to 
[http://localhost:631/](http://localhost:631/)

From there I was able to administrate CUPS.  The CUPS-PDF was idle. So I activated it, and now I can print pdf's.

What was very strange however, is **only** the CUPS PDF printer was idle. After the upgrade, my Brother HL-2070N, and my Cannon ip5200 has absolutely no problem.

So the problem is solved, but what caused it in the first place when I upgraded?

---

### Post by bayvista on 2010-06-17
I had a strange problem with this. When printing my monthly Credit Card Statement using Acroread, the first page of the PDF file was black and unreadable. The remaining pages were OK.

The problem turned out to be the Canon Printer Driver. I was printing to a Canon LBP3100. When I switched to my Brother DCP165, it printed perfectly. I will report this as a bug to Canon

---

### Post by negotiation on 2011-02-07
[LaughingHorse]("http://ubuntuforums.org/member.php?u=825874"): please provide more detail. I've no idea from what you've written I've no idea what action to take to achieve this: 'From there I was able to administrate CUPS.  The CUPS-PDF was idle. So I activated it, and now I can print pdf's.' Am able to see the options as you have described, but hit a dead end.

---

### Post by akwatve on 2011-03-22
I had the same probem. After doing everything mentioned here. I get a new error :

/usr/lib/cups/filter/pdftopdf failed.

Some searching revealed that libpoppler is responsible for this. But the solution seems to recompile cups to incorporate changes in the prototype of one of the functions in poppler. This is where things get uncomfortable.

Does anyone know is there is another way of fixing this without recompiling cups or libpoppler

Thanks,

---

### Post by brian724 on 2011-04-27
I had the same problem. I installed cups-pdf from synaptic and I can print to pdf.

---

### Post by keinea on 2011-04-30
I had the same issue after upgrading from Hardy to Lucid and used aptitude to purge and reinstall cups-pdf.

Just have to remember to go into System --> Administration --> Printing (configure printing), and right-click on the PDF printer to ENABLE it after the re-installation.

Refer to:

[https://bugs.launchpad.net/ubuntu/+source/cups-pdf/+bug/573667](https://bugs.launchpad.net/ubuntu/+source/cups-pdf/+bug/573667)

---

### Post by megafedt on 2011-05-05
> **keinea said:**
> I had the same issue after upgrading from Hardy to Lucid and used aptitude to purge and reinstall cups-pdf.

Just have to remember to go into System --> Administration --> Printing (configure printing), and right-click on the PDF printer to ENABLE it after the re-installation.

Refer to:

[https://bugs.launchpad.net/ubuntu/+source/cups-pdf/+bug/573667](https://bugs.launchpad.net/ubuntu/+source/cups-pdf/+bug/573667)

Great - thanks! However, now I have a new problem...

The GUI web-interface is back, but after I enable the printer and reprint some of the stopped jobs I get this: "Print Error" + "There was a problem printing document 'Test Page' (job 272): 'Stopping job because the sheduler could not execture the backend."

I've tried to google for this and I found some suggestions, primarily a few years back. I tried a few things, however please advice/suggest something if you have an idea about what might solve this...

I've also tried to use the "Printing troubleshooter" by "Enable Debugging" (should cause the scheduler to restart). I then click "diagnose" and also get this error message in my "Document Print Status"-queue: "There is a missing print filter for printer 'PDF'".

My debug output is the following:

E [05/May/2011:10:50:39 +0200] [Job 272] Stopping unresponsive job!
E [05/May/2011:10:50:39 +0200] Unable to execute /usr/lib/cups/backend/cups-pdf: No such file or directory
E [05/May/2011:10:50:39 +0200] [Job 273] Stopping job because the sheduler could not execute the backend.

Please help / suggest me some advice so I can begin printing to PDF again, thanks!

---

### Post by megafedt on 2011-05-05
> **LaughingHorse said:**
> I got it solved.

Here is what I did

alt+f2 and type "gksudo browsername"
(firefox in my case)
So it would be "gksudo firefox"

Once logged in as root, I went to 
[http://localhost:631/](http://localhost:631/)

From there I was able to administrate CUPS.  The CUPS-PDF was idle. So I activated it, and now I can print pdf's.

What was very strange however, is **only** the CUPS PDF printer was idle. After the upgrade, my Brother HL-2070N, and my Cannon ip5200 has absolutely no problem.

So the problem is solved, but what caused it in the first place when I upgraded?

This doesn't seem to work for me - sorry, see my other post...

---

### Post by beau.raines on 2011-06-09
I had this same problem and keinea's solution worked for me.  For some reason, it appears that cups-pdf was not installed during my inplace upgrade to Lucid.

> **keinea said:**
> I had the same issue after upgrading from Hardy to Lucid and used aptitude to purge and reinstall cups-pdf.

Just have to remember to go into System --> Administration --> Printing (configure printing), and right-click on the PDF printer to ENABLE it after the re-installation.

Refer to:

[https://bugs.launchpad.net/ubuntu/+source/cups-pdf/+bug/573667](https://bugs.launchpad.net/ubuntu/+source/cups-pdf/+bug/573667)

---

### Post by riky_6 on 2012-01-15
I had the same problem printing a page with the CUPS PDF virtual printer: "not execute the backend"

I solved the problem running the this command:
#sudo chmod 700 /usr/lib/cups/backend/cups-pdf

---

### Post by kuifje09 on 2013-02-24
I nedded to reinstall, because it wasn't there after the upgrade to 11.10

Then had to run  /usr/sbin/cupsenable PDF

Not I could print to PDF again.

( with the system tools menu, icould not fix this )

---

