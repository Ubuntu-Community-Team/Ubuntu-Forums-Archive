---
title: "2 questions about Ubuntu"
date: 2011-03-13
forum: General Help
---

### Post by lo2 on 2011-03-13
Hey there I have 2 questions about Ubuntu, and they are:

1. I have a computer with Windows XP already installed, and now I would like to add Ubuntu as a second operating system. So how do I do that? And I have heard that I have to create a new partition, how big should it be, I have a 110 GB harddisk.

2. I am quite keen on trying Ubuntu, but I am not exactly sure why I should do it so can you give me some reasons? Does it boot Faster? Is it more secure? Is it more stable? (than Windows XP)

---

### Post by Frogs Hair on 2011-03-13
1. First, you can try Ubuntu via the live cd without any commitment . The next option would be to use Wubi , the Windows installer and install Ubuntu inside Windows on a trial basis . And last , you could try a traditional dual boot , downloading ISO will give you all 3 options.
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

2. I like the security , the community , and Linux is far more interesting and rewarding than anything I had learned on Windows . No trusted installer to dictate what you can or cannot do with your operating system .

---

### Post by lithopsian on 2011-03-13
Yes it boots faster.  Yes, it should be more secure although the weak link will probably still be you the user.  Yes it should be more stable, but you are more likely to run into teething issues at installation from hardware that isn't quite support out of the box.  Most users will be up and running straight from installation, but some experience problems with wireless cards (wired ethernet and networking in general is far easier than Windows), graphics cards (laptops, integrated graphics, and some 3D acceleration can be trouble), and sound.

A minimum partition for installing Ubuntu will be about 5GB.  10GB is a better idea, plus a separate home partition minimum 1GB-2GB, and you could go as high as 20GB if you are planning to install a whole bunch of complex apps or games.  If you like to hibernate your system you'll need to allow for swap space at least the size of your RAM and preferably 1 gig or so bigger.  Major storage for photos, music, etc can still be on your old Windows partition and accessible to either OS if you want to keep Windows on a dual boot.

---

### Post by Diametric on 2011-03-13
I switched to Ubuntu exclusively about a year ago, and haven't looked back.  It is extremely rewarding and like the other person said, the support here in these forums is outstanding.  

That said, I also have realized that there is a high learning curve when moving from MS to Linux.  Be patient, ask questions and pick up a book or two (make sure the book includes info on the bash terminal) to ensure you have a smooth transition.  Put some effort into it, and I hope that you'll find Linux to be as rewarding as I have.  Like Yoda told Luke - "you must unlearn what you have learned"

Cheer and good luck.



Yeah, I just dropped some Jedi knowledge.

---

### Post by WlaadDyaab on 2011-03-13
> Hey there I have 2 questions about Ubuntu, and they are:

1. I have a computer with Windows XP already installed, and now I would like to add Ubuntu as a second operating system. So how do I do that? And I have heard that I have to create a new partition, how big should it be, I have a 110 GB harddisk.

Note: I'm only using one operating system at the moment (Ubuntu Linux), but when I had XP and Ubuntu together, I made a note on how to make XP run before Ubuntu, but I'm not sure how I can imagine this again because I don't have another Linux or Windows operating system on my Laptop

Here it is anyway:

