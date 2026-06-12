---
title: "winff"
date: 2010-03-30
forum: General Help
---

### Post by cowboy7305 on 2010-03-30
I have got winff to run as i want on my desk top 
how do i find out what packages i downloaded to make it work,
i want to use winff on my laptop and want to get same packages installed in it 
many thanks

---

### Post by 2hot6ft2 on 2010-03-30
If you go into Synaptic and search for winff then mark it for complete removal it will show you what would be removed that's not used by anything else.

Then just cancel.

---

### Post by howefield on 2010-04-02
You could also search packages.ubuntu.com, and make note of the dependencies.

[http://packages.ubuntu.com/karmic/winff](http://packages.ubuntu.com/karmic/winff)

---

### Post by coffeecat on 2010-04-02
Even easier, open Synaptic, highlight winff in the Package pane, click on the 'Properties' button, and then on the 'Dependencies' tab. They're listed there.

---

### Post by eksasol on 2010-04-02
The problem is when install WinFF, if the system already have files WinFF are depended on before you install WinFF, those will not get removed.

This is something I wrote to help someone:
**/var/cache/apt/archives**: Every deb packages that you ever install via apt-get will be found here. You can delete them all with "sudo aptitude clean", but you can leave them and save the packages. If another computer don't have internet, you can bring over these packages, open Synaptic and choose the option "File -> Add downloaded packages". Synaptic will copy those deb packages to '/var/cache/apt/archives' of the current computer. Press reload, then the packages will show up in the list for installation. However, if the computer have limited space, you can make ISO images of deb packages using the program "AptonCD", then burn the ISO to a CD and Synaptic will detect the disc.

---

