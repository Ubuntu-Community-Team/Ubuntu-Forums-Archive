---
title: "nautilus sftp:// smb:// and trash:/// broken"
date: 2009-11-08
forum: General Help
---

### Post by mrmooge88 on 2009-11-08
I upgraded from 9.04 to 9.10. I used to be able to access my home server in nautilus with sftp or smb but I haven't been able to access since the upgrade. I can't view my trash either, but I can send files to it and see them in ~/.local/share/Trash/files.

When I try to view my trash folder (trash:///) I get the message:
The folder contents could not be displayed.
Sorry, could not display all the contents of "trash": Operation not supported

---

### Post by mrmooge88 on 2009-11-10
bump

---

### Post by mrmooge88 on 2009-11-13
bump. one last time :)

---

### Post by kernst on 2010-05-16
Yeah, this is annoying. 

I'll check my 10.10 box a little later to see if it got fixed. And I'll dig through the bugs in Launchpad to see if anyone's tracking this problem yet.

---

### Post by vividexstance on 2011-02-07
I also have the same problem for my trash, where if I double-click the Trash icon on my desktop, it first didn't know which application to open it with and I had to set it to nautilus.  When it opened in nautilus, it said the same thing:  &quot;The folder contents could not be displayed. Sorry, could not display all the contents of &quot;trash&quot;: Operation not supported&quot; in an alert dialog upon opening nautilus in the Trash bin.  I'm running ubuntu 10.04.

---

### Post by cjejuni on 2011-02-22
was this ever resolved? i am experiencing this prob in ubuntu 10.10. 
thanks. cj

---

### Post by csad on 2011-02-23
cjejuni,

I don't know if the OP resolved this in some way, but I had a similar problem with 10.10 recently, so I just went ahead and reinstalled all nautilus files at Synaptic Package Manager. It worked. Try and see if it helps. :)

---

### Post by cjejuni on 2011-02-24
thanks, reinstalled nautilus, still getting the same. it must be in the config file. just do not know where they are. tia. cj

---

### Post by csad on 2011-02-24
Well, this is what I did step for step, actually: 

Reinstallation in "Synaptic Package Manager" of not just "nautilus", but all packages related to it, such as "nautilus-data" and "libnautilus-extension1" especially. So a search was necessary.

In my case, the trash bin had crashed down after a particularly big bout of deleting, where I got rid of a few thousand of my unnecessary documents at once, and hadn't been able to empty the bin. Heck, the symbol was gone from its place on the bottom right, and clicking "Rubbish Bin" in Nautilus gave out the error "trash:/// not found", if I remember correctly.

So the next step was for me to empty the bin through the command file, as I couldn't even open up the folder in the path: ```
/home/USERNAME/.local/share/Trash/files
```This is the code for trash bin emptying using terminal: 

```
sudo rm -fr /home/USERNAME/.local/share/Trash/

```I must have mistyped something though, or something else might have happened that I didn't notice, because for some reason while the trash bin *was* emptied, and the symbol restored back where it belonged, the folder "Trash" in the path ```
 /home/USERNAME/.local/share/
``` had been deleted. I had to use "File/Create Folder" and name it "Trash" in that path. 

Deleted a few test docs to see if it had worked, and it had. Haven't had a problem since then.

Does any of this sound like something that you already tried or that'd perhaps help you?

---

