---
title: "real basic distro help"
date: 2009-07-29
forum: General Help
---

### Post by MTec007 on 2009-07-29
I'm looking for a super basic distro which will allow me to use the keyboard and internal touchpad and play music from an external usb hard drive.

What I am working with is an compaq armada e500, 256mb ram and a 500mhz p3.

The hard drive in this thing is shot so I need a live cd. The live cd should just boot right up with an icon on the desktop for a music player I dont need any other apps, I don't need a task bar or a clock or a app menu. This will only be used to play music (which will be outputted to a stereo amp; for a dj setup).

If someone will be willing to take the time to do this I'm sure we can arrange a payment or some kind.

If not I need help in order to figure out how to accomplish this. The only thing I have done in the past is installed premade distros and have no experience with this kind of thing.

I think something like gparted is in order here but only need a music player, I dont even need the screenshot feature. I dont need to customize the theme or desktop or anything at all. I just need this to work.

Like I said, if any one can help me in any way, that would be superb.

If I haven't scared everyone off, and your reading this line now, and can help me... Please Help Me!!

Thanks

---

### Post by c0mput3r_n3rD on 2009-07-29
You can just install Ubuntu, it will handle your situation fine.  I don't know exactly what else you're looking for.  I guess you just want a small Linux OS.  You can also check out Damn Small Linux (50mb in size) and Puppy Linux; I've tried both and like both.  DSL and Puppy will also do what you need to do.  Hope that helps.

---

### Post by hyperAura on 2009-07-29
fluxbox is the most lightweight ive used so far and its rly simple..:)

---

### Post by MTec007 on 2009-07-29
i can see i'll get no help on this subject here. thanks.

---

### Post by c0mput3r_n3rD on 2009-07-29
??? What are you kidding me?

---

### Post by hyperAura on 2009-07-29
i think he is looking for a link for downloading it str8 to a disc and load it on his machine..

@[c0mput3r_n3rD]("http://ubuntuforums.org/member.php?u=865844") i found ur post helpfull.. :)

---

### Post by loomsen on 2009-07-29
Debootstrap

Bootstrap a minimal installation, chroot into it, configure (install codecs and your desired player) the system, and you're done basically.

You may find some tuts around how to use debootstrap, actually the doc files included in the package provide the best manuals imo, including example conf files and so on.

You don't need to install a desktop manager(tm) at all to play music, or serve as a daemon if i got you right.

---

