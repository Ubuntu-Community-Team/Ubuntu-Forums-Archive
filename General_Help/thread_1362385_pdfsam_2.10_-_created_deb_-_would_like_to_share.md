---
title: "pdfsam 2.10 - created deb - would like to share"
date: 2009-12-23
forum: General Help
---

### Post by practic on 2009-12-23
I noticed that pdfsam was up to version 2.10 and the current ubuntu version is 1.1.3. There are quite a few changes. While it is fairly easy to download the zip archive from pdfsam.org and either run the jar file, or sudo copy the new files overtop of the old ones, I put together a DEB file which seems to work fine (basically took the old DEB, and replaced the files, edited the control file).

I'd like to put this somewhere to share with others until the newer one is officially available, but was a bit uncertain about putting it on my own website, as I don't know what kind of traffic it will generate.

So I tried setting up a PPA area on launchpad, but quickly got bogged down with dput, gpg, dbuild, etc. I don't have a changes.log, and couldn't understand what else they were talking about.

Anyone have any other suggestions? Should I just attach the DEB as a ZIP to this thread? It is about 12.4mb...

---

### Post by dcstar on 2009-12-23
> **practic said:**
> I noticed that pdfsam was up to version 2.10 and the current ubuntu version is 1.1.3. There are quite a few changes. While it is fairly easy to download the zip archive from pdfsam.org and either run the jar file, or sudo copy the new files overtop of the old ones, I put together a DEB file which seems to work fine (basically took the old DEB, and replaced the files, edited the control file).

I'd like to put this somewhere to share with others until the newer one is officially available, but was a bit uncertain about putting it on my own website, as I don't know what kind of traffic it will generate.

So I tried setting up a PPA area on launchpad, but quickly got bogged down with dput, gpg, dbuild, etc. I don't have a changes.log, and couldn't understand what else they were talking about.

Anyone have any other suggestions? Should I just attach the DEB as a ZIP to this thread? It is about 12.4mb...

People are getting wary about any packages outside the official repositories, basically anyone can write any malware they like and tell others "hey, install this .deb".......

If the PPA repositories force some sort of verification then that is a step in the right direction, but the whole notion of providing software packages outside of the official sources contains risk - no matter how good the intentions are.

If you want an updated version of a package then ask the Ubuntu developers to make it or check to see if it already available in the next version:

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by practic on 2009-12-23
> **dcstar said:**
> People are getting wary about any packages outside the official repositories, basically anyone can write any malware they like and tell others "hey, install this .deb".......

That is the inevitable result of freedom. I don't see that as avoidable, and I'm not particularly wary about downloading deb files from outside sources. If I go to a website where it is clear that the folks are sincerely interested in the same things I am, and are not pushing some fly-by-night money-making scheme, I will trust them.

The problem is that pushing everything on the ubuntu developers is simply not reasonable. They can't do everything, and there will always be people outside of the ubuntu developers who will specialize in certain areas, and be willing to push farther and faster in those areas.

It's the age-old struggle between centralization and diversity. Both have their place.

> **dcstar said:**
> If the PPA repositories force some sort of verification then that is a step in the right direction, but the whole notion of providing software packages outside of the official sources contains risk - no matter how good the intentions are.

I went through the steps of getting a PGP key and having the fingerprint registered with them, etc. But when it came to uploading the file, I couldn't figure out what to do from their instructions...it seemed that they wanted some kind of source directory. The instructions simply weren't clear enough for a layman.

> **dcstar said:**
> If you want an updated version of a package then ask the Ubuntu developers to make it or check to see if it already available in the next version:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

No, it is not available. The pdfsam slated for Lucid (so far) is still 1.1.3. That's archaic. The new 2.1.0 has many more features.

I'll just go ahead and put it up on my website then, and if Lucid catches up, then I'll point people to that instead.

[http://www.practicatechnical.com/files/pdfsam2.1.0.deb](http://www.practicatechnical.com/files/pdfsam2.1.0.deb)

---

### Post by FrancoNero on 2010-02-21
couldn't believe how antiquated my version of pdfsam (karmic) was, thanks for the deb! hooray for initiative. personally, I hate having older versions of software than those available from the people who're creating it

---

### Post by Matt G Dalian on 2010-04-11
Solved this problem another way.

For people stumbling onto this thread from a search engine this was my problem:

The version of PDFsam in Ubuntu Software Center is old (as of April 11, 2010 version 1.1.3-1 ). The current version of PDFsam is 2.2.0.

And the current version is much better than version 1.1.x- for example, in the current version you can see individual PDF pages, so you can load 5 pages from PDF A, 7 pages from PDF B, then extract two pages from PDF A and two from PDF B to make a four-page PDF C, etc. 
There are other Linux utilities that allow you to do this but PDFsam is nice because it has a graphical user interface (GUI).

So anyway, here's how to get PDFSam 2.2.0 on your Ubuntu computer (I'm running Ubuntu 9.10 Karmic).

