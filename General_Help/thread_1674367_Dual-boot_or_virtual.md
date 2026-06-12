---
title: "Dual-boot or virtual?"
date: 2011-01-23
forum: General Help
---

### Post by mousethief on 2011-01-23
I'm a fairly new Ubuntu user and am coming up to speed (slowly), but I find now that I need to run some Windows apps for school. Grr. I have made my machine a dual-boot, but a bud said I should think about running XP from within Ubuntu on a virtual machine instead. I haven't really started any heavy lifting on the new installation so I'm not averse to starting over. 

So which is better: creating a dual-boot set-up, or running XP as a virtual machine from inside Ubuntu? 

Thanks!

MT

---

### Post by clearym on 2011-01-23
I started off dual booting like u r now, but now I use virtualbox if I need/want to do something in another OS. The virtual machine makes it nice and easy to switch back and forth between OSes but can be a strain on your computers resources. If u have a fairly new multi-core processor and lots of RAM definitely use virtual machines. If not, give it a try and see how ur machine handles the strain. You may find the performance lags. So I guess it depends. My opinion, if ur CPU can handle it use a virtual...

---

### Post by mousethief on 2011-01-23
Well, good point. I'll try the virtual without changing anything about the boot setup, and if I don't like it, then I'm not stuck with it.

---

### Post by coldraven on 2011-01-24
Another factor to think about is what sort of XP install disk you have.
If it is one with the serial number on it then it is easy to make a VM in VirtualBox.
If you have an OEM install with a restore disk you will need to search the VirtualBox forum for tips. (Look for a script called VMbios) Otherwise the restore disk will not get the data from your BIOS and fail to activate XP.
Technically, if you have two XP installations this would be in breach of Windows T&C but as you are going to delete one  I guess that's OK.

---

### Post by piquat on 2011-01-24
Totally different opinion:

Keep dual booting, BECUASE it's annoying.  Why?  It will push you to find ways to do things in Linux that you used to do in Windows.  Eventually you will get to those few applications that you just can't get to run or find substitutes for in Linux.  THEN, use a VM for those few.

---

### Post by sammiev on 2011-01-24
I prefer Dual Boot at this time. Why delete Windows just to add it again to run at a slower speed. GL :)

---

### Post by mastablasta on 2011-01-24
> **sammiev said:**
> I prefer Dual Boot at this time. Why delete Windows just to add it again to run at a slower speed. GL :)
yeah not to mention that applications under virutal box might not run as smooth as in original environment. everythign can't be run in virutal box and it is not a total substitute.

---

### Post by mousethief on 2011-01-24
Well I went ahead and installed VirtualBox and I'm pretty happy with it. I'll keep the old Windows boot around for now, I guess, in case my happiness fades. Really there's only two things I need Windows for: (1) some of the documents I'm formatting absolutely require Word by the people I'm handing them off to and I'd rather not buy another copy of Word (if there is Word for Linux? I dunno); and (2) I have a tutorial put out by Micro$oft to learn MS SQL that I need for school. Since I'm not doing much heavy lifting on my computer anyway (chatroom, social networking, email, occasional YouTube), I don't imagine the performance hit is going to be too insurmountable (pun intended).

Thanks everybody for answering! This is a great place.

---

### Post by MARP1961 on 2011-01-24
Do 'those people' just need the office files saved as 'doc.' files? If this is all you need Microsoft Office for you know you can use the 'Save As' option then select a different file format/type eg. Microsoft Word 97, 2000,XP (doc.)

---

### Post by earthmeLon on 2011-01-24
Really depends on how often and how many different things you need Windows to run within.  

[VirtualBox]("http://www.virtualbox.org/wiki/Documentation") is a nice/easy/free way of running Windows under Linux (virtually).  It makes setting up networking/3d acceleration very easy.

I like this method because I have to test websites in IE to make sure everybody that visits these sites is seeing things correctly.  I have a Windows 7 copy that I run and works great.  

If you don't have a copy of windows that you can install, and just want to do simple tests, you can use Microsoft's free images found [here]("http://www.microsoft.com/downloads/en/details.aspx?FamilyId=21EABB90-958F-4B64-B5F1-73D0A413C8EF&displaylang=en").  They can be downloaded and used until they expire.  After which, you'll just have to re-download.


The downside to virtualization is that it does slow your computer down and programs within the virtualized system could potentially not work as well as they should.  

Before doing any of this, I'd see if Wine can handle the program.  That's usually the most simple way to do it :D


[OpenOffice]("http://download.openoffice.org/") and [LibreOffice]("http://www.libreoffice.org/download/") are two great alternatives to ALL MS Office applications.

---

### Post by BHEJU on 2011-01-24
I have used both. but the way I use my machines. I prefer virtual.

for me: both set-up are stable. I do not have perf issues on any as I have powerful machine: I5 and 6gig ram.
The only reason I prefer virtual is that I rarely need to use Win. and I always have some apps running on my ubuntu. So, it is easy for me that way since I do not need to shutdown ubuntu.
So, I suggest virtual over dual-boot if you don't have to use win that often. but it depends on your use of win and ubuntu.

---

