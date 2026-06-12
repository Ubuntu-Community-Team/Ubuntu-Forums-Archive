---
title: "Recover data from emptied file"
date: 2010-07-22
forum: General Help
---

### Post by Magma828 on 2010-07-22
I was editing a PHP file by FTP on my Ubuntu server, and for some reason it's saved an empty file. Is there any chance I could get the contents back? If not, I'll just have to revert to an older backup =/

---

### Post by robsoles on 2010-07-22
Your predicament seems odd to me because I wouldn't personally use software that even claimed I was going to 'edit via FTP (or SFTP)' to actually try to edit via FTP (or, better still, SFTP) because it would leave me in a position of being able to destroy the remote file without having a copy of my most recent edit(s) to rely on!

Unless your FTP program that allows editing via FTP made a backup of the file for you the content, particularly any changes you made, must be lost.

I can only offer a tip I hope you might apply in future:

Where it is a script/program that you will be editing: Make a copy and work on a copy of the copy - that way when you put your copy over the 'running' original you will be able to revert back to the other copy if you find it is not what you wanted from your edit!

---

### Post by WorMzy on 2010-07-22
If you were using gedit, and have the "make backup on save" option checked, then the original file should have been copied to "<filename>~", it'll be hidden by default.

---

### Post by Magma828 on 2010-07-22
> **WorMzy said:**
> If you were using gedit, and have the "make backup on save" option checked, then the original file should have been copied to "<filename>~", it'll be hidden by default.
I was using gedit, but the backup option was disabled :(

I'll enable it now in case this happens again, but where exactly is the file saved? (like, on the remote server or my computer?)

---

### Post by WorMzy on 2010-07-22
If it works on remote hosts (I can't see why it wouldn't), it'll be in the same directory as the updated file.

---

### Post by Magma828 on 2010-07-22
> **WorMzy said:**
> If it works on remote hosts (I can't see why it wouldn't), it'll be in the same directory as the updated file.
Alright, thanks. Whatever it was that caused a blank file to be saved, could it save the backup as a blank file too?

When I saved the file gedit actually kept all my code showing as if it had saved properly, but when I logged into FTP this morning the file was empty. I had noticed it had saved empty files before, but it wasn't a problem because I could just click Save to restore the code. It's only a problem when I don't realise it's emptied the file, and I close gedit.

---

### Post by WorMzy on 2010-07-22
I can't guarantee anything, but I think that gedit just copies the original before it commits the changes, so as long as the file had text in it when you opened it, the backup should have the same text in it too.

---

### Post by robsoles on 2010-07-22
Programs '''automatically''' backing stuff up for you doesn't help that much IMHO - if it's going to put a '.' at the start of the filename to make it hidden then that helps even less.

I prefer to make my own backups in which I include a time stamp as part of the filename of my backup. I don't use a GUI to deal with a remote server unless using FTP to replace complete files - I use SSH to access in BASH when I will do the kind of editing you spoke of - and even then I copy the file to a new name before  making changes.

---

