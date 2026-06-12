---
title: "Recover deleted files"
date: 2011-10-31
forum: General Help
---

### Post by Joshua on 2011-10-31
I think I accidentally deleted some files and I don't understand how it could have happened.

I was organizing some video and picture files and had two Nautilus windows open.

In Window A I navigated to a single directory with all of my files.  In Window B I navigated to a single directory where I wanted to copy my video (.MOV) files.

Then in Window A I clicked the search button and typed mov in the search box.  The contents of the directory were filtered so that I only saw the .MOV files.  I selected all those files, right clicked, clicked cut and then pasted them into Window B.  Everything looked good.  All the files showed up in Window B and I opened a couple to make sure they worked.  Then I went back to Window A and all the files were still there (they weren't actually cut).  I assumed this was because I was working on an external mounted drive and sometimes file operations behave differently.  So I selected all of the .MOV files and hit delete.  A window popped up saying they could not be sent to the recycle bin (again this is on an external mounted drive so I think that's normal behavior).  I clicked delete all.  At that point the files disappeared from BOTH Window A and Window B.

I double checked Window A and it looks like it's filtering within the correctly location.  The pink box at the top says Search results with a drop down for location and another drop down with the name of the correct directory.

How could this have happened?  Is there any way to get my files back?

---

### Post by Joshua on 2011-10-31
It looks like my heading was changed.  I wanted this thread to be about more than just recovering the files I lost - although that is really important to me.

The bigger issue, though, is that I can't figure out where I made a mistake.  I haven't tried to repeat this because I don't want to do something that will make it impossible to recover my files, but it looks to me that Nautilus is not deleting files the way a normal user would expect.

---

### Post by raja.genupula on 2011-10-31
Hi this thing can help you

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by Joshua on 2011-10-31
Wow.  That worked really well.

I installed testdisk and used the photorec tool that is described on that page.  I had all the old SD cards with my photos and videos, but they had been re-formatted.  photorec found all the missing files.

I still don't understand how I could have deleted the files in the first place.  The expected behavior should be that files in the source directory would be deleted and files in the destination directory would remain.

---

