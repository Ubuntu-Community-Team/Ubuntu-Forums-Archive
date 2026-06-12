---
title: "Amarok and streamed music from a Win2000 share"
date: 2006-03-07
forum: General Help
---

### Post by Coulrophobe on 2006-03-07
OK...think I'm doing something dumb here but don't know what ! I've got amarok on and I can connect to the share on my server with all my music but when I open the collection tab in Amarok I don't get the option to select that SMB folder from my desktop for Amarok to parse up my music...Can anyone enlighten me as to what I might be doing wrong please ?

Ta's
S

---

### Post by peyu on 2006-03-07
Well, I'm not an expert, but I think that you first need to import the share in your music collection, going to Settings / Configure amarok, check the box of the share folder (the share need to be mounted), and then amarok will scan it to add to your music collection.

Maybe you also need to have write access to the share...

---

### Post by Coulrophobe on 2006-03-08
Still stuck...I have the SMB-mounted Win2k server folder on my desktop. I got this there by going places -> connect to server -> filling out the server, folder and user account etc and up came the folder icon...nice.

I can open the folder and browse all it's contents however when I open amarok (and rhythymbox for that matter too) and try to use this folder to build the collection from, it doesn't appear in the checkbox treeview to select.

Have I mounted this remote folder wrongly or is there some other configuration issue with Amarok in order to let it navigate to Samba-mounted volumes ?

TIA
S

---

### Post by pete on 2006-03-08
From your description, I'm guessing that you used Nautilus's "Places -> Connect to Server" wizard, and now have a desktop icon that links to the Win2K share.

The problem is that the SMB share isn't actually mounted in the filesystem on your Ubuntu machine, so even though there's an icon right there that lets *you* navigate to it via the GUI, Amarok has no idea that it exists.

Do a search for "mount smbfs" or "smbmount"...  there's a ton of threads that will walk you through it better than I could.  The other option is to add an entry to your /etc/fstab to auto-mount the share on boot.

---

### Post by Coulrophobe on 2006-03-08
Schweet...that's exactly what I did Pete. I'll go hunting right now ?!
Cheers
S

---

