---
title: "Trash Not Deleting"
date: 2010-05-30
forum: General Help
---

### Post by TheRainbowBitMe on 2010-05-30
My trash won't delete and it is causing me to not be able to use my flashdrive. 

When I tell my trash to empty it will either say it will but the files will still be there or it will say a can't b/c i didn't delete it from my trash(screenshot). I don't know what to do to get it to get rid of the files since I tried telling it to bypass the trash and that didn't do anything.

---

### Post by etdsbastar on 2010-05-30
try using this option,

open terminal

type the following

$ sudo nautilus

if asked for password then type your user password, nautilus will be opened as root access (Be Careful).

Goto you trash directory and delete all the file as required, then close your nautilus window and terminal.

Hope this helps.

---

### Post by quadproc on 2010-05-30
> **TheRainbowBitMe said:**
> My trash won't delete and it is causing me to not be able to use my flashdrive. 

When I tell my trash to empty it will either say it will but the files will still be there or it will say a can't b/c i didn't delete it from my trash(screenshot). I don't know what to do to get it to get rid of the files since I tried telling it to bypass the trash and that didn't do anything.
I don't know any of the details of your situation so this response may not be on target, but here goes:

Moving something to trash actually just changes the directory(s) leading to the file; the file still remains intact.  Removing (emptying) the trash causes an actual deletion of the file.  Flash memories are limited in their ability to tolerate write operations such as deletes so this action is usually deferred until the device is unmounted.  So, the thing to do is to empty the trash and then to unmount the device.  You will find an unmount command in the file manager's (Places) window for the flash drive under the File button.

It is important to unmount a drive before unplugging it so that all of the pending operations on it will be completed before it is unplugged.

quadproc

---

### Post by etdsbastar on 2010-05-30
That's why i told [TheRainbowBitMe]("http://ubuntuforums.org/member.php?u=1003557") to use the solution i told him to use it with sudo

---

### Post by greyfox1 on 2010-05-30
> **etdsbastar said:**
> 

$ sudo nautilus

This should be gksudo nautilus. Any time you wish to run a graphical application as root, use gksudo rather than sudo. [More info]("http://www.psychocats.net/ubuntu/graphicalsudo")

---

### Post by etdsbastar on 2010-05-30
> **greyfox1 said:**
> This should be gksudo nautilus. Any time you wish to run a graphical application as root, use gksudo rather than sudo. [More info]("http://www.psychocats.net/ubuntu/graphicalsudo")

hello friend,

I have used with sudo and it worked fine for me, if not for the poster then he is free to use gksudo or can use ALT+F2 then typing nautilus and then check the box "Run In terminal" option and then click run.

---

### Post by jflaker on 2010-05-30
> **TheRainbowBitMe said:**
> My trash won't delete and it is causing me to not be able to use my flashdrive. 

When I tell my trash to empty it will either say it will but the files will still be there or it will say a can't b/c i didn't delete it from my trash(screenshot). I don't know what to do to get it to get rid of the files since I tried telling it to bypass the trash and that didn't do anything.

if this was something from a removable drive, you need to have that drive attached to successfully empty the trash

---

### Post by TheRainbowBitMe on 2010-05-30
> **etdsbastar said:**
> try using this option,

open terminal

type the following

$ sudo nautilus

if asked for password then type your user password, nautilus will be opened as root access (Be Careful).

Goto you trash directory and delete all the file as required, then close your nautilus window and terminal.

Hope this helps.

i tried this, with the flashdrive attached and I got an error message saying the operation isn't supported(screenshot).

**I also tried it the ALT+F2 way and the only thing that came up was my home folder.

---

### Post by TheRainbowBitMe on 2010-05-30
> **greyfox1 said:**
> This should be gksudo nautilus. Any time you wish to run a graphical application as root, use gksudo rather than sudo. [More info]("http://www.psychocats.net/ubuntu/graphicalsudo")

I had the same issue with trying it this way as I said in my last post.

---

### Post by etdsbastar on 2010-05-31
> **TheRainbowBitMe said:**
> i tried this, with the flashdrive attached and I got an error message saying the operation isn't supported(screenshot).

**I also tried it the ALT+F2 way and the only thing that came up was my home folder.

Hey i am really sorry, i was a bit confused, try this and it will work i am sure:

$ sudo nautilus .local/share/Trash/files

type your password.

then delete the files in your trash folder.

If you want to delete from a flash or usb drive then type

$ sudo nautilus

and then goto /media/(your flash or usb folder)/.Trash

and then delete the files there.

---

### Post by TheRainbowBitMe on 2010-05-31
> **etdsbastar said:**
> Hey i am really sorry, i was a bit confused, try this and it will work i am sure:

$ sudo nautilus .local/share/Trash/files

type your password.

then delete the files in your trash folder.

If you want to delete from a flash or usb drive then type

$ sudo nautilus

and then goto /media/(your flash or usb folder)/.Trash

and then delete the files there.

My flashdrive doesn't have a .Trash file. And I even checked to see if maybe for some reason it was hidden and it wasn't. Any other ideas?

---

### Post by etdsbastar on 2010-06-01
> **TheRainbowBitMe said:**
> My flashdrive doesn't have a .Trash file. And I even checked to see if maybe for some reason it was hidden and it wasn't. Any other ideas?

will you please send me the screenshot of your flashdrive trash folder with CTRL+H pressed and your system's Trash folder with CTRL+H pressed.

Thanks,

---

### Post by TheRainbowBitMe on 2010-06-02
> **etdsbastar said:**
> will you please send me the screenshot of your flashdrive trash folder with CTRL+H pressed and your system's Trash folder with CTRL+H pressed.

Thanks,

So I'm not sure how this happened, but when I plugged my flash drive in all my files that were "deleted" were back on my flashdrive and I hit delete and they deleted for good. Sorry for all the trouble. My computer has been doing strange things like this since I did the last big update. 

Thanks for everyone that helped. ^_^

---

### Post by jarviser on 2010-06-02
> **TheRainbowBitMe said:**
> My flashdrive doesn't have a .Trash file. And I even checked to see if maybe for some reason it was hidden and it wasn't. Any other ideas?

.trash is a hidden file. To see hidden files just browse the drive then hit ctrl+H  Then delete .trash   This is THE most annoying feature of using flash drives in Linux.

---

### Post by etdsbastar on 2010-06-03
> **TheRainbowBitMe said:**
> So I'm not sure how this happened, but when I plugged my flash drive in all my files that were "deleted" were back on my flashdrive and I hit delete and they deleted for good. Sorry for all the trouble. My computer has been doing strange things like this since I did the last big update. 

Thanks for everyone that helped. ^_^

Thanks Rainbow and congrats that your problem has been solved... Keep posting and be in touch with Ubuntu forums for more queries and solutions... Bye and take care...

---

