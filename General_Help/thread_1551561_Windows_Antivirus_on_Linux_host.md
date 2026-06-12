---
title: "Windows Antivirus on Linux host?"
date: 2010-08-12
forum: General Help
---

### Post by knottshawk on 2010-08-12
Does anyone know of a list of Antivirus suites that will run on Linux but scan for Windows Malcode?

It's a difficult thing to search for because searches turn up so many bad results (AV for linux, AV for Windows, etc)

Thanks!

---

### Post by Noz3001 on 2010-08-12
There's ClamAV and AVG for linux

---

### Post by qamelian on 2010-08-12
All of the anti-virus apps I know of for linux scan for Windows viruses / malware. This includes ClamAV, AVG, and Avast.

---

### Post by eriktheblu on 2010-08-12
I believe MacAfee and Symantec have (or had) Linux applications as well.

---

### Post by WorMzy on 2010-08-12
I use [ClamAV]("apt://clamav") (sudo apt-get install clamav), which is in the repos. There's also [AVG]("http://free.avg.com/gb-en/download") and [Avast!]("http://www.avast.com/linux-home-edition"), which I think you'll need to manually download and install.

---

### Post by TyLLy_4 on 2010-08-12
it seems you want to scan a partition form another partition. 

try UBCD4WIN (Ultimate Boot Disk For Windows) 

Its a live windows xp enviroment that comes with lots of tools (like antivirus/antispyware software) 

[http://www.ubcd4win.com/](http://www.ubcd4win.com/)

---

### Post by ankit singh on 2010-08-12
clam av dont look for windows viruses that effective,i have tested it.Avast does the job.I cant say about other antivirus softwares. I m now testing bit-defender, will post about it in few minutes

---

### Post by knottshawk on 2010-08-12
I was hoping there was a master list somewhere... bum deal.

---

### Post by wilee-nilee on 2010-08-12
> **knottshawk said:**
> I was hoping there was a master list somewhere... bum deal.

Download superantispyware for windows the free version. You can set it to not run at startup, but when you want it to, and is a excellent program.
[http://www.superantispyware.com/](http://www.superantispyware.com/)

Malwarebytes is very good as well it doesn't run automatically.
[http://www.malwarebytes.org/](http://www.malwarebytes.org/)

Both of these have free home versions, and can be run only when you want to scan, in windows.

---

### Post by knottshawk on 2010-08-12
> **wilee-nilee said:**
> Download superantispyware for windows the free version. You can set it to not run at startup, but when you want it to, and is a excellent program.
[http://www.superantispyware.com/](http://www.superantispyware.com/)

Malwarebytes is very good as well it doesn't run automatically.
[http://www.malwarebytes.org/](http://www.malwarebytes.org/)

Both of these have free home versions, and can be run only when you want to scan, in windows.

> **knottshawk said:**
> 
Does anyone know of a list of Antivirus suites that will run on Linux but scan for Windows Malcode?

I need it to run on Linux... not Windows.

---

### Post by Rubi1200 on 2010-08-12
Not exactly>  a master list but perhaps a start:

[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

---

### Post by 3Miro on 2010-08-12
There are no Linux viruses so all apps that scan for viruses scan for Windows viruses. Google search for "Antivirus for Linux" should return proper results.

Here is a link with an official HowTo that I found very useful.

[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

---

### Post by tgm4883 on 2010-08-12
> **3Miro said:**
> There are no Linux viruses so all apps that scan for viruses scan for Windows viruses. Google search for "Antivirus for Linux" should return proper results.

Here is a link with an official HowTo that I found very useful.

[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

Not entirely true, there are a few threats for Linux, though I don't believe there are any that are strictly viruses. 

Symantec has a product called "Symantec Antivirus for Linux" that scans for Windows/Mac/Linux threats.

---

### Post by knottshawk on 2010-08-12
> **3Miro said:**
> There are no Linux viruses so all apps that scan for viruses scan for Windows viruses. Google search for "Antivirus for Linux" should return proper results.

Here is a link with an official HowTo that I found very useful.

[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

This has a list of Linux viruses for you... :)
[http://en.wikipedia.org/wiki/Linux_malware#Anti-virus_applications](http://en.wikipedia.org/wiki/Linux_malware#Anti-virus_applications)

Thanks for the link though!

---

### Post by shadow120 on 2010-08-12
just run whatever you would run on windows with wine thats what i do to scan the files i upload.  spysweeper and zone alarm anti-virus work.  ive used others thru wine in the past so i think you could get just about any of them to work.  hope this helps

---

### Post by qamelian on 2010-08-13
> **ankit singh said:**
> clam av dont look for windows viruses that effective,i have tested it.Avast does the job.I cant say about other antivirus softwares. I m now testing bit-defender, will post about it in few minutes
In a test comparing a variety of anti-virus apps last year, ClamAV was one ot the top 3. In my experience, it blows Avast out of the water. When I tested Avast, I had issues with it generating too many false positives and missing files that I had intentionally infected as part of the test.

---

