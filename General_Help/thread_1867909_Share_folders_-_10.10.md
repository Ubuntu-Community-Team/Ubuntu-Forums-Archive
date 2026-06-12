---
title: "Share folders - 10.10"
date: 2011-10-23
forum: General Help
---

### Post by canhoto on 2011-10-23
How do you share folders with other computers (Mac's) with Xubuntu 10.10?

I don't see any "shared folders" in the menus. I installed Samba, but nothing happens.

---

### Post by zero2xiii on 2011-10-23
I am not sure about the naming on xubuntu,

But normaly you rightclick the folder, select sharing options. Then do the selections. Another option is rightclick, then properties, then look for the sharing options under either permissions or share tabs.. 

This is how it works under Ubuntu and Kubuntu as far as I know.

Maybe it works on xubuntu the same way,

Cherz

---

### Post by canhoto on 2011-10-24
> **zero2xiii said:**
> I am not sure about the naming on xubuntu,

But normaly you rightclick the folder, select sharing options. Then do the selections. Another option is rightclick, then properties, then look for the sharing options under either permissions or share tabs.. 

This is how it works under Ubuntu and Kubuntu as far as I know.

Maybe it works on xubuntu the same way,

Cherz

It doesn't. I installed Samba, I installed Nautilus (which is better han Thunar), but I still have no sharing ptions :-(

---

### Post by Toz on 2011-10-24
@canhoto, if you haven't already, have a look at my reply to your post at: [http://ubuntuforums.org/showthread.php?t=1670223]("http://ubuntuforums.org/showthread.php?t=1670223").

---

### Post by garvinrick4 on 2011-10-24
Have you tried installing 
system-config-samba
```
sudo apt-get install system-config-samba
```
Then opening in System to Admin to samba open samba
then make samba shares by path.
/home/rick/Music
for example.
then in second tab make permissions.
Or make your own Directory to share
sudo mkdir /home/rick/Share
then make a samba share by same path.

---

