---
title: "Files in trash but not in trash?!?!?!?!?"
date: 2010-12-24
forum: General Help
---

### Post by yancouto on 2010-12-24
Hi, I have a problem with a couple of folders in the Trash.
If I click on the Trash icon, 2 foldersare there, and when I try to delete them, it just says "Failed to delete the item from the trash"

But when I go to .local/share/Trash there are no files there!
Anyway, I tried using the command "sudo rm -rf .local/share/Trash", it shows no error, but the files continue when I click in the trash icon.

Can anyone help me?

---

### Post by owiknowi on 2010-12-24
had the same problem a while ago.
installed bleachbit and it cleaned it up for me (used root mode and user mode).

still don't know why though.
could be you've deleted files with root privileges and now trying to empty trash as normal user?

anyone else?

---

### Post by johnmay on 2010-12-24
It is possible that the files are from another system which you were not 'owner of' maybe restore and give yourself full rights. Also try opening nautilus as root and delete with the gui. 

I know the sudo command you tried should work but who know what will until it does right?

---

### Post by yancouto on 2010-12-24
> **owiknowi said:**
> had the same problem a while ago.
installed bleachbit and it cleaned it up for me (used root mode and user mode).

still don't know why though.
could be you've deleted files with root privileges and now trying to empty trash as normal user?

anyone else?

I tried BleachBit in both modes and it didn't work, I used the options "System: Free Disk Space, Trash, Temporary Files"
:(

> **johnmay said:**
> It is possible that the files are from another system which you were not 'owner of' maybe restore and give yourself full rights. Also try opening nautilus as root and delete with the gui. 

I know the sudo command you tried should work but who know what will until it does right?

I used "sudo nautilus" to open it (is it the right way?)
But when I click in the Trash it shows the message
[SIZE="6"]"[/SIZE][I]The folder contents could not be displayed.
Sorry, could not display all the contents of "trash": Operation not supported[/I][SIZE="6"]"[/SIZE]



EDIT: I just realized that one folder was deleted But the other remains, I don't know why, maybe I'll try BleachBit again to see if it deletes the other one

---

### Post by matt_symes on 2010-12-24
Hi

*EDIT: Maybe i have miss understood, but...*

What are the names of the folders in Trash?

Are they info, files and expunged?

Some folders get auto generated, because they hold information about the files stored in trash.

Kind regards

---

### Post by TeoBigusGeekus on 2010-12-24
If you have previously mounted a portable device (i.e. external hd, usb flash, etc.), deleted something from it and then unmounted without emptying its trash, then the folders will show in your trash but you won't be able to delete them.
Mount the portable device again and delete its trash folder (.Trash or something).

---

### Post by yancouto on 2010-12-24
> **matt_symes said:**
> Hi

*EDIT: Maybe i have miss understood, but...*

What are the names of the folders in Trash?

Are they info, files and expunged?

Some folders get auto generated, because they hold information about the files stored in trash.

Kind regards

The folder is called "Adobe Commons", I used it to put Photoshop on ubuntu. I can't tell if it is files or expunged (I guess it's not info) because It does not appear on .local/share/Trash

---

### Post by yancouto on 2010-12-24
> **TeoBigusGeekus said:**
> If you have previously mounted a portable device (i.e. external hd, usb flash, etc.), deleted something from it and then unmounted without emptying its trash, then the folders will show in your trash but you won't be able to delete them.
Mount the portable device again and delete its trash folder (.Trash or something).

Thanks. The folder was indeed in my pen drive's trash, but now that I found it, I can't delete it either. If I press "Delete", nothing happens. I also tried deleting through the terminal, using "sudo rm -rf .Trash-1000" but it doesn't delete anything, it just says it can't delete because it is "Read-Only" and sometimes it says "Input-Output Error"

EDIT: I can't delete anything on my pen drive, it turned read-only :O
EDIT2: I just unmounted and mounted it again and it was back to normal, but I tried to delete the files(normally and through terminal) but I couldn't delete again!!!! When I try deleting it becomes Read-Only again!!

---

### Post by TeoBigusGeekus on 2010-12-24
Try rebooting and mounting your pen drive again.

---

### Post by owiknowi on 2010-12-24
> **TeoBigusGeekus said:**
> Try rebooting and mounting your pen drive again.

yes and again you're right!
in my case it were old back up files from a not mounted external device.

when mounted it did - of course - work the right way.

another problem that sometimes occurs, is when windos files are deleted, especially from external ntfs formatted devices.
----------
in this case the files may be still in use by some application (the installed)?
suppose you installed adobe with root privileges?

btw. in nautilus menu edit/preferences, second tab, you can enable a delete command that bypasses trash.

---

### Post by Syed75 on 2010-12-24
I have the same problem it says theres 1 thing in trash. I go to trash and theres nothing there...

---

### Post by owiknowi on 2010-12-24
did you try the nautilus menu option: view/show hidden files?
maybe you can see what files are present.

---

### Post by JosephC on 2011-04-08
This happens when you try to delete a file or files from an external device, and the file(s) are labelled as Trashed, but are not moved to the proper folder (like $RECYCLE.BIN) on the external device. Therefore, it shows up in your Trash, but cannot be deleted. Simply open the external device folder as administrator (gksu nautilus), check Show Hidden Files (under View), and move the .Trash folders that now appear in the external drive to $RECYCLE.BIN (also present on the external drive). The .Trash folders cannot be deleted, for they already have been. You can only move them to $RECYCLE.BIN or another similarly named folder so that they are recognized as deleted. In actuality, your computer was just haunted by the ghost of a dead file - a slight categorical error, now solved by helping the poor file move on. Your Trash icon should now immediately appear empty, and upon clicking on it, you'll find that it is indeed empty. Problem solved. Just a file naming quirk. Not a fundamental or complex problem. Breathe. Find your calm. Be free of all the stress and frustration that computers regularly contribute to the countless pains of our lives.

---

### Post by dniMretsaM on 2011-04-08
Or you can simply plug your device in and then empty the Trash. That works for me and is simpler than what JosephC said.

---

### Post by JosephC on 2011-04-08
Sadly, emptying the Trash did not work for him.

---

### Post by dniMretsaM on 2011-04-08
Did he try actually emptying the Trash (via right click -> Empty Trash) instead of manually deleting the .Trash folder or whatever it's called?

---

### Post by JosephC on 2011-04-08
Yes. He received a "Failed to delete the item from the trash."

---

### Post by dniMretsaM on 2011-04-08
Hmm... That's odd. Oh well. As long as he got it working.

---

### Post by JosephC on 2011-04-08
Yes. I hope so too.

---

### Post by dniMretsaM on 2011-04-16
[S]I now have a similar problem. I deleted some files off of an SD card, then formatted it, and now I have some files stuck in the Trash. I ran gksu nautilus and showed the hidden files, but there is not .Trash-1000 or RECYCLE.BIN folder.[/S] Never mind, I restarted my computer and the Trash is now empty so it must have just been a glitch.

---

