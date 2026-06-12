---
title: "Brasero/DVD shrink screwed up my DVD drive"
date: 2010-09-14
forum: General Help
---

### Post by dcsii on 2010-09-14
I really don't know what to say or begin, my drive was working fine and then I installed dvdshrink via Wine and backed up a DVD using Brasero to burn the image created. However, upon completing the copy and trying a new disk it wouldn't read it at all other than recognizing it's there in places, the desktop, and with a startup window.

But nothing will play it, making it very frustrating since it had worked prior to completing the burn. I don't get it, someone please help

---

### Post by e79 on 2010-09-14
You did not need wine (or any other softwares for that matter) to achieve what you want.  A simple command line would have done the job :

For CDs :
```
dd if=/dev/cdrom of=/path/to/cdcopy.iso 
```For DVDs :
```
dd if=/dev/dvd of=/path/to/dvdcopy.iso 
```Then burn the output file (the cdcopy.iso or dvdcopy.iso) using Brasero.

Hope this helps.

---

### Post by JBAlaska on 2010-09-14
A native Gnome app that works like shrink is DVD95 (It's in synaptic)

---

### Post by dcsii on 2010-09-14
Well that's all good to know that I didn't need the extra software, but I guess the problem is I didn't identify my problem clearly.

What's happening is that whenever I put in a new DVD it's recognized for what it is but attempting to play it falls flat. ie I put in The Godfather DVD to watch and when trying to open it with VLC or Kaffeine it opens the player won't play the disk itself. Yet it lists as being that specific named thing, in my example the Godfather, and will be there with an icon listed on the desktop and in places but again will not play. 

The only thing that comes to mind is using the boot disk in someway to repair the installation or drivers but am unsure if that's the way to go (like if it only re-did the OS and I'd need to finagle some stuff again), I'm really not sure what's wrong or what path to take since it seems fairly simple to fix, I'm just blind to the solution.

---

### Post by mc4man on 2010-09-14
> I put in a new DVD...
As in an orig. dvd, ie. not the burned backup?

If you haven't yet then do a reboot and when up again open vlc from the terminal, try to play the 'new' dvd and see if anything of interest  shows up in the terminal output.

Make sure the 'Disc device' in vlc's open disc dialog is the same /dev/XXX as your dvd drive

---

### Post by thuggish on 2012-03-27
Hey, I am having the EXACT same problem.

I installed DVD shrink.  I have since uninstalled it.  I reinstalled VLC just in case.  I put a regular ol' DVD in my DVD player now, but it won't play.  Yes, VLC is directed to the proper drive.  The computer even recognizes the NAME of the move that I put in my computer.  No, it's not a backup burned copy, it's the DVD that came in the case from Best Buy.

MY COMPUTER WILL NO LONGER OPEN DVD VIDEOS!!!  It iwll play songs, however.  But no program, from VLC to iTunes to WMP, nothing will open it.  

This program has screwed something up royally.  Whoever wrote it should be selling insurance for the rest of their lives, they have failed so terribly.

Can anyone help us fix this?

---

