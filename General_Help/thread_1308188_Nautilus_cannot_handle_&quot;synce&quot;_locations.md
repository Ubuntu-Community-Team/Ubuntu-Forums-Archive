---
title: "Nautilus cannot handle &quot;synce&quot; locations."
date: 2009-10-31
forum: General Help
---

### Post by xc8 on 2009-10-31
Hi,

I just installed the 9.10 and I wanted to browse the files of my Windows Mobile 6.1 device.

When I choose the 'Explore with filemanager' on the synce-trayicon I get the error 'Nautilus cannot handle "synce" locations.' 

I had no problems on 9.04 , seems that something is missing or is broken on 9.10 ? 

TIA

Chris

---

### Post by gbthomps on 2009-11-14
I had the same problem.  I was able to fix it.  You need the file "synce-gvfs".  However, this file is no longer available in Karmic.  After many hours of pulling my hair out trying to install it via a tarball, I discovered an easy way of doing it:

Go to System, Administration, Software Sources.  Then click on "Other Software".  Click on add.  At the command APT line enter:  deb  [http://ppa.launchpad.net/synce/ubuntu](http://ppa.launchpad.net/synce/ubuntu) jaunty main

Click "+add source"

Click add again.  At the command APT line enter:  deb-src  [http://ppa.launchpad.net/synce/ubuntu](http://ppa.launchpad.net/synce/ubuntu) jaunty main

Click "+add source" again

Click on "close"

Click on "reload"

The window will close on it's own when it's done.

Now open a terminal window (Applications, Accessories, Terminal)

Type:  sudo apt-get install synce-gvfs

This will install the missing file.

When done, restart your computer.  When you now connect your pda, you won't get the nautilus error message anymore when right clicking on the trayicon and "explore with filemanager." 

Unfortunately, this is as far as I've gotten.  It still won't see any of the files.

If anyone out there knows how to get it to actually see the files on the pda, please let me know.

This is the only thing I haven't been able to get working again.  (It worked fine in Jaunty.)

---

### Post by TBerk on 2009-11-16
> **gbthomps said:**
> I had the same problem.  I was able to fix it.  You need the file "synce-gvfs".  However, this file is no longer available in Karmic.  After many hours of pulling my hair out trying to install it via a tarball, I discovered an easy way of doing it:
<snip>
Type:  sudo apt-get install synce-gvfs

This will install the missing file.

When done, restart your computer.  When you now connect your pda, you won't get the nautilus error message anymore when right clicking on the trayicon and "explore with filemanager." 

Unfortunately, this is as far as I've gotten.  It still won't see any of the files.

If anyone out there knows how to get it to actually see the files on the pda, please let me know.

This is the only thing I haven't been able to get working again.  (It worked fine in Jaunty.)


For The Win!  I found the command; 

```

sudo apt-get install synce-gvfs

```

Did it for me. (I had already the right repositories sourced in Synaptic/APT-GET).

After a reboot I can now use the SynCE Tray Icon to browse via Nautilus filemanager.

btw- I can see my files under the FILESYSTEM tree structure.

Thx,
berk

---

### Post by jo@tux on 2009-11-16
Hi,

I use synce-gvfs at least since Jaunty and so far it has always worked perfekt. 
But despite a successful installation,in karmic nautilus does not show me the data of the PDA.
Nautilus looks awhile, but then shows only a blank window. 
The command synce-pls work.
Which version of synce-gvfs you have installed and from which branch? ppa:dupondje/ppa ?

Thanks jo@tux

---

### Post by gbthomps on 2009-11-17
> **jo@tux said:**
> Hi,

I use synce-gvfs at least since Jaunty and so far it has always worked perfekt. 
But despite a successful installation,in karmic nautilus does not show me the data of the PDA.
Nautilus looks awhile, but then shows only a blank window. 
The command synce-pls work.
Which version of synce-gvfs you have installed and from which branch? ppa:dupondje/ppa ?

Thanks jo@tux
   
The problem has been fixed.  The good folks at synce.org fixed the synce-gvfs file.  All you have to do, is go to synaptic package manager, search for the synce-gvfs file and click to upgrade it.  I restarted after doing so (just to make sure) and TA DA.  Files are all there.

---

### Post by jo@tux on 2009-11-18
Thank you for your information. I think I used the wrong repositories, from a sub branch.
The only difference tou your Instructions is i now use the repositories for karmic.
deb [http://ppa.launchpad.net/synce/ubuntu](http://ppa.launchpad.net/synce/ubuntu) karmic main

---

### Post by Naegling23 on 2009-11-19
nice, working now.

Yup, I had to add the karmic repository to get it to work....finally, I can sync my podcasts to my phone.

---

### Post by Aposp on 2009-12-05
hmm i seem unable to add the source cause it reports that there is not a public key when i am adding the repository.  =/ any ideas?

---

### Post by excogitation on 2009-12-24
```
$ gpg --keyserver keyserver.ubuntu.com --recv B152F042D246C25D
$ gpg --export --armor B152F042D246C25D | sudo apt-key add -
```

---

