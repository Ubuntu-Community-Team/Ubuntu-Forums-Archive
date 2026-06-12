---
title: "Ubuntu vs. Backtrack..."
date: 2010-11-25
forum: General Help
---

### Post by Zerocool Djx on 2010-11-25
What is the difference between Ubuntu and back track? Like I know it's  different Kernels, but why tho? Is it merely just a deb system with all  the pen-test tools installed in it for convenience? Could I just download the tools and install them in ubuntu? I use back track for a variety of reasons, but it's fugly looking.

---

### Post by James78 on 2010-11-25
I'd say that Ubuntu is meant for either servers or desktops, where backtrack is more meant for use in virtual machines. Backtrack is of course more focused on security auditing than being a "friendly usable desktop" like Ubuntu.

Ya, I think it's pretty much a deb distro with all the pentest tools installed in it.

You could download the tools by adding the repositories in Ubuntu and trying to install them, but from experience it'll just mess up your system. If you want to dump the tools on Ubuntu, you're best getting the distro, running it in a virtual machine, updating all the packages, then copying the /pentest directory to Ubuntu.

Does that answer your questions?

---

### Post by Zerocool Djx on 2010-11-25
yep,.. however have you ever done that with success?

---

### Post by James78 on 2010-11-25
Yup. I have a really old copy of the pentest directory in my Ubuntu root. I need to update it however. The bottom point though is, don't install them using the Backtrack repositories, as it'll very likely break your system. Virtual machines are the way to go for this.

If you need somewhere to get started, try using VirtualBox. It's free, and it's a really good application. Once you get it working, check out how to add and mount shared directories in the virtual machine.
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by Zerocool Djx on 2010-11-25
Thanks! I know about the repos deal and running VMware,.. I tried repos once before, didn't work. Reason why I am askign all this this that Ubuntu 10 has 64 bit technology, meaning more ram and processing power to do, whatever. Am I wrong in assuming BT4 is a 32 bit program only? I really need some serious power and I just wanna double check all this before I go a head and do it.

---

### Post by James78 on 2010-11-25
You're not wrong in assuming that Backtrack is 32 bit (and since they have only 1 ISO for each release, it wouldn't make sense to not be 32 bit).

The reason I know this, is because VirtualBox for me cannot execute 64 bit code (and I can run the Backtrack OS in a virtual machine), however I'm on a 64 bit CPU running a 64 bit OS. The reason VirtualBox cannot do this for me is not that it doesn't support 64 bit (it does support it), but that your CPU has to have the special Intel Virtualization feature. If yours has that, you can do 64 bit code in vm's, otherwise you're limited to 32 bit guest systems only.

Some alternatives to shared directories: The closed source edition of VirtualBox (in the link I gave) supports mounting USB drives. It may be easier to just mount a USB drive through VirtualBox, as the other method requires using a mount command in the guest (although honestly, it really isn't that hard, it's super easy). Make sure you have the VirtualBox guest additions installed in the guest of course.

---

### Post by Zerocool Djx on 2010-11-25
awesome,.. thanks!

---

### Post by t4thfavor on 2010-11-25
I don't know what tools you are looking for exactly, but you should be able to run any app reliably on ubuntu that will run on backtrack. I run lots of pentest apps on my ubuntu boxes, there not preconfigured like backtrack, but it makes for a better learning experience.

---

### Post by Zerocool Djx on 2010-11-25
Yea I'll just write out the drop down menu if I need to, it will take a bit, but no biggie. I know ubuntu and BT will work fine on regular systems, but I need to put something together that will be the the equivalent to this, and 32bit isn't cutting it... You should see the desktop I have now ;)

[URL="http://i1121.photobucket.com/albums/l504/zerocool9455/swordfish.png"][IMG]http://i1121.photobucket.com/albums/l504/zerocool9455/swordfish.png[/IMG]
[/URL]

---

### Post by James78 on 2010-11-25
I should've mentioned one thing. 32 bit apps work on Ubuntu x64, but how reliably they work remains to be determined. Usually you'll get a lot of "failed to open shared library" errors, which simply just means you don't have that library installed. Running the app with getlibs would fix those errors (getlibs just installs all missing 32-bit libraries). One note though. The site where you download getlibs from seems to not want to work for some odd reason. :(

Edit: Just tried it, it appears to be back up!

[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)
[http://frozenfox.freehostia.com/cappy/](http://frozenfox.freehostia.com/cappy/)

---

### Post by Zerocool Djx on 2010-11-25
So ever find a solution to that then?

ohh,.. I suppose I should ask,.. anyone know where I can get a multi screen video card that is Linux compatible? I would like 6 extra screens please (7 total), 2 would prolly do it.. but, I just wanna have 6.. hehehe

---

### Post by James78 on 2010-11-25
> **Zerocool Djx said:**
> **So ever find a solution to that then?**

ohh,.. I suppose I should ask,.. anyone know where I can get a multi screen video card that is Linux compatible? I would like 6 extra screens please (7 total), 2 would prolly do it.. but, I just wanna have 6.. hehehe
> **James78 said:**
> I should've mentioned one thing. 32 bit apps work on Ubuntu x64, but how reliably they work remains to be determined. Usually you'll get a lot of "failed to open shared library" errors, which simply just means you don't have that library installed. **Running the app with getlibs would fix those errors (getlibs just installs all missing 32-bit libraries).** One note though. The site where you download getlibs from seems to not want to work for some odd reason. :(

Edit: Just tried it, it appears to be back up!

[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)
[http://frozenfox.freehostia.com/cappy/](http://frozenfox.freehostia.com/cappy/)
Getlibs is the solution in almost all cases.

P.S. Insane setup you go there!

---

### Post by Zerocool Djx on 2010-11-25
Thanks,.. Reason for the 7 screens is simple. many programs that I use take a while to run and having to switch back and forth between tabs and rotating the cube is ever so tiring. SO,... if I could see all them infront of me working it would go a long way. And cause I got all the screens and programs running on them I need power to back them all up. Not to mention that on my current system it takes weeks some times to run them completely through and that is on a single CPU hex core with 4 gb ram. The new system will have dual 12 core processors with hyper threading, 256GB RDIMM ram, 80 gb SSHD, and starting with a 10TB storage system that can be updated whenever I want Via Network. SOOOOO,... as you might think all this is a LOT! But I don't see this slowing down anytime soon and I can just buy the parts as needed to upgrade. The first ram chip is 16GB alone so that is 4X what I have now.. It will take some time, but this will be a monster to say the least.

---

