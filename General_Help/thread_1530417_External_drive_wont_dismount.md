---
title: "External drive wont dismount"
date: 2010-07-13
forum: General Help
---

### Post by w00ly on 2010-07-13
I have a 100gb external USB hard drive. I downloaded about 50gb of files to it. I had transmission downloading a torrent to it but it was taking a long time so I stopped it about 2 hours ago. 

I closed transmission a half hour ago and tried to dismount the drive. Now I'm getting "Writing data. To prevent data loss wait until this has finished before removing or disconnecting media". It's been sitting at this for about half an hour now and I need the drive! I have no idea what it's writing but it shouldnt be writing anything...there wasnt anything that was being transfered to/from the drive. How do I safely dismount this thing? It seems like the "safe dismount" is stuck :???: 

Basically fresh installation of 10.04. Any help whatsoever is greatly appreciated!!

---

### Post by w00ly on 2010-07-13
Bump

---

### Post by ajgreeny on 2010-07-13
This is probably because transmission has left the torrent download in an unfinished state, and therefore the disk is showing as still being written to.

I have no idea how you can overcome this, and suggest either that you try to force an unmount, or even better just reboot the computer; the shutdown will unmount the disk, no problem.

---

### Post by w00ly on 2010-07-13
Sigh, I shutdown the computer and it froze on shutdown. I got "The system is going down for halt NOW!" on an ssh session and all the programs closed out but it froze with the wallpaper up. I tried switching desktops with ctrl alt f1-f8 to see if I could see any messages but the screen is completely black. In fact I cant even get back into the GUI now :frown:

So now my system is stuck and I'm afraid if I disconnect the drive or forcefully poweroff the system my drive will be corrupted!! I'm starting to really dislike linux...I dont even recall having any dismounting issues in windows :cry: Sad because I really like ubuntu but it has a lot of flaws

Edit: Ok never seen this happen before but I ^C the "system is going down for a halt" message and I'm still able to SSH into the system. Is there anything I can do from my SSH session to get it to dismount/shutdown properly??

---

### Post by w00ly on 2010-07-13
Ok so I tried killing processes in SSH that i thought might have been accessing the drive still but no luck. So then I tried sync but it froze. Lastly I sudo shutdown now and it finally shutdown. I restarted the system and could see my data on there. 

However when I connect the drive to my windows PC now the drive doesnt appear and I cant see any data! I was afraid this was going to happen :( Can anyone tell me how to repair my drive please??

---

### Post by zerin on 2010-07-13
Try plugging it back in your Ubuntu Machine againa nd this time dismount (right click it and do safely remove device) it properly, see if that works, worked for me once with my external Drive in NTFS. that happens sometimes when i unplug it and i forget to unmount. Hope i helped. keep trying dude.

---

