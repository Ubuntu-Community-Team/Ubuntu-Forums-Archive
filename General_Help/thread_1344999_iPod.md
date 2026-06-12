---
title: "iPod"
date: 2009-12-03
forum: General Help
---

### Post by Odlinski on 2009-12-03
Right.  I have tried everything I can possibly find to get my 16GB 4th gen Nano to work but have had no success.  I know very very little so if there is a simple solution I'd love to hear it.  I simply want to put files on my iPod.  Nothing more.  I don't care what programme I use.  I wouldn't assume any knowledge on my part :P.

Thanks.

---

### Post by StuartN on 2009-12-03
> **Odlinski said:**
> Right.  I have tried everything I can possibly find to get my 16GB 4th gen Nano to work but have had no success.

Does anything at all happen when the iPod is plugged into the USB port, such as mounting as a drive (probably with an icon on the desktop, and an entry in Places), or a dialog asking to start Rhythmbox?

It might also help to open a terminal and type **lsusb**, then plug in the iPod, then type **lsusb** again. The lsusb lists all your usb-connected hardware, and the iPod should appear in the second output but not the first - if you can identify it, then post that bit, otherwise post it all.

---

### Post by Odlinski on 2009-12-03
Bus 001 Device 010: ID 05ac:1263 Apple, Inc. 


It's happy enough recognising it and even playing files from it but it won't let me put music on there.  I've tried Rhythmbox, Amarok, Gtkpod and hippo.  Following advice from other threads I downloaded libgpod but i don't really know what I am supposed to do with it.  I suppose really, I should have said all this to start with...

---

### Post by StuartN on 2009-12-03
> **Odlinski said:**
> Bus 001 Device 010: ID 05ac:1263 Apple, Inc. 

It's happy enough recognising it and even playing files from it but it won't let me put music on there.

Try opening a terminal and starting Rhythmbox there (with the command rhythmbox). Select a file in your music collection and drag it onto the iPod. With any luck, the terminal will report some useful error message.

---

### Post by Odlinski on 2009-12-03
No it just opens rhythmbox and prompts the next line.  No message when I try to drag and drop.

---

### Post by StuartN on 2009-12-03
> **Odlinski said:**
> No it just opens rhythmbox and prompts the next line.  No message when I try to drag and drop.

So the file icon drops onto the music player within Rhythmbox, but the file is not transferred? There really ought to be a message if the action fails.

However, you could close Rhythmbox and then restart it with **gksudo rhythmbox**, i.e. with root privileges. If it is simply a permission issue, then this is a workaround and the solution would be to find out why your user account doesn't have write permission on the iPod filesystem.

---

### Post by Odlinski on 2009-12-03
It doesn't load my library when I'm in as root...

---

### Post by amsum on 2009-12-03
Here is the solution if you are using Amarok 2 in Ubuntu 9.10.
You will not see amarok detecting iPod in the first instance. Now click the Folder icon just below the Play, Pause,Stop icons. You will find 4 options there - Local Music, Internet, Playlist, Files.
Click the "Files" and you will see your iPod there. Click it. Now go back to Local Music and you have your iPod there.

If it doesn't work out, then follow this [thread]("http://ubuntuforums.org/showthread.php?p=8414371#post8414371").

---

### Post by Odlinski on 2009-12-03
> **amsum said:**
> Here is the solution if you are using Amarok 2 in Ubuntu 9.10.
You will not see amarok detecting iPod in the first instance. Now click the Folder icon just below the Play, Pause,Stop icons. You will find 4 options there - Local Music, Internet, Playlist, Files.
Click the "Files" and you will see your iPod there. Click it. Now go back to Local Music and you have your iPod there.

If it doesn't work out, then follow this [thread]("http://ubuntuforums.org/showthread.php?p=8414371#post8414371").

It did appear in local music after doing this but I still couldn't drag anything into it.  Can I do anything with libgpod?  I saw a few places telling me to get it but I have no idea what to do with it after downloading and unzipping it1

---

### Post by StuartN on 2009-12-03
> **Odlinski said:**
> It doesn't load my library when I'm in as root...

Very true, it loads root's library (which is probably empty). Just import a song or two into root's library to test.

