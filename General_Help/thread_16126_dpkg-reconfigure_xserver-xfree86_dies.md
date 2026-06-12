---
title: "dpkg-reconfigure xserver-xfree86 dies"
date: 2005-02-19
forum: General Help
---

### Post by Rottweiler on 2005-02-19
I'm trying to get my gdm and xfree resolutions set to sane values. So I did
  
  sudo dpkg-reconfigure xserver-xfree86
  
 This worked great on the first system I tried. But on the second one it dies part way thru and does not write a XF86Config-4 file.
  
 It dies right after the part about "writing DRI section". No error message, just goes back to the command prompt. Couldn't find anything in the logs tho not sure where to look.
  
  Tried every conservative setting I could think of including running it in runlevel 1. No change.
  
  Any help appreciated.

---

