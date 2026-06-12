---
title: "concerning the transfer of files from destop to home folder."
date: 2009-12-19
forum: General Help
---

### Post by zigNzag on 2009-12-19
When ever I move a file from my desktop to my home folder it copies the file instead of moving it. In fact xubuntu is acting like my desktop is on a whole different hard drive. I have to use xubuntu because my dell 1420 is affected by the bad sector bug in Ubuntu(main). If anyone can tell me how to correct my file transferring issue between my home folder and desktop that would be great.

P.S
I know the sectors on my HDD are not bad and have double checked this with Windows 7.

---

### Post by zigNzag on 2009-12-19
bump

---

### Post by Chesamo on 2009-12-19
Are you using Thunar or the Terminal to move?

In the Terminal, you can use the```
mv filenamehere ~/
```command to move a file from the current working directory into your Home folder.

---

### Post by Dennis N on 2009-12-20
> **zigNzag said:**
> When ever I move a file from my desktop to my home folder it copies the file instead of moving it... 

On Xubuntu,

Hold Shift key down while dragging from your Desktop to the Home Folder Window. This will move the file instead of copying it.

---

### Post by joeknoodle on 2009-12-20
I recommend always using copy and paste, rather than a cut (or drag as a cut).

If your system has problems the original file is okay, and all you gotta do is go back to the original folder to make a delete.

Just FYI, your mileage may vary.

---

### Post by ubun_two on 2009-12-20
> **joeknoodle said:**
> I recommend always using copy and paste, rather than a cut (or drag as a cut).

If your system has problems the original file is okay, and all you gotta do is go back to the original folder to make a delete.

Just FYI, your mileage may vary.

But "moving" or "cut and paste" is way faster than "copy and paste", as long as the move is within the same drive/partition.

On "move", only the file pointer needs changing, but on "copy and pasting" the whole file contents actually needs to be written to another location of the drive.  It makes a lot of difference when moving large files.

---

### Post by zigNzag on 2009-12-20
yes, I just don't see why the desktop seems to be on a different partition. Is their any way to correct this.

---

