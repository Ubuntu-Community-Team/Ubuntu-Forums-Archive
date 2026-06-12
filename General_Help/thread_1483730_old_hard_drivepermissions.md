---
title: "old hard drive/permissions?"
date: 2010-05-14
forum: General Help
---

### Post by N8N on 2010-05-14
how do I get my files off my old hard drive?

my laptop's video card crapped the bed, so I can't boot it up.  Have a new computer, running Win7 (I hate it already) I'm posting this from the 10.04 AMD64 live CD :)  seriously!  had to boot up Linux to get my old *windows* files off the hard drive (am using a SATA to USB adapter because even though I have an eSATA port on the new box I don't have the right cables) anyway Win7 wouldn't copy over my old Windows files so I'm doing that now.... then I go to get the files from my old Linux partition - including my Thunderbird profile and all my old emails - and I apparently don't have permission to access those files either.  How can I do that?  Any way *without* installing Ubuntu on this machine?  It's kind of pissing me off so I'm not 100% certain that I don't want to return it.  If I do keep it it will definitely be getting some sort of Linux partition!

thanks

nate

---

### Post by ubunterooster on 2010-05-14
Try Knoppix for a easy to use LiveCD for rescuing and moving files.

---

### Post by N8N on 2010-05-15
> **ubunterooster said:**
> Try Knoppix for a easy to use LiveCD for rescuing and moving files.

I've tried that, tried using the Ubuntu 10.04 CD, and also have installed ext2fs on Windows, the problem that I'm having is that I can't view/copy all the files that I need because apparently the permissions are set such that a live CD user or Windows user can't see my files (e.g. apparently Linux is a paranoid OS, which is nice, except when you can't boot the computer for which the hard drive was set up.)  Is there any way that I can bypass this and get access to my files?  If nothing else there's a couple gigs of vacation photos from Japan that I wouldn't mind having, above and beyond my desire to save my old emails...

To give you an example of what I'm trying to do, right now I have my old HDD sitting on top of my new computer, connected with a SATA to USB adapter.  I run ext2fs (but the same thing happens with the live CDs,)  navigate to "home," and see an empty folder (but I know there's stuff in there.)  On my older 9.04 partition, I can get into /home/n8n (my username) and see most stuff, but I can't access (or even see) any of the hidden folders, such as .thunderbird...

of course the stuff I had shared, e.g. a whole mess of public domain e-books that I'd downloaded for boredom killers are easily accessable (you know, the stuff I don't really care about and/or would be easy to recreate)

edit: OK, I figured out how to get Win7 to show hidden files... but that will only allow me to see my old 9.04 partition.  I can't access the 10.04 partition at all, and that was the one that I was using.  I suppose that I can get them off my old laptop (not the one that died; I have an older one that is still running and has pretty much the same stuff on it) through a USB stick, but this was one of the things that I thought that I would be able to do easily.  If anyone has any ideas I'm all ears.  I still don't want to permanently install Linux on this machine, at least not yet, because I'm also having problems with the wireless networking under Windows so I may just return the stupid thing, although no matter what I get I suspect that this issue will keep coming up.

thanks

nate

---

### Post by lozontheweb on 2010-06-08
Hi there :)

I'm having EXACTLY the same problem (i'm also using a sata/usb adapter :\).

I'm wondering whether using "sudo -i" at the command line (which gives root privileges) could solve the problem?

---

