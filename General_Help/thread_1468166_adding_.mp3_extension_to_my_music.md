---
title: "adding .mp3 extension to my music"
date: 2010-05-01
forum: General Help
---

### Post by Jguy on 2010-05-01
Hello,

Just made the upgrade to 10.04 and after copying my /home/ directory to my external and back over to my hard drive, the .mp3 extensions have all disappeared. Dolphin still identifies the files as mp3 audio files, but without the extension, Amarok, Banshee or VLC will not play them. Is there anyway to get the media players to play those files, or anyway to add the .mp3 extension onto all of those files at once?

Thanks for any help you can provide.

---

### Post by dino99 on 2010-05-01
need ubuntu-restricted-extras package

---

### Post by eriktheblu on 2010-05-01
I sincerely hope that your mp3s are in a separate directory, as that will make everything easier.

I'm certain there's an easy one step process to do this, but here's what I can do with my limited knowledge.

Assuming you have mp3s and only mp3s in ~/music start with 
```
ls ~/music/ >~/Desktop/mp3list.txt
```
Open the mp3list.txt on your desktop, copy and paste into Open Office Calc in column A. Some clean up may be required; you want to end up with only a listing of file names.
In cell B1, use the following formula
```
="mv '~/music/"&A1&"' "'~/music "&A1&".mp3'
```
Transpose this down to cover all the files.

Copy the B column into the terminal.

---

### Post by happyhamster on 2010-05-01
A nice (gui) way to bulk rename stuff is using a program like pyrenamer (which is a standalone application) or, in case you're using the thunar file-manager, there's a bulk-rename extension (it's part of the package thunar-media-tags-plugin). Good luck.

---

### Post by Jguy on 2010-05-01
dino99: That was not the problem, but thanks anyway.
eriktheblu: I never would have thought of doing that and thanks. Although it doesn't work for this scenerio, I bet I can find a use for it elsewhere.
happyhamster: Thanks, albeit slow since I have all my music in seperate folders, it still worked. Thanks!

---

### Post by mixmaster on 2010-05-01
for future reference, open a command window, go to the directory containing the music and type

find . -type f -exec mv {} {}.mp3 \;

command lines may seem arcane but they can be very fast.  Note that this command will affect all files in directories under the current directory and so is suitable if you have a tree of music folders.

Beware that it will rename ALL files.  Don't use it if your music is scattered through other folders.

---

