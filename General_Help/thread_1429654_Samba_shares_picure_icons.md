---
title: "Samba shares picure icons"
date: 2010-03-14
forum: General Help
---

### Post by seelk on 2010-03-14
I have samba shares set up on my server running Ubuntu Server 9.10.  My issue is, when browsing images from the server on a different computer it doesn't show the preview icons.  However, it does preview the images locally on the same computer.  Ideas?

---

### Post by Jared Norris on 2010-03-14
Previewing pictures is usually on a per computer basis not actually attached to the file itself. 

First thing to do is check the computer you're accessing the share from does display previews of files stored locally (of the same file extension to be sure). 

You will probably find that picture previews is just not enabled on the other computer.

---

### Post by seelk on 2010-03-14
> **head_victim said:**
> Previewing pictures is usually on a per computer basis not actually attached to the file itself. 

First thing to do is check the computer you're accessing the share from does display previews of files stored locally (of the same file extension to be sure). 

You will probably find that picture previews is just not enabled on the other computer.

The "other computer" is the server.  I am able to view the previews from Windows 7 accessing the same location on the server.

How can I check the server allows previews for images?  Does it matter that I can view the previews in Windows 7 but not Ubuntu 9.10?

---

### Post by coffeecat on 2010-03-14
Gnome stores the thumbnails for the "previews" in ~/.thumbnails (where ~ = your home folder). The default setting is for creating thumbnails for the local machine only. If you want thumbnails in your smb share folders, open a Nautilus (file browser) window and go to Edit > Preferences > Preview tab, and change "show thumbnails" to "always".

There's a tip on [here]("http://www.latenightpc.com/blog/archives/2009/01/01/thumbnails-for-samba-shares-in-nautilus") for if you get a failure to show the thumbnails even after you've changed the preference.

I should imagine Windows 7 stores its thumbnails locally as well, but that the default is to have them showing for shares.

**Edit:** that link's comment about the 1GB file limit for thumbnails is no longer current - or at least not in the version of Nautilus that comes with Lucid. I've just checked my samba fileserver and two 1.6GB video files are showing thumbnails nicely. I'll check that detail out in Karmic when I'm next in Karmic. My guess is that the default is to have them off because samba sharing is slow at the best of times, and interrogating many files to get thumbnail information can take a significant time even on the local machine.

---

### Post by seelk on 2010-03-14
> **coffeecat said:**
> Gnome stores the thumbnails for the "previews" in ~/.thumbnails (where ~ = your home folder). The default setting is for creating thumbnails for the local machine only. If you want thumbnails in your smb share folders, open a Nautilus (file browser) window and go to Edit > Preferences > Preview tab, and change "show thumbnails" to "always".

There's a tip on [here]("http://www.latenightpc.com/blog/archives/2009/01/01/thumbnails-for-samba-shares-in-nautilus") for if you get a failure to show the thumbnails even after you've changed the preference.

I should imagine Windows 7 stores its thumbnails locally as well, but that the default is to have them showing for shares.

Thanks a lot!  That did it!

---

