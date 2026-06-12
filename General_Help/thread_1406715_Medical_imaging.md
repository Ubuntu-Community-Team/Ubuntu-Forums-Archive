---
title: "Medical imaging"
date: 2010-02-14
forum: General Help
---

### Post by ok_dr on 2010-02-14
Hi all. I'm a resident in neurology and in my work you deal often with CT scans and MRIs which come on Cds and the viewing software included is for Windows.
So I was wondering whether you've heard of any linux software able to open and browse medical imaging. I tried Aesculap but it didn't work, the quality of the images was awful and you couldn't browse them conveniently anyway, you'd have to explore every folder and file one by one.
I've heard about a free open source Mac software called Osirix but there doesn't seem an equivalent for Linux. If anyone knows one please tell me.

---

### Post by iponeverything on 2010-02-14
googleing on "ubuntu DICOM" should give you good idea of the present state of affairs.

Getting a machine with plenty cpu power and ram will allow you to you to do the work with the more mature widows application in a VM that is dedicated to just that purpose. Also, backing up and restoring VM's are as easy as copying a file, so you will not have to worry about the inevitable widows flakeout at the worst possible time.

Virtualbox works quite well.

---

### Post by mörgæs on 2010-05-30
While searching for programs for viewing pictures of my poor foot, I found this old thread.

**Xmedcon** is a good program for converting DICOM to other formats, for example PNG. Besides mere converting there are some good functions, for example you can add fake colours for making the fractures stand out more clearly.

---

### Post by bumanie on 2010-05-30
Here's an [article]("http://www.linuxlinks.com/article/2010030916055813/MedicalImaging.html%5C") from March this year. Hope it helps.

---

### Post by Robertoprb on 2010-08-21
> **ok_dr said:**
> Hi all. I'm a resident in neurology and in my work you deal often with CT scans and MRIs which come on Cds and the viewing software included is for Windows.
So I was wondering whether you've heard of any linux software able to open and browse medical imaging. I tried Aesculap but it didn't work, the quality of the images was awful and you couldn't browse them conveniently anyway, you'd have to explore every folder and file one by one.
I've heard about a free open source Mac software called Osirix but there doesn't seem an equivalent for Linux. If anyone knows one please tell me.
I'm a radiology medical resident, and i'm using EvoRad solution.
Works perfectly on ubuntu. It's more professional and uses the java Environment.
just go to [www.evorad.com](www.evorad.com)
But i would still prefer a efilm or osirix port to linux...

---

### Post by radtek on 2010-08-21
> **ok_dr said:**
> Hi all. I'm a resident in neurology and in my work you deal often with CT scans and MRIs which come on Cds and the viewing software included is for Windows.
So I was wondering whether you've heard of any linux software able to open and browse medical imaging. I tried Aesculap but it didn't work, the quality of the images was awful and you couldn't browse them conveniently anyway, you'd have to explore every folder and file one by one.
I've heard about a free open source Mac software called Osirix but there doesn't seem an equivalent for Linux. If anyone knows one please tell me.

I'm assuming these are outside films brought in with patients. Our PACS system is McKesson and definitely will export to linux via CD. Viewer isn't station quality of course... 

Downloaded evorad and it didn't work for me. Doesn't mean it won't work for you.

If you have a copy of windows then Virtualbox is free and easy to use. As distasteful as it is I was able able to quickly connect an iphone to itunes without jailbreaking using virtualbox. Evorad or some other software might fare better this route.

Good luck.

---

### Post by TheCraneMan on 2010-08-21
> **ok_dr said:**
> Hi all. I'm a resident in neurology and in my work you deal often with CT scans and MRIs which come on Cds and the viewing software included is for Windows.
So I was wondering whether you've heard of any linux software able to open and browse medical imaging. I tried Aesculap but it didn't work, the quality of the images was awful and you couldn't browse them conveniently anyway, you'd have to explore every folder and file one by one.
I've heard about a free open source Mac software called Osirix but there doesn't seem an equivalent for Linux. If anyone knows one please tell me.
You should use wine, add the repository by doing
Open the Software Sources menu by going to  **System->Administration->Software Sources**.  Then select the **Third  Party Software** tab and click **Add**. Add: [I]ppa:ubuntu-wine/ppa
[/I]( copied from [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb) )

just run the installer ( I'm assuming it's executable ) in wine and install it on your virtual "C:\" drive. 
Going into **Applications->Wine->Programs** should be where the software is located ( like the start menu in Windows )

Hope this helps!

---

### Post by ok_dr on 2010-10-12
Since there hadn't been an answer in 2 months I had quit on this thread. I see there's been some activity and I thank every one for their answers.
Regarding wine use I've tried and it doesn't work, and the softwares I mentioned run from the CD and are not to be installed.
I don't need software to convert to other formats because for each CT or MRI exam there are sometimes over 100 images so it would take an eternity to navigate them without the appropriate software.
Of the other proposed variants the only one who seems to be on to smth is Evorad. I've been using it only for 30 min now, it doesn't seem to integrate perfectly with Ubuntu but with some effort I was able t work with the cd that I tried. Maybe there'll be even better versions in the future.
Regarding the possibility of using Windows in VirtualBox, I'm aware of that, I'd been doing that before I opened this thread. However I was hoping not to have to use Windows.
I really hope there comes a Linux version of Osirix, it's open source after all. A friend of mine who has Mac's been using it and it's really a great software, I'd want it even if I was using windows, it's a really wonderful software you can do so much with it.

---

### Post by ok_dr on 2010-10-15
Just an update to say that Evorad is a fine software. Tried with discs from different sources and got the job done every time. :biggrin:. Thanks a lot. Now I don't have to boot XP in Virtualbox anymore

---

### Post by felix94 on 2010-12-27
Hi!

For my dissertation I measured pediatric renal stones by CT with different kv - measurements (80, 100, 120). Now i got the pictures and was succesful uploading them in Osirix. 

My problem is that I have no idea where I can find the kv - Information on Osirix Viewer and everything would be for nothing if I can´t find this information.

I´m pretty desperate and get more and more depressed about this work.

Can somebody help me to find a solution?

Greets from Austria Felix

---

