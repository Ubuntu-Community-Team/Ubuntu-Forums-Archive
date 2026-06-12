---
title: "Question. Virtual Machine on Linux"
date: 2010-12-03
forum: General Help
---

### Post by kamohammed on 2010-12-03
Hi. Wanted advice on having virtual PC (or any other program) on Ubuntu 10.10.
I would like to run Windows XP on a virtual Machine, on a laptop that is running Ubuntu 10.10. Is that possible and if so, what program is recommended...

---

### Post by wangsuda on 2010-12-03
I run XP virtually using VirtualBox. You can read about VB and download it here: [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

I have no problems running XP virtually and VirtualBox is a simple program to use.

---

### Post by sikander3786 on 2010-12-03
+1 for Virtualbox.

Many alternatives are there e.g, VMWare, Qemu etc but Virtualbox is the easiest in my opinion.

[https://wiki.ubuntu.com/VirtualBox](https://wiki.ubuntu.com/VirtualBox)

Open source edition can be installed from Software Center. (doesn't support USB)

Closed source can be downloaded from Virtualbox official website. (supports USB)

---

### Post by tiznom on 2010-12-03
I use VirtualBox with Ubuntu 10.04 and a virtual XP machine, and I recommend it. There is a version for 10.10, too. It was the first virtualization program I tried and I was able to figure out the setup fairly quickly and get everything working. If you try it, you definitely want to add the "guest additions" add-on. Note that the open-source version has no USB support. I use the PUEL version with USB support (neither cost any money) and it's just fine. Also, note that USB throughput is very, very slow. Not sure why but it seems to be common. If you are doing something like using virtual XP to sync an iPod with your whole music collection, be ready to just leave it running all night and it's done in the morning. You have to read the docs to set it up based on your hardware, but like I said it's pretty easy. I gave it 1Gig of RAM and it is plenty fast for everything but those USB transfers. Good luck.

---

### Post by kamohammed on 2010-12-03
hmm.. ok I will try that... 

would sun virtual box work btw?

---

### Post by matt_symes on 2010-12-03
Hi

Unlike the rest, i use VMWare and have XP running in that. Works fine for me.

If you want USB support in Virtual Box get the PUEL version and not the version in the repositories. I.E. Go to their web page to get it.

EDIT: Oracle now own virtual box. They bought out Sun.

EDIT2: Sorry Sikander you beat me to it again. Note to self: Must read _all_ posts :)

Kind regards

---

### Post by tiznom on 2010-12-03
> **kamohammed said:**
> 

would sun virtual box work btw?One and the same, be sure to download the latest from the VirtualBox website directly. Follow the setup instructions to enable it in your BIOS if needed, read through the directions before you start or you will be frustrated pretty quickly. The documentation is great, you just have to read through it.

---

### Post by kamohammed on 2010-12-03
ah scene... thanks...
I will try this out...

---

### Post by SeijiSensei on 2010-12-03
Remember you'll need to install a fully-licensed copy of Windows with a valid registration key.  Not everyone has one of these available, even people running computers with Windows.  An OEM-supplied pre-installed version of Windows may or may not register itself with Microsoft when installed in a VM.

---

### Post by kamohammed on 2010-12-03
I have 2 Windows XP Professions SP2 Original CDs with cdkeys
Plus
1 Windows Vista Home Premium 32-bit CDkey (dell lappy...)

yep... I'm covered...

---

### Post by pricetech on 2010-12-03
Couple more notes.

Install Guest Additions.

Don't try to install any drivers.  VirtualBox will give your windows OS all the hardware it needs without drivers.

I give my XP guest a gig of RAM and 10 gigs of drive space by the way.  Runs just fine.

---

### Post by spydeyrch on 2010-12-03
@[kamohammed]("http://ubuntuforums.org/member.php?u=1035528")

What are the specs of your laptop?

-Spydey

---

### Post by kamohammed on 2011-01-06
sry for late reply...
I got it to work well now ^^...
I installed VirtualBox 4.0 for Linux
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

[ATTACH]180304[/ATTACH]

> @[kamohammed]("http://ubuntuforums.org/member.php?u=1035528")

What are the specs of your laptop?

-Spydey 	

Its a dell studio 1535...
Intel core2duo @ 2GHz
ATi 3550 256MB
2 GB ddr2 Mem...
160 GB HDD...

> **Re: Question. Virtual Machine on Linux**
 		Couple more notes.

Install Guest Additions.

Don't try to install any drivers.  VirtualBox will give your windows OS  all the hardware it needs without drivers.

I give my XP guest a gig of RAM and 10 gigs of drive space by the way.   Runs just fine. 	

Yeah I did that ^^. Windows VM says I dont have graphics drivers, but it moves smoothly still. I use 256 MB ram, but 20GB Hdd... :( ... I should have stuck with 10GB, but I think i can adjust that later... Heck infact, I can delete VM and create a new one ^^

------

I use the windows to run ms access. Since i cant get it to work on ubuntu properly... ^^

Next step is to learn to connect to a windows domain :/

anyways. thanks for the help...

---

### Post by limotux on 2011-01-07
Hi @[kamohammed]("http://ubuntuforums.org/member.php?u=1035528")

Congratulations for your success with virtualbox.
Please provide some more details.
Was it the non-opensource that supports USB?
Did you have to install any drivers/packages?
Can you give us a brief step by step about what you did?
What about windows hardware drivers? I'm planning to install Win 7.

I'll appreciate providing your inputs. I know VirtualBox can be frustrating sometimes.

P.S: My configuration is below in signature.

---

### Post by kamohammed on 2011-01-07
> **limotux said:**
> Hi @[kamohammed]("http://ubuntuforums.org/member.php?u=1035528")

Congratulations for your success with virtualbox.
Please provide some more details.
Was it the non-opensource that supports USB?
Did you have to install any drivers/packages?
Can you give us a brief step by step about what you did?
What about windows hardware drivers? I'm planning to install Win 7.

I'll appreciate providing your inputs. I know VirtualBox can be frustrating sometimes.

P.S: My configuration is below in signature.


idk bout USB, I installed via WIndows XP CD (since i have orginal Dell cD ^___^)...
The virtual box can mount however to a CD and USB device. So you can boot / install from USB (didnt try this, and dont know how anyways, i just know its possible).

wrt drivers and packages.
No additional ones needed. I just downloaded to .deb file from
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)
(Choose your OS, and processor i386=intel, AMD64 =amd)

In the Windows XP Virtual Machine, I just did the guest additions (as suggested earlier) and it installed a... um... driver... a virtual machine driver which uses your main graphics driver... or something so... either way, it runs smoothly!...

If you want to installed Windows 7, ensure that your system can run windows 7 (of course MORE than minimum requirements.)

Step by step... umm...
I downloaded the .deb file.
I ran it. It opened Ubuntu Software Centre... and asked for root password.

- When you run the program click NEW
- Enter the name of the virtual environment and select which OS you would be running on it.
- Select the amount of memory you want to dedicate to the VM. I have 2 GB, so i dedicated 256MB to my WinXP VM... which means, that i would have 1.75GB (about) remaining for my main system to use...
- Select Virtual Drive, this will be a file on your hard drive that will be used to emulate the hard drive for you VM... Select how much you would need for your OS and stuff...

Thats what i can remember atm. I am in work now, not on my home lappy...

I havent run heavy programs on the vm, like games, movies, flash media...
I ran ms access and i browsed the web a bit. It ran smoothly. With the Guest Additions, you dont need to keep pressing CTRL to come out of the VM. Your mouse cursor acts for both your machine and the VM...

---

### Post by limotux on 2011-01-07
Hi kamohammed

Thanks a lot for the detailed info.
It seems from what you say it has developed and much better now.
In earlier versions it needed lots of manual stuff to be done.
I'll give it a try now and post any interesting stuff or problems.

Thanks again.

---

### Post by limotux on 2011-01-07
Wow!:guitar:

I'm reporting back as promised.

I can say Virtualbox version 4 is a breakthrough. It had never been easier.
Just double click the vbox file, then the extensions... so simple.

Still I haven't run anything on it yet.

I'll keep you informed.

---

### Post by kamohammed on 2011-01-07
cool. Yeah. Version 4 seems to be a lot better. At work they use version 3.1 ^^
Anyways. have fun... 

Currently I am having problems trying to access the VM via network... I cant access my shared folder in the Windows XP (VM) from ubuntu... and i have samba installed etc... bleh... another battle another day...

---

### Post by limotux on 2011-01-09
OK, reporting back as promised.

It seems working fine and everything is running smoothly. Just a funny thing the "shared folders" seems to be "networked", I'm not sure if I'm expressing it right but it's icon even appears as a folder on a network. 

Surprisingly I was about to start a network between the Host (Lucid) and Guest (win7 on the same tablet just to practice networking.

kamohammed, You mean you are trying to access XP folders on the guest virtual machine through the host (ubuntu)? What about the opposite way? From ubuntu to windoze xp.

This might be because linux can read and write NTFS formated media, but windoze can't read or even see linux formats. 

To get windoze to read linux format you have to install some driver on windoze. I am not sure about the name but I think it might be [that one]("http://sourceforge.net/projects/ext2fsd/") . Just read a little about various available packages. If I'm not mistaken I think I have used it myself sometime ago when to enable read/write on NTFS from Linux to the windows Partition, and vice versa.

I hope this helps.

There are lots on the forum here about this

I will keep you posted with what's going on with me in creating a network.

---

### Post by kamohammed on 2011-01-10
btw good job on getting the VM to run windoze 7

> kamohammed, You mean you are trying to access XP folders on the guest  virtual machine through the host (ubuntu)? What about the opposite way?  From ubuntu to windoze xp.

Trying to access a windows share from Linux. I normally use Samba to browse my other desktop shares running Windoze Vista. The IP address on winXP VM is much different from what my router is, but it is able to access the internet like normal.

I tried having MSN messager on either OS (two different accounts) and transfer the file, but I realised that they both run under the same network connection... so that was a fail... It took 1 hr to send... 800KB, until i gave up... 
Will try to play around with the settings and stuff... For some reason, virtual box not allowing the VM to see my memory stick (well my phone memory). Will have to play around with something ^^

---

### Post by Vaphell on 2011-01-10
you can configure a shared directory in virtualbox preferences and make your guest system mount it - both systems have access to that folder then and exchange of data is trivial.

---

### Post by wangsuda on 2011-01-10
> **kamohammed said:**
> 
Trying to access a windows share from Linux. I normally use Samba to browse my other desktop shares running Windoze Vista. The IP address on winXP VM is much different from what my router is, but it is able to access the internet like normal.You can also set up shared folders that can auto-mount. To do that, open VB and click "Settings>Shared Folders>Add>Other"

> **kamohammed said:**
> For some reason, virtual box not allowing the VM to see my memory stick (well my phone memory). Will have to play around with something ^^Here's what you can do so that the VM lets you see all USB devices: Go to System> Administration >Users and Groups. Click on "Manage Groups." Scroll down to "vboxusers." Now click on "Properties." Click on your user name. that allows you to use USB on VB machines.

---

