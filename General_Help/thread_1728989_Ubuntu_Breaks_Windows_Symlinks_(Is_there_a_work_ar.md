---
title: "Ubuntu Breaks Windows Symlinks (Is there a work around?)"
date: 2011-04-14
forum: General Help
---

### Post by HeadGremlin on 2011-04-14
Hello all, 

I am playing with Ubuntu and Windows 7.  I find that Ubuntu does not deal correctly with Windows 7 Symlinks  (If there is already a post on this let me know but I did not find it)

Windows 7 has a new little program called mklink which creates links similar to ln in Ubuntu.  (Finally) The Microsoft people seem to love their new feature too as when you look in the users directory for example they link stuff all over the place.

Since I dual boot into Ubuntu it is common for me to manipulate files on my windows partition using Ubuntu.  Ubuntu has no difficulty understanding any symlink created by windows 7.  It simply follows it as you would expect.  You can create new ones on the NTFS partition and as long as you view them from Ubuntu everything is fine.

The issue occurs when you go back to windows.  Any syslink created while booted into linux is not recognized.  The *nix created syslinks can be opened and they show some odd characters then the *inux path to the file to which the link points.  

This leads me to the first question.  Is there a way to create a Windows 7 compatible  syslinks while using Ubuntu?

The next thing I noticed was when I make copies of a windows syslink the copied link is created in the new location as a *nix syslink not a windows one.  This means that if I back up a window directory that contains syslinks using ubuntu then restore the directory all the syslinks are broken.

I observe the above behavior both if I copy using cut and paste in the Nautilus or by using cp -d (to preserve the links).  

mv seems to work ok as long as you are on the same partition I will have to try moving between partitions.

Has anyone else noticed this issue?

---