1. Install PDFsam from the Ubuntu Software Center. It will install as version 1.1.3-1.

2. Now download the most recent version of PDFsam in ZIP format from the official website ( [http://www.pdfsam.org/?page_id=32](http://www.pdfsam.org/?page_id=32) ).

3. Extract the pdfsam-2.x.x-out.zip file into a folder (mine was in ~/Downloads/pdfsam-2.2.0-out ). You're going to copy all of these files in this ZIP archive into their corresponding places in the /usr/share/pdfsam  folder, replacing the original files that were installed through Ubuntu Software Center.

4. To do this you need to open up another file manager as root. So in terminal type:
gksudo nautilus

5. Go to /usr/share/pdfsam
(You probably want to copy and paste all of these files into a backup directory, just in case)

6. Delete /usr/share/pdfsam/pdfsam-1.x.x.jar and copy pdfsam-2.x.x.jar in its place

7. Delete the contents of the /usr/share/pdfsam/lib folder and copy the files from the /lib directory of pdfsam-2.x.x-out.zip

8. Delete the contents of the /usr/share/pdfsam/plugins folder and copy the files and folders from the /plugins directory of pdfsam-2.x.x-out.zip

And you're done. Now when you open up pdfsam from Applications -> Office it will load as 2.x.x instead of the older version.

Matt

---

### Post by inspired on 2010-04-21
> **practic said:**
> 
I'll just go ahead and put it up on my website then, and if Lucid catches up, then I'll point people to that instead.

[http://www.practicatechnical.com/files/pdfsam2.1.0.deb](http://www.practicatechnical.com/files/pdfsam2.1.0.deb)

Thanks so much for posting this file. Really helpful. Installed and happy.

Cheers,
Jonathan

---

### Post by champost on 2011-08-29
This is just a personal experience and may work for some...

For installing pdfsam-2.2.1 you basically follow what Matt G Dalian posted but you needn't copy the "pdfsam-config.xml" (created problems for me) and the "pdfsam-starter.exe" (not needed a DOS/Widows executable) into /usr/share/pdfsam from your temporary extracted files folder (e.g. /home/aham/Downloads/pdfsam-2.2.1-out).

It all works fine now with a simple warning "Unable to find pdfsam-config.xml into /usr/share/pdfsam"

cheers
champost

---

### Post by practic on 2012-08-25
I originally started this thread. pdfsam has since been updated again. I'm posting a download link to another non-official DEB on my site for anyone that needs this:

[pdfsam_2.2.1]("http://www.practicatechnical.com/files/pdfsam_2.2.1.deb")

---

### Post by raja.genupula on 2012-09-12
Hi Thank you for this , why dont you upload it into your PPA  ?

---

### Post by Bromden on 2012-11-07
On sourceforge you can find the Pdfsam release that can be executed easily with java, without installing it ;)

---

### Post by frogotronic on 2013-02-15
> **practic said:**
> I originally started this thread. pdfsam has since been updated again. I'm posting a download link to another non-official DEB on my site for anyone that needs this:

[pdfsam_2.2.1]("http://www.practicatechnical.com/files/pdfsam_2.2.1.deb")

Hi,

Thanks very much!

- CH

---

### Post by kelly harlton on 2013-05-17
> **Bromden said:**
> On sourceforge you can find the Pdfsam release that can be executed easily with java, without installing it ;)

Thanks Practic for posting your deb!
and thanks Bromden!, The Sourceforge download was the ticket for me! just extracted, right clicked the .jar file, and ran with java! [http://sourceforge.net/projects/pdfsam/](http://sourceforge.net/projects/pdfsam/)

---

### Post by web1-practicatechnical on 2013-08-22
Just wanted to mention that I added a new update for the pdfsam deb on my website:
[http://www.practicatechnical.com/files/pdfsam_2.2.2_all.deb](http://www.practicatechnical.com/files/pdfsam_2.2.2_all.deb)

---

### Post by Lee_Adams on 2013-09-01
Hey practic/web1-praticatechnical:
I want to give you a huge thank you! 3 and a half years later you are still updating the .deb

Cheers!

---

