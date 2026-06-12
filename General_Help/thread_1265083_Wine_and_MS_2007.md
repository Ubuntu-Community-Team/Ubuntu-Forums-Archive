---
title: "Wine and MS 2007"
date: 2009-09-13
forum: General Help
---

### Post by holycow131415 on 2009-09-13
How well does MS 2007 work on WINE? Does it crash when using features, i know it installs from seeing videos on youtube.

The only thing that is stopping me from putting xubuntu on my desktop is that my users need to use MS office 2007 for school. Yes im aware of openoffice, but that doesnt cut it with school using ms office 2007 so dont tell me to get openoffice ;)

---

### Post by harrismh777 on 2009-09-13
> **holycow131415 said:**
> 
The only thing that is stopping me from putting xubuntu on my desktop is that my users need to use MS office 2007 for school. Yes im aware of openoffice, but that doesnt cut it with school using ms office 2007 so dont tell me to get openoffice ;)

I guess you have not been watching the news lately regarding office 2007???

Microsoft has been ordered by a judge to *stop* selling office 2007 because it violates an XML patent. Schools that have office 2007 and insist on using xml standard are going to be trouble in the long run. Regardless, the open document format is going to win the day... because folks are not going to be able to use office 2007 XML.  (yes, M$ is going to appeal, and they are going to lose)

Use open software... use OpenOffice !:guitar:

---

### Post by holycow131415 on 2009-09-13
yes i do know and it still doesnt change the fact that my user needs it for school when thats all the texts use lol =)

so how does it handle on wine?

---

### Post by tacantara on 2009-09-13
I've tried Wine several times for various programs, unfortunately MS Office 2007 isn't one of them.  Personally, I wouldn't rely on Wine, as it seems to handle games better than most applications (just my opinion, not trying to flame up anything here).  I installed Sun's VirtualBox so I can run Windows in a virtual environment.  That may be a more practical solution for you, as it ensures that Office 2007 will run as you need it to.  Download the latest version of Virtual Box from [http://www.virtualbox.org/](http://www.virtualbox.org/) (if you download the version in Synaptic, it won't be full-featured like the one at the website).  Build a virtual disk, and install Windows.  Once Windows is installed in the virtual machine, start it up, and install Office like you normally would in Windows.

---

### Post by holycow131415 on 2009-09-13
would it be really slow with a pc having 512 ram, penti 3?

---

### Post by tacantara on 2009-09-13
Hmm...I probably should have asked that first.  You'd need to dedicate about 1/2 your RAM to the virtual machine in order to run Windows efficiently (provided that you're using XP), and even then 128 MB may not be enough to run the OS and Office 07.

---

### Post by holycow131415 on 2009-09-13
So has anyone used ms 2007 with wine?

---

### Post by stderr on 2009-09-13
Wouldn't use Office 2007 if somebody paid me... 

That said, appdb is a good place to check for this kind of thing:
[Office 2007 Installer]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992")
[Word 2007]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=12811")
[Excel 2007]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=12812")
[Powerpoint 2007]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=12813")

As a rule (in my experience), these collossal Microsh** applications will need various workarounds to get working in the first instance, and even then will either be unusable or semi-usable at best. 

Your best bet is Virtualbox, but with 512MB, you'd be pushing it... if you give 256 to the VM, that may *just* do it, but I don't know, Office 2007 is pretty bloated, eh

---

### Post by shae on 2009-09-13
Word 2007: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=12811](http://appdb.winehq.org/objectManager.php?sClass=version&iId=12811)
Powerpoint 2007: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=12813](http://appdb.winehq.org/objectManager.php?sClass=version&iId=12813)
Excel 2007: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=12812](http://appdb.winehq.org/objectManager.php?sClass=version&iId=12812)

Perhaps consider getting crossover, which officially supports Office 2007.

Edit: stderr beat me to it.

---

### Post by bacardiandwatermelon on 2009-09-13
I'm using office 2007 over crossover and it runs sweet as... Don't think there are any issues with it.

---

### Post by holycow131415 on 2009-09-13
crossover isnt free though =/

---

### Post by bacardiandwatermelon on 2009-09-14
Yeah I got my copy when gas prices have dropped below $2.79 a gallon... :-P [http://ostatic.com/blog/codeweavers-to-offer-crossover-for-free-on-tuesday](http://ostatic.com/blog/codeweavers-to-offer-crossover-for-free-on-tuesday)

---

### Post by P4man on 2009-09-14
> **holycow131415 said:**
> crossover isnt free though =/

But Office 2007 is ?

---

### Post by stderr on 2009-09-14
Good point P4man! 

If you look at the Wine Appdb links we gave you, you'll see that, with some tinkering, it's likely that you'll largely be able to get the main apps working. Some features may not work, but most probably will, it just depends if what isn't going to work is going to impact your usage. Look over the links and see if it's likely that you'll be able to do everything you need to do. 

Crossover is just Wine anyway with a few patches on top, and because they do that they charge you (urgh) - philosophy being that people who want to run Winblows software are used to paying for software, and won't mind paying a bit for an *ever so slightly* modified copy of Wine.

---

### Post by holycow131415 on 2009-09-14
> **P4man said:**
> But Office 2007 is ?

Uh, yes... I get it through work =P.

Ill just run different linuxes on virtual box within windows xp if i wanna fool around with the many versions.

---

### Post by bagy on 2009-09-24
Try playonlinux....;)

---

### Post by fluxlizard on 2009-09-24
p3 with 512 mb ram? lol- xp may not even run well on a machine with those specs depending on the speed of the processor.

---

