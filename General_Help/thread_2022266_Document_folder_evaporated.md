---
title: "Document folder evaporated"
date: 2012-07-10
forum: General Help
---

### Post by analogdialog on 2012-07-10
Recently I decided to back up my work to an usb hard drive. What a strange result. I dragged a folder named "H" (as well as other folders in "Documents") from "Documents" to a folder on the drive. When I looked into H on the usb drive it slowly dawned on me this was a 6 month old version. I should also mention a strange question I got during copying regarding the merging of two folders. How can there be merging of any folders when I am copying to a newly made, empty folder with a unique name. Something very wrong here, me think.

So I thought "Maybe Ubuntu (12-04) doesn't care for usb hard drives." I proceeded to copy to an usb flash device. That went  well, now the copy was actually a copy.

Then some days passed, and suddenly, you guessed it; Document folder gone, no warning, no trace. That's the original, mind you, not the copy.

But there must be a backup in the cloud. I had "Ubuntu One" active, and every blessed time I saved a file, it was uploaded.
I started "One" and looked in "H". There was a 6 month old version and no trace of all the automatically uploaded files.

So that's it. I hope a copy is on the flash device. Right now I dare not look, for fear that Ubuntu will decide to wipe that out as well. It's 6 month worth of work.

I've had my problems with MS Windows, but not that kind. Maybe there is some explanation, but drag and drop shouldn't be rocket science. I dragged and dropped to the flash device and apparently performed a copy operation. At least the original lingered for several days, reminiscent of the Cheshire cat...

Oh, and while we are talking drag and drop, why can't I "right drag" and get a choice of copy or move like in windows ?

---

### Post by analogdialog on 2012-07-10
.

---

### Post by ajgreeny on 2012-07-10
> **analogdialog said:**
> Recently I decided to back up my work to an usb hard drive. What a strange result. I dragged a folder named "H" from "Documents" to a folder on the drive. When I looked into H on the drive it slowly dawned on me this was a 6 month old version.

So I thought "Maybe Ubuntu (12-04) doesn't care for usb hard drives." I proceeded to copy to an usb flash device. That went  well, now the copy was actually a copy.

Then some days passed, and suddenly, you guessed it; Document folder gone, no warning, no trace.
But there must be a backup in the cloud. I had "Ubuntu One" active, and every blessed time I saved a file, it was uploaded.
I started "One" and looked in "H". There was a 6 month old version and no trace of all the automatically uploaded files.

So that's it. I hope a copy is on the flash device. Right now I dare not look, for fear that Ubuntu will decide to wipe that out as well. It's 6 month worth of work.

I've had my problems with MS Windows, but not that kind. Maybe there is some explanation, but drag and drop shouldn't be rocket science. I dragged and dropped to the flash device and apparently performed a copy operation. At least the original lingered for several days, reminiscent of the Cheshire cat...

Oh, and while we are talking drag and drop, why can't I "right drag" and get a choice of copy or move like in windows ?
I can't help with your main problem of missing files and folders as it has never been a problem I have seen when drag/drop/copying to a usb flash drive, hard drive, or anywhere else for that matter.

As for your query about right-drag, in nautilus it is middle-drag that shows you the menu for move/copy/link?

---

### Post by analogdialog on 2012-07-10
Nautilus.. Well, in Ubuntu 12.04 it's just a file explorer, don't know if it's got a name. Any way I don't think I can middle-drag on my netbook (got no rodent).

---

### Post by ajgreeny on 2012-07-10
> **analogdialog said:**
> Nautilus.. Well, in Ubuntu 12.04 it's just a file explorer, don't know if it's got a name. Any way I don't think I can middle-drag on my netbook (got no rodent).
Hold both left and right buttons on trackpad/touchpad to emulate middle click.

---

### Post by analogdialog on 2012-07-10
Thanks, ajgreeny. I have resorted to choose "Copy to" from the right click menu, then copied to the desktop, then moved from there to destination. Question; what keeps ubuntu from implementing right-drag with a choice of move or copy ?
Yes, I could copy-and-paste, I just realized.

