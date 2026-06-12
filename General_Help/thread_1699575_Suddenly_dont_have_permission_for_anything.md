---
title: "Suddenly dont have permission for anything"
date: 2011-03-03
forum: General Help
---

### Post by unbuntunewb on 2011-03-03
I dont know what happened but I suddenly do not have permission to write to my external devices such as sd cards or hard drives and its driving me crazy. I have to use nautilus every time to do anything and thats a pain. also I have "usb0" on my desktop that I cannot unmount that I have no clue of what it is.

How do I make this all go away?

I couldnt get my external HD to mount earlier so I did some digging around and saw someone had the same problem and they put a command in the terminal to auto mount. I did the same. Since then I have had this trouble. I think they are related.

please someone help me, I want the system to be as it was permission wise as it was when it was installed.

UPDATE

Ive been reading on here and someone with a similiar problem thought that maybe it was due to the external device not being properly unmounted before removal. When I tried to unmount my external HD I get this error message:

/media/usb0 is not in the fstab (and you are not root)
what does this mean?

UPDATE

I tried to edit the permissions in nautilus just now and the owner is root, I went to change it to me as in my user name and I get this error:

Sorry, could not change the owner of "usb0": Error setting owner: Operation not permitted

also I cannot change anything else. any ideas?

UPDATE

I managed to get my computer to read my sd cards but It still wont read my external HD, when I go to /media/usb0 then right click and try to dismount I get this error:
DBus error org.gtk.Private.RemoteVolumeMonitor.NotFound: The given mount was not found

any ideas?

---

