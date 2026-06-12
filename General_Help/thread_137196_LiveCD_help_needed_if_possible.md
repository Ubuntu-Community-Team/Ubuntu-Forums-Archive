---
title: "LiveCD help needed if possible"
date: 2006-02-27
forum: General Help
---

### Post by dwanders on 2006-02-27
I believe I have the Ubuntu Live CD Rebuilding down to fairly stable process. I am running into one gotcha that I cannot seem to figure out. I have followed the Wiki to the T and where I am having trouble is saving the user settings, specifically the session applications I would like to have run during boot up. 

After building my Live CD - I boot into it and make all my changes to the desktop I need. One of those changes is to have a script executed at login - I need to have a parallel (or USB) printer added at boot time so I wrote a little script call add_kiosk_printer to the /etc/skel directory. While running the LIve CD, I added this script to my sessions to have it execute at boot up but it does not seem to be executing. I also have firefox launched at start up with the sessions, and it seems to work fine. 

Any help with this matter is greatly appreciated.

---

### Post by dwanders on 2006-02-28
Thanks for all the responses, but I think I have figured it out - apparently I should have placed my script somewhere in a path, rather than having it in my home directory. I think I have it worked out now. 

Thanks.

---