---

### Post by papibe on 2012-07-11
Hi analogdialog.

I'm sorry you had bad luck with this.

In my experience, the 'Merge' message only appears when there is conflicts with folder names. Unless you are pretty sure what you are doing, it is better cancel the merge, and study the situation before going further.

As for the lost of ~/Documents, my first (optimistic) guess is that you somehow move it inadvertently since 'moves' within the same filesystem are super fast on Linux.

Let's try this:
```
find / -type d -name Documents
``` 
That will look for every directory called Documents in the whole file structure. With luck is there somewhere.

Nautilus, the Ubuntu file manager, has the same basic functionality than most file manager, but as you expect, different shortcuts and MO. I know it is a little late, but here's [Nautilus Guide]("http://library.gnome.org/users/user-guide/stable/nautilus.html") I think you may find useful.

There's also the [Ubuntu manual]("http://ubuntu-manual.org/") you can download for further study

Let us know how it goes.
Regards.

---

### Post by analogdialog on 2012-07-11
OK, that gave me

root@A10:/home/xxxxx# find / -type d -name Documents
/usr/share/office2010trial/install_en/Documents
/home/xxxxx/.wine/drive_c/users/Public/Documents
/home/xxxxx/.local/share/Trash/files/Documents
/home/xxxxx/Ubuntu One/Documents

I looked into the /home/xxxxx/.local/share/Trash/files/Documents path, and it looks like the content I'm missing. Moved to trash, that makes some sense.

The sense I can make of it is that I performed a "move" when I thought I performed a "copy". Move means copy and delete. If so, why did the Documents folder linger for days ?? And does Nautilus default to "move" when I drag and drop to an other drive ? Windows file manager's default is "copy" in that situation.
When I started using computers, I was using DOS. Maybe I should go back to the command line more often, and rely less on the GUI !

And what happened to the cloud backup I was supposed to have ?

It's good to know my files are somewhere, even if it's in Trash. To restore, do I copy Documents to my home folder using the command line ?

AD

---

### Post by JKyleOKC on 2012-07-11
As others will rush to tell you, Ubuntu is not Windows and many of its features operate a bit differently.

A complicating factor is that while Windows has only one flavor of file manager, Explorer, the Ubuntu world has at least three and undoubtedly more that slip my mind at the moment. The three most popular have been Nautilus, Konqueror, and Thunar -- and all of them treat drag and drop actions a bit differently from each other!

I'm most familiar with Thunar, which is the default in Xubuntu; with it, drag and drop between directories that are direct relatives of each other, such as from Documents to Pictures when both are in one's home directory, results in a move action -- copy and delete. However if the directories involved are not direct relatives, such as from one user's home directory to another, or off to another network drive, it's only a copy, no remove. And sometimes, for no reason I've been able to discover yet, dragging a file from a folder to another folder that's a child of the original one results in a copy rather than a move!

In my trash folder, right-clicking on any file there gets a context menu that includes "restore" as one choice. Selecting it puts the file back in its original location. I trust that the same would be true for a subdirectory -- but have not tested to be sure. And since this is Thunar, not the default manager of Ubuntu 12.04, it may be different for you!

I think it was Winston Churchill who observed during WW2 that Britain and the USA were "allies separated by a common language." The same could be said of the many flavors of Ubuntu or even Linux, and while Windows isn't exactly considered an ally, it shares some but not all of the common language too...

---

### Post by analogdialog on 2012-07-12
Like a complete fool I have neglected the obvious, namely to look in the trash can. There it was, the missing documents folder, and it was restored with a click, including all subfolders as far as I can tell.

Thank you kindly, papipe and JKyleOKC.

I won't mark this thread solved, because there are many questions unanswered.
I admit to being a windows refugee, largely ignorant of the Linux/Unix ways (and I'm glad to have several choices besides windows). Still, I would be surprised if I were to discover that nautilus defaults to "move" when I drag to an other drive.

Regards
AD

---

