---
title: "dosbox only see's 1 dir"
date: 2010-03-17
forum: General Help
---

### Post by reble on 2010-03-17
[SIZE=3]I have the C drive were dosbox is mounted. I have 3 hard drives, C, D, and E. D I use for storage and quick refrence, E hd has all my games on it.  I have figured out how to mount the 2nd hard drive. But dosbox doesn't recognize any directory other then the directory that dosbox is in.  How do I cure this problem?[/SIZE]
[SIZE=3][/SIZE]
[SIZE=3][/SIZE] 
[SIZE=3]Steve[/SIZE]

---

### Post by rCXer on 2010-03-17
could you post the commands you are entering?

---

### Post by reble on 2010-03-18
Below is the dosbox.conf file that I made
-------------------------
[dosbox conf]
@ECHO OFF
mount c \dosbox 
mount f \games\dosbox
promp=$p$g
path=c:\dosbox\utils;f:\games\dosgames
c:
----------------------
the dosbox directory on the c drive is were dosbox is.  c:\dosbox\utils is were an old dos prog called stereo shell is. The directory  f:\games\dosgames is were the dos games are keeped.
 
I have setup and worked on meny a msdos machine for years  My 1st computer was a Timex Sinclair, then a commador 64 and 128 before my 1st msdos sys.  This dosbox is a bit different in behavior then a real msdos sys that I rember.  I even still have a few old msdos command books around.
 
> **rCXer said:**
> could you post the commands you are entering?

---

### Post by rnerwein on 2010-03-18
hi
as far as i can remember my old dos times - to change the drive type: D:
ciao

---

### Post by Zayfox on 2010-03-18
```

D:\

```
Done.

---

### Post by anaconda on 2010-03-18
huh..

sounds complicated.

What is wrong with just opening nautilus (file browser) and going to the folder you have your dos-game and right-clicking on the .exe file and selecting open with dosbox.

then the game folder will be mounted"automagically"

---

### Post by reble on 2010-03-19
I just did a right mouse click on the .exe file but there is no line to click on "open with dosbox".   Would VDMSound clash with Dosbox?    I have both installed?
 
> **anaconda said:**
> huh..
 
sounds complicated.
 
What is wrong with just opening nautilus (file browser) and going to the folder you have your dos-game and right-clicking on the .exe file and selecting open with dosbox.
 
then the game folder will be mounted"automagically"

---

### Post by joshedmonds on 2010-03-19
You say you have 3 hard drives which you name with drive letters. Are these the letters you are used to seeing under Windows? Do you actually have 3 hard drives, or one hard drive that appears to Windows as 3 separate drives (they would then be partitions)?

By default Dosbox will mount a folder ~/dosbox as the c: drive. The easiest way to use Dosbox under Ubuntu is to copy all of your applications to that folder created by Dosbox, mount it as your C drive, and launch the applications from there.

If you have created a /dosbox folder under the root of your system, that would generally not be the best place for it.

If you have 3 drives/partitions, and Ubuntu is installed on the 'C' drive, with the dosbox folder at /dosbox then C is mounted:
mount c /dosbox

The other hard drives/partitions may be automounted by Ubuntu under /media or /mnt. If for example the second partition was mounted under /media/disk1 in Ubuntu, the you would mount in Dosbox as:
mount d /media/disk1

Is that helpful?

---

### Post by anaconda on 2010-03-19
> **reble said:**
> I just did a right mouse click on the .exe file but there is no line to click on "open with dosbox".   Would VDMSound clash with Dosbox?    I have both installed?

The first time you want open a dos-program from file-browser you have to right-click, and select "open with other application", and from there write dosbox in the "Use a custom command".

the next times you just need to right click and select open with dosbox...

And the directory, where you do the open with dosbox will be automagically mounted in dosbox...

PS. it also works from terminal. just go to the folder where the dos-program is, and type:
dosbox nameofthegame.exe

---

