---
title: "Lost Pictures Folder"
date: 2009-12-18
forum: General Help
---

### Post by Monrizzy on 2009-12-18
Hi folks!
My wife seems to have managed to loose all my pictures that I had stored on my hard drive.  Basically when I go to places instead of seeing the folder called Pictures I see a folder called Trash:Pictures.  When I go to the trash bin I don't see any of the picture files.  Is there a way I can restore that folder?

---

### Post by Barriehie on 2009-12-18
Perhaps have a look in ~/.local/share/Trash/files

Barrie

---

### Post by Monrizzy on 2009-12-18
Thanks Barrie.

I'm a bit of a n00b and don't know exactly how to follow the file structure in the OS.  Could you provide a little guidance please?

---

### Post by Barriehie on 2009-12-19
> **Monrizzy said:**
> Thanks Barrie.

I'm a bit of a n00b and don't know exactly how to follow the file structure in the OS.  Could you provide a little guidance please?

:) Certainly!  In linux the ~ is indicated to represent your home folder.  This is typically /home/*YourLoginName*  Filenames preceeded with a . are hidden, they can be displayed in nautilus, or thunar, file browsers by typing CTRL-h <control and h>, this is a toggle, pressing CTRL-h again will turn off display of hidden files.  So, your trash bin is located in **~/.local/share/Trash/files** The Pictures folder is **~/Pictures** or the long way; **/home/*YourLoginName*/Pictures**.  The file browser MAY have an issue with moving/renaming those files/folder and if it does post back here and I'll tell you how to move them via the terminal.

Barrie

---

### Post by Barriehie on 2009-12-19
A preventative measure, besides backing up your pictures, would be to put your original picture files in a folder like ~/pics and then create symlinks from that folder to the ~/Pictures folder.  This way the symlink will be deleted but not the original file.

In the terminal: Applications > Accessories > Terminal

```

mkdir ./pics                   # make the holder directory
mv ~/Pictures/* ./pics         # move existing files to holder directory
ln -s ~/pics/* ~/Pictures      # create the links

```

Of course when you add pictures to ~/pics you'll have to rerun the ln -s command to add the new links to the ~/Pictures folder.  It won't overwrite the existing links so this will work.  If your wife deletes anything in the ~/Pictures folder at this point just run the ln -s command.  See, from the terminal, man ln, to get the manpage on the ln command.

Or, get a thumb drive...!

HTH
Barrie

---

### Post by Monrizzy on 2009-12-19
Not in the trash folder.  When I go to places the folder that use to say pictures is now replaced by a folder that says > Trash: Pictures Then when I click on it is says > **Could not find "trash:///Pictures".**
Please check the spelling and try again.

---

### Post by Barriehie on 2009-12-19
It seems then that they are gone. :(  Linux is adept at deleting files, unlike some other OS's...  I can only suggest at this point to keep a backup of them on a thumb drive or to use, per my prior post, the symlink method.  I did that on my machine last night and it worked just fine.  Only failure option to that method is someone using either the terminal or a file mgr. and deleting them via either of those interfaces.

There are ways to undelete files in linux but from what I've read the recovery process must be initiated pretty soon after the mistake is noticed.

If the Pictures folder has been deleted it's easy enough to recreate either via the terminal or your file mgr.

Barrie

---

