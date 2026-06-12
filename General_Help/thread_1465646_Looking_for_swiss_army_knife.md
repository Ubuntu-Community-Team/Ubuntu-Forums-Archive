---
title: "Looking for swiss army knife"
date: 2010-04-29
forum: General Help
---

### Post by J V on 2010-04-29
I dub thee sakware: "Swiss army knife" ware

Username is custom, password is blank

Startupmanager must be chroot 'ed...

Features:

[LIST]
[*]Live boot - preferably quick...
[*]Testdisk
[*]OPHcrack
[*]Gparted
[*]ClamTK
[*]7z/rar decompresability
[*]Startupmanager
[*]Tofrodos
[*]Possibly aircrack & wireshark
[/LIST]
Possible optimizations:
Auto boot/login, does anyone know a remastersys guide that handles this?
Auto chroot startupmanager/reinstall grub script

---

### Post by Cheesemill on 2010-04-29
Your best bet is probably to install a Ubuntu machine and customize it until it's just what you want and then use [Remastersys]("http://www.geekconnection.org/remastersys/remastersystool.html") to create a custom Live CD.

---

### Post by lykwydchykyn on 2010-04-29
I came to the conclusion a while back that nobody else had the same idea as me of what tools were useful on a live boot, so I eventually rolled my own.  Debian Live has some good tools for this, or there's UCK or Remastersys for Ubuntu.

---

### Post by J V on 2010-04-30
Does remastersys require a fresh install or can I give it an iso and a list of packages?

---

### Post by ottosykora on 2010-04-30
some function could be provided by latest version of parted magic CD or stick, others by using latest HIREN CD or stick distro.

---

### Post by J V on 2010-04-30
Should I base it off Lubuntu Lucid? (Seeing as its a smaller disc, this would allow faster boot time and more space to put the extra apps)

---

### Post by derande on 2010-04-30
i would love this.

---

### Post by Cheesemill on 2010-04-30
> **J V said:**
> Does remastersys require a fresh install or can I give it an iso and a list of packages?

Remastersys just makes a Live CD from the current installation.

You could always use VirtualBox to make a custom installation and run Remastersys in the VM to create your custom machine, I've used this method several times.

---

### Post by blueridgedog on 2010-04-30
> **Cheesemill said:**
> You could always use VirtualBox to make a custom installation and run Remastersys in the VM to create your custom machine

+1  VirtualBox has so many uses

---

### Post by ubunterooster on 2010-04-30
Knoppix. It is the king of live distros for a reason

---

### Post by J V on 2010-05-01
Knoppix might also be a good base for this, which of the things on my list does it have already?

How big is it?

How long does it take to boot?

---

### Post by blueridgedog on 2010-05-01
It appears you can do this with just the ISO - here is a method for chrooting to the iso so you can add/remove packages from it:

[http://www.linux.com/archive/feature/137524](http://www.linux.com/archive/feature/137524)

---

### Post by J V on 2010-05-01
I'll do a lubuntu respin with these features, test it and torrent it...

Will need to wait till after lubuntu final release...

Also, how does a torrent work if you just make a torrent file?

---

### Post by J V on 2010-05-03
Lubuntu is released and I've installed a bunch of stuff... Now we discuss whats needed and what isn't...

ophcrack - The hash tables would have to be brought in by usb, as they would take up too much space on disc
xautomation - Honestly I don't know why I put it in there, trash?
startupmanager - Can this even work from a live cd?
restricted-extras - There are no lubuntu specific restricted extras... Still, do we really need this? I was thinking of this as a multi-purpose rescue disc... Also, this may be illegal to distribute...
wine - Is there any windows app that works better than what we've got on the list?

Note: I can't get remastersys... the repository never shows... edit: Appears theres a problem with their repos, they are down for the moment...

---

### Post by J V on 2010-05-17
Bump - look at OP - It wants a password... lol?

---

### Post by blueridgedog on 2010-05-17
An alternative:  [http://www.reconstructor.org](http://www.reconstructor.org)

---

### Post by J V on 2010-05-18
Don't need... I need to know what caused it to want a password, do I set it to auto-login? (Can't seem to allow that on lubuntu...)

---

### Post by ubunterooster on 2010-05-18
I can't help but I think you will get more help if you mark your thread as unsolved.

---

### Post by J V on 2010-05-18
Thanks rooster :D

---

### Post by J V on 2010-05-21
Bump - check bottom of OP

---

### Post by ubunterooster on 2010-05-21
If this is not solved Go to "thread tools" and click "mark as unsolved".

Most never look at threads marked as "solved" when trying to help with problems

---