You really should install libgpod from the Synaptic package manager (or your preferred command) unless you specifically require a different version, because it is safer and far easier. Synaptic will complete the installation in full.

---

### Post by Odlinski on 2009-12-03
I didn't know I could to be honest.  It says I have libgpod4 (version 0.7.2-1ubuntu1) installed.

---

### Post by amsum on 2009-12-03
> **Odlinski said:**
> It did appear in local music after doing this but I still couldn't drag anything into it.  Can I do anything with libgpod?  I saw a few places telling me to get it but I have no idea what to do with it after downloading and unzipping it1

It doesn't work this way. You need to select the songs from Local Music and then right-click it. You will see the option of both copy-to-ipod and move-to-ipod there. just be careful about move-to option as it works like cut-paste.

---

### Post by Odlinski on 2009-12-03
> **amsum said:**
> It doesn't work this way. You need to select the songs from Local Music and then right-click it. You will see the option of both copy-to-ipod and move-to-ipod there. just be careful about move-to option as it works like cut-paste.

You sir, are a genius!

/I'm a retard.

Yeah that worked.  Thank you all for getting me through. :D

---

### Post by StuartN on 2009-12-03
> **Odlinski said:**
> You sir, are a genius!

@amsum, any idea on what the problem is with Rhythmbox, or even how to go about diagnosing it? The iPods that I have tried mounted read/write, but the next one is bound to do this...

---

### Post by amsum on 2009-12-03
> **StuartN said:**
> @amsum, any idea on what the problem is with Rhythmbox, or even how to go about diagnosing it? The iPods that I have tried mounted read/write, but the next one is bound to do this...

I haven't tried iPod in Rhythmbox. I will try to figure out and report you back.

---

### Post by Odlinski on 2009-12-03
Actually it didn't work.  I though it had because it said that the files were already on the iPod.  It now transpires that it was lying to me.  Adding as root didn't work either when I tried it.

---

### Post by amsum on 2009-12-03
> **Odlinski said:**
> Actually it didn't work.  I though it had because it said that the files were already on the iPod.  It now transpires that it was lying to me.  Adding as root didn't work either when I tried it.

Just curious, what didn't work? Did the song transfer didn't work? After copy-to-ipod option, unmount the ipod and check the song in it. It must be there probably with different name or so. Sometimes it do happen that ipod doesn't take the filename and alter it with some weird id.

---

### Post by Odlinski on 2009-12-03
> **amsum said:**
> Just curious, what didn't work? Did the song transfer didn't work? After copy-to-ipod option, unmount the ipod and check the song in it. It must be there probably with different name or so. Sometimes it do happen that ipod doesn't take the filename and alter it with some weird id.

The song transfer didn't happen because it said the song was all ready there.  I checked at that point in the iPod folder of Amarok and it was.  I unmounted, checked on the actual iPod (also checked for strange filenames) then when I plugged it back in and looked in Amarok, it had gone.

---

### Post by amsum on 2009-12-03
Were you able to listen to those songs in ipod once you unmounted.

Also, you mean songs from ipod was gone once you connected back to amarok? or amarok was not detecting ipod again?
You need to follow the same step told earlier to make amarok recognize ipod.

---

### Post by Odlinski on 2009-12-03
> **amsum said:**
> Were you able to listen to those songs in ipod once you unmounted.

Also, you mean songs from ipod was gone once you connected back to amarok? or amarok was not detecting ipod again?
You need to follow the same step told earlier to make amarok recognize ipod.

I wasn't able to listen to songs in iPod after unmounting.

I had followed those steps again and the iPod was recognised but the songs were gone.  I'm pretty sure they were never actually on the iPod.

---

### Post by amsum on 2009-12-03
hmm... this is strange. just try with one file and see how it works. 

I have to leave now but will follow this thread and may report back tomorrow. I hope somebody else jumps in with some kind of input.

---

### Post by StuartN on 2009-12-04
> **Odlinski said:**
> I wasn't able to listen to songs in iPod after unmounting.

I had followed those steps again and the iPod was recognised but the songs were gone.  I'm pretty sure they were never actually on the iPod.

Can you find the location where the iPod mounts, something like /media/iPod, and run **ls -l /media** (or whichever path it is in) to just check the permissions and ownership.

---

