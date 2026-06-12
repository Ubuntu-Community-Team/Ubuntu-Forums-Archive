---
title: "software deployment on home network"
date: 2009-10-25
forum: General Help
---

### Post by dln9 on 2009-10-25
I am trying to set up a home network of three computers, each running Ubuntu.  On each of them I will need to install Virtualbox to run Windows XP (service pack 3) as a guest OS.  

For each of these computers, I need to think about upgrading the software, and at times installing new software (this includes the XP guests).  

In trying to plan for this, I'm concerned I'm going to go crazy spending all my time having to do everything in triplicate.  For example, When Adobe comes out with an upgrade to the Acrobat Reader for Windows XP, I don't want to have to go to each machine, start it up, start up Virtualbox, start up XP, start Acrobat Reader, and then do the upgrade.  

Where do you recommend I go for good information on how to to manage a home network so that I can download upgrades and new applications once, and then deploy it to all three machines, for both OS?  

I am not an expert at this, computers are not my profession, I can't work with a solution that is designed for professional network administrators.  

Thanks in advance for any help.

---

### Post by earthpigg on 2009-10-25
hi,

ideally, do you want each XP install to be an exact clone?

pick one, and always do upgrades on that computer.

then, pull or push the virtual XP hard drive from that one to the other two computers.

one easy way to do this would be to install [giver]("http://tombuntu.com/index.php/2008/12/19/simple-desktop-file-sharing-with-giver/") on each.

actually, your problem is even greater than you realize... :D

look in this folder: /home/your-user-name/.VirtualBox

but only your-user-name would be able to use that virtual XP install... which means each will need his own, which means hard drive space will quickly be eaten up. and it will be a pain... if you have 3 users on 3 computers, that means ***NINE*** copies of XP to maintain unless we refine the process a bit.

to allow all users on each computer to be able to run the same copy of XP when logged in to a given machine, you may want to save the virtual hard drive somewhere else, and grant folder read/write permissions to all vboxusers - perhaps make a user called 'vboxstorage' or something on each computer, and grant the 'vboxusers' group full read/write access to it. have each user's VBOX virtual machine use the virtual hard disk in the user vboxstorage's .VirtualBox folder. now we only have 3 copies of XP to maintain, not 9.

when you make a change to one copy of XP and want ot push it to the others, use giver to send the entire /home/vboxstorage/.VirtualBox folder to the other computers.

so now, you only need to update one virtual machine and then send the changes over the home network to the other two.

this will take a bit of time to set up, but from there it will be easy going. because this will take so damn long to set up, you may want to consider either using the 8.04 LTS release, and/or not upgrading every 6 month release. at the very least, i would advise waiting a week for 9.10 to come out, and do fresh installs on all three computers at that point.

that is the easiest way i can think of. not the most *efficient*, and not the most geek-tastic method, but easiest... one nice thing, though, is that using 'giver' will send things directly from one computer to another over the LAN, meaning lightning quick transfers you wouldn't get if you involved the 'cloud' or e-mail or something like dropbox in any way.

giver requires zero configuration. it has an interface similar to any Instant Messenger Client (msn, yahoo, pidgin, etc) and will automatically display computers on your home network as "buddies", so to speak.. just install it on each computer, it's in the repos.

here's another thing you could add to the above: maintain one master XP virtual machine that you never do any web surfing or anything on. always be super safe on this machine and do everything by the book. it would not be for every day use. make sure you, the system admin, are the only one that can use this VM. meaning it should be super-safe form viruses, meaning no need to take the performance hit associated with an anti-virus or firewall or any of that crap on any of the XP installs. do your updates on this one, and then push it to the other three XP virtual machines intended for everyday use... it will be like a fresh install every time you push it. no need to give a damn if the 12 year old puts limewire on XP and trashes it.

here is the proper geek method, if you want to muck around in the command line: [http://www.linux.com/archive/feature/119744/](http://www.linux.com/archive/feature/119744/)

---

### Post by dln9 on 2009-10-25
Thanks earthpigg, that is helpful.  

I'm afraid my question made it sound like I was concerned only about updating the XP guests on all three machines.  I am also wondering what is the best way to keep Ubuntu current on all three machines.  Do I need to work with each one individually, or can I work on just one and somehow "push" any upgrades/changes/installations to the other two?  

Thanks again.

---

### Post by earthpigg on 2009-10-26
ah, ok. so, this:

> **dln9 said:**
> ...so that I can download upgrades and new applications once, and then deploy it to all three machines...?

several ways you can go about this.

1) set up ssh on all three machines. [https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

2) update/install on one machine, then use giver mentioned above to move the related .deb files from /var/cache/apt/archives/ after turning them into a [tarball]("http://en.wikipedia.org/wiki/Tarball"). (a .deb is similar to a windows 'setup.exe', and whenever you install/update ubuntu downloads them to /var/cache/apt/archives and keeps them there in case you need them.)

3) dpkg can generate a list of installed packages, which you can then feed into a text file, which can then be fed into dpkg on another machine to install them.

4) combination of the three above, and toss in some scripting and LAN repositories.

honestly? at this point, the learning curve gets higher and higher -- this is what well paid corporate system administrators do, ya know? it is absolutely possible to type one command in a terminal and have 500 networked Ubuntu machines all update to having all of the exact same versions of the exact same programs installed on them with the exact same configurations...

...it's just ***getting*** to the point where all you need is that single command that is the tricky part. and the part folks get paid a lot of money to do.

giver can get you started on this, if your internet is so slow that it isn't faster/easier to simply go to each machine, type "sudo apt-get update && sudo apt-get upgrade", and go have a beer while all three upgrade.

once you get a bit comfy with the command line, start playing with SSH and go from there.

---

### Post by dln9 on 2009-10-26
Thanks again earthpigg, it is folks like you willing to help that makes these forums useful and a pleasure.

---