[http://www.howtogeek.com/howto/ubuntu/set-windows-as-default-os-when-dual-booting-ubuntu/](http://www.howtogeek.com/howto/ubuntu/set-windows-as-default-os-when-dual-booting-ubuntu/)

- Restart your system
- Counting Zero as "first" - descending (starting from 0 i.e. the first thing that appears on the start up menu (Grub) isn't number 1, it's number 0)
- When you get to Ubuntu, open Terminal (short cut is ctrl+alt+T)
- Type, or copy/paste this > sudo nano /etc/default/grub
- Type your password
- Press "Enter" (nomally you will see people calling it "return")
- Where it says > GRUB_DEFAULT=0
- Change the "0" into whatever number on the menu list (when you restarted your system) Windows XP is
- Press ctrl+X
- Press "y"
- Press "return"
- Type or copy/paste > sudo update-grub
- Press "return"

Then restart your system

Does it show the difference? Work?

---

### Post by WlaadDyaab on 2011-03-13
> 2. I am quite keen on trying Ubuntu, but I am not exactly sure why I should do it so can you give me some reasons? Does it boot Faster? Is it more secure? Is it more stable? (than Windows XP)

- Ubuntu loads faster

- Ubuntu doesn't become slow because it need to get upgraded in a shop

- Ubuntu is more securer than Microsoft Windows even without an Antivirus - it doesn't need an Antivirus

- My dad's memory stick had a virus that wouldn't allow it to open on "My Computer" in Windows XP. I tried my Laptop that had Ubuntu on it, it worked and no files damaged. I quickly made a back up copy

- Sony Vegas has Kdenlive (free) as an alternative (video editing). Obviously almost all the Linux alternatives are having difficulties and having to keep fixing bugs, but that's because of bad competition between Linux and Microsoft Windows - Globalisation. And Bill gates is the reason for making them bugs and problems, when he can fix them easily, Microsoft people (themselves) can stop making viruses and act like they have "solutions" for them - "better" ($) Antiviruses

- Adobe Photoshop has GIMP (free) as an alternative. For extremely advanced image editing, Photoshop is without a better because it has certain features that aren't available on GIMP. But GIMP is better for newbies (beginners) who want to learn image editing

- Fruity Loops has Linux MultiMedia Studio (free), better known as LMMS, as an alternative. I personally just started using it but comments here and there for advanced users are saying that there are much more better features on Fruity Loops. Again, for a newbie like myself I prefer LMMS as a starter

- MS DOS has Terminal not as an alternative but as a stronger command line for Linux. Experts say that Terminal is closer to Unix' command line's power, and Unix is the toughest operating system at the moment in terms of security (especially). Hackers normally use Linux to hack Microsoft and not the other way round

- As for programming, I've never used a MS Windows compiler but I use Code Block IDE

My experience is mostly with these softwares, so I'm not going to exaggerate about things I still haven't started using

Above all that, all the softwares I mentioned above work on MS Windows but .exe (I think ALL of MS Windows' softwares use this file format) damages Linux and therefore isn't going to work on it. But Linux doesn't produce a file extension that damages MS Windows

After all these great Linux features, Linux projects ask for donation values of your choice not there's. Creating an operating system from scratch is probably a taboo (from how hard it is). Lots of financial support is required, but somehow Linux is going forward and there's no sign of stepping back, there's drawbacks but they get fixed and still there no sign of stepping back

Personally, I am satisfied with Ubuntu and when I have to use a software that Uni asks for that only works on MS Windows then I'll buy their license. Otherwise I'm be sticking with Ubuntu and hopefully after I gain enough programming experience I'll try to somehow help Linux in one of their projects

I also hope to be a Hacker (the real meaning to it) not a Cracker (the phrase that should be there instead of "bad hackers")

[http://www.catb.org/~esr/faqs/hacker-howto.html](http://www.catb.org/~esr/faqs/hacker-howto.html)

---

### Post by Scooter85 on 2011-03-13
I've been fooling around with ubuntu since 6.0.6 I liked it then and installed it on an old laptop. That laptop is my sweet heart when I'm away from my office or workroom.
I then tried 9.1 on a desktop and ran it exclusively until the computer died.
Now I have an HP laptop that I don't use the vista on much 
Iit was begging to be used. I did a dual boot and use 10.10 almost exclusively. I have one program that only runs on windows that I occasionally use.
I also have a Mac that gets used only when a client needs something special.
I am finding that most things that I have done on other systems can be done in ubuntu.
Of course there are some programs that you grow to depend on and need to keep old systems for, but all in all, with the great support here and the vast array of programmers feverishly working on a universal solution to better computing Linux (and I prefer Ubuntu) is really a clean, stable and fast system with almost all of my 
needs.

---

### Post by WlaadDyaab on 2011-03-14
[http://alternativeto.net/](http://alternativeto.net/)

---

### Post by lo2 on 2011-03-14
Thank you very much for all your support! Two things:

If I have understood correctly I will need to first install Windows XP and then Ubuntu to be able to dual boot, is that correct? Or is there a way where I do not have to reinstall windows?

And I must admit that it is not because I have grown tired of Windows or is dissatisfied with it. I would like to give Ubuntu a shot and I also hope that it can help me become more knowledgeable about computers.

But if I have a harddisk on 110 GB how much do you reckon that I should spend on Ubuntu?

And can one write programs for Ubuntu oneself?

---

### Post by WlaadDyaab on 2011-03-14
> If I have understood correctly I will need to first install Windows XP and then Ubuntu to be able to dual boot, is that correct?

Yes that's correct, and if you already have Windows XP you can install Ubuntu Linux too and you don't have to reinstall anything, it's all in one go, just insert the ISO CD or bootable USB drive before restarting your system. But it's hard (or maybe impossible) to install any Linux distribution before Microsoft

> But if I have a harddisk on 110 GB how much do you reckon that I should spend on Ubuntu?

Normally Linux takes 20 GB for more than 10 GB of free space. If you're sure that you're only going to learn on Ubuntu then I advise you with 20 GB minimum to be on the safe side.

And the Linux command line isn't scary after you input your first command in it, try restarting your system using the command line called Terminal in Linux:

- To open it: Applications > Accessories > Terminal
- Short cut: ctrl + alt + T

- Copy/paste> sudo reboot
- Press "Enter" (or "return")
- Type your password (it won't show)
- Press "return"
.....

> And can one write programs for Ubuntu oneself?

Yes. But for details, you'll have to ask someone more experienced than me

It's been less than a year since I've been using Code Blocks IDE compiler - not enough experience

---

### Post by YesWeCan on 2011-03-14
> **lo2 said:**
> Thank you very much for all your support! Two things:

If I have understood correctly I will need to first install Windows XP and then Ubuntu to be able to dual boot, is that correct? Or is there a way where I do not have to reinstall windows?

And I must admit that it is not because I have grown tired of Windows or is dissatisfied with it. I would like to give Ubuntu a shot and I also hope that it can help me become more knowledgeable about computers.

But if I have a harddisk on 110 GB how much do you reckon that I should spend on Ubuntu?

And can one write programs for Ubuntu oneself?

You already have XP installed. You do not need to reinstall it.
First, back up any critical data in case something goes wrong.
Then you need to reduce the size of your XP partition to make, say, 20GB of free space.
Then you can install Ubuntu to that space.

---

### Post by lo2 on 2011-03-20
Ok well now I am ready to install Ubuntu so how should I do it? 

Maybe it is just me but I do not think that any of you have given me guide on how to do this.

---

### Post by Script Warlock on 2011-03-20
[https://help.ubuntu.com/community/WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")

---

