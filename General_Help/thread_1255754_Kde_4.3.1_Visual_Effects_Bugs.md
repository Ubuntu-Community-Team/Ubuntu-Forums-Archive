---
title: "Kde 4.3.1 Visual Effects Bugs"
date: 2009-09-01
forum: General Help
---

### Post by lakerssuperman on 2009-09-01
Hello,

I just upgraded to Kde 4.3.1 from the backports repo.  After I did this I began noticing graphical bugs.  For example, windows no longer smoothly minimize.  They simply turn into an outline.  Also, the panel thumbnail previews appear as black boxes with no texture.  Has anyone else experienced this?  My video card is a Radeon 4800 running the 9.8 driver.  Any help would be appreciated.  Thanks.

---

### Post by lakerssuperman on 2009-09-01
I have found the issue.  When setting the effects to Trilinear filtering it causes this issue.  I have set it back to Bilinear and it has been corrected.  However, one bug remains.  While watching a video in VLC with video set to the X-video extension the video is fine until I minimize the VLC window to the panel  When I restore it the video window is black but the sound continues.  Any one have any ideas about this one?

---

