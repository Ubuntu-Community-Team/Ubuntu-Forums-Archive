---
title: "Urgent help, deleted user from all groups"
date: 2009-12-05
forum: General Help
---

### Post by ztrange on 2009-12-05
Hello, I know this sounds very very newbie.

I was messing with some "advanced" groups thing and tried to add my user to a group. however, I wrote 

sudo usermod -G group user
instead of
sudo usermod -G group -a user

So, now I'm out of every group and don't know what to do. I don't even want to turn off my computer because I'm afraid I won't be able to login again. Is there some way to recover the groups list and add myself again to them??

Thanks for your help. I'll keep looking for an answer in google.

---

### Post by ztrange on 2009-12-05
Ok I added back myself to adm and admin groups (Don't know if adm was relevant. Then, I was able to enter the System/Administration/Users and Groups and add a new desktop user to my computer. Then I checked the groups list it got and added myself to all those groups.

But I'm not sure if that's enough.

Any help, reaffirmation will still be appreciated

---

### Post by ztrange on 2009-12-05
Wel... It seems I just freaked out. I just rebooted my computer with the changes above and it rebooted ok. I learned a little about groups in my little days of Arch linux; I made the call and well, here I'm back. If this may help anyone, I give the list of commands that I used.

First, to get myself into trouble:

sudo usermod -G groupx ztrange
The one I was intending to use, was 
sudo usermod -G groupx -a ztrange

Then, I added my user back to adm, admin
sudo usermod -G adm,admin -a ztrange

Finally, when I was able to add a new user to see the group list Ubuntu defaults a desktop user, I used this command to fully restore my user.
sudo usermod -G dialout,fax,cdrom,tape,audio,dip,video,plugdev,fuse,vboxusers,disk -a ztrange

That's all, thanks anyway to all the community

---

