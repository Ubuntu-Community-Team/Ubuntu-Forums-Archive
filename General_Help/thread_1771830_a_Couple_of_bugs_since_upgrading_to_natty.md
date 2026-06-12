---
title: "a Couple of bugs since upgrading to natty"
date: 2011-05-30
forum: General Help
---

### Post by brand0ng on 2011-05-30
First of all I'd like to say me and my family and friends who ive converted to Ubuntu users have had trouble with natty from the start (needing to mount the drive manually from the terminal after the upgrade being one of the problems) but there are two problems I was curious if anyone else had and fixed. The first problem is an app called "DeVeDe" which is used to convert video files into isos,  it appears to work fine until the end when it errors and says I may be out of disk space.  My work around is to take the MPG file it converted (which didn't seem to be affected by the error) and convert it using bombono into the ISO. Bombono gives me a similar error if I try to use it from the beginning, so devede does the first half without retiring and bombono does the second half, both program's world perfectly before upgrading to natty and I've tried changing settings and reinistalling but nothing helps. My second problem is with my nvidia drivers, they seem to work fine when I'm using my monitor but when I try to use my 47" LED vision as a monitor it says its detecting it as a CRT and only lets m do 1024x768 as my Max resolution.  I know some people will say I should be posting in recede and nvidias forums but thee bugs aren't there fault, as both things world perfect before I upgraded to natty

---

### Post by 4Orbs on 2011-05-30
About the DeVeDe thing: it's possible that your /tmp directory is running low on space (or whichever temporary directory is used by the app). Maybe try running in a terminal:
```
sudo apt-get clean
```
to empty the apt-cache and provide some extra room for temporary files.

---

