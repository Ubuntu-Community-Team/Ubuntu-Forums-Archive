---
title: "Making Windows Internet Explorer shortcuts (.url) work in Ubuntu -- redux"
date: 2010-05-14
forum: General Help
---

### Post by bokl on 2010-05-14
On Windows systems webpage URLs can be saved to individual hyperlink/shortcut files (.url extension). .url files are plain text files with the following format
```
[InternetShortcut]
URL=http://www.google.com
```
When you doubleclick it on a Windows system the browser associated with .url files opens the associated URL.
You can organize .url files in folders and subfolders and easily copy and sync them between different Windows computers with different default browsers.

Ubuntu does not support such files out of the box. That problem was brought up in this 2007 thread:
[http://ubuntuforums.org/showthread.php?t=495131](http://ubuntuforums.org/showthread.php?t=495131)
A solution was later provided in that thread, but it is complex (for new users) and must be repeated after each clean reinstall of Ubuntu. 

A launchpad bug post was made: [https://bugs.launchpad.net/ubuntu/+bug/185165](https://bugs.launchpad.net/ubuntu/+bug/185165)

Things were looking good, a fix seemed likely. 
 
Three years later the bug remains. It was brought up again in this 2010 thread: [http://ubuntuforums.org/showthread.php?t=1453240](http://ubuntuforums.org/showthread.php?t=1453240)

I am making this post to again raise awareness of this problem (the old thread has been locked for further posts). I myself have thousands of .url files and would like to use them the same way on Windows and Ubuntu out of the box. I hope it gets fixed. Windows users in the habit of using .url files otherwise risk running into frustrating trouble when starting with Ubuntu. If you do use these files you likely use them as often as others use bookmarks in Firefox. That is, very often. 

(Note: Please do not open up a debate on how good/bad using .url files is. Let's keep this thread focused on getting the fix and changing Ubuntu to fit a group of new users' pattern of browser use, not on changing the users.)

---

