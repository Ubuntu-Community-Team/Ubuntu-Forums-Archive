---
title: "Mounted device not showing up on desktop"
date: 2011-02-17
forum: General Help
---

### Post by kingofthething on 2011-02-17
I have two external hard drives mounted to my computer. They both work and are accessible. The one shows up on my desktop when it is mounted just fine. The other one does not. I went in to Configuration editor-apps-nautilus-desktop and checked the volumes_visible. That makes the other one not visible/visible but not the one I am having problems with. I read somewhere that devices must be named for it to show up and both devices are named, I even changed the name and that didn't do anything. Again, this device shows up in my computer but not on my desktop like all my other devices do. If anyone has any ideas on how I can get this external hard drive to show up it would be greatly appreciated. 

Thanks,
Paul

---

### Post by tredegar on 2011-02-17
Is there a reference to the disk that does not show on the desktop in **fstab** ?

If you don't know what I am talking about please plug in both disks and then give us the output (inside code tags, *please* [Click Go Advanced, then the # icon]) of the following commands:```
mount
cat /etc/fstab
```

---

