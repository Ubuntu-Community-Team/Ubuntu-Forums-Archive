---
title: "Problem of Accessing XP files through Ubuntu"
date: 2006-04-12
forum: General Help
---

### Post by ububaba on 2006-04-12
Earlier, I have been able to play on VLC in Ubuntu stuff which was actually lying on the 
XP HD, i.e. by copying it first to my "home" directory in Ubuntu.  While in Ubuntu through 
System>Admnistration>Disks, even now I can access the files on XP HD, but I am not 
able to click the VLC icon to play the video.   VLC does not start but flashes this message 

Cannot Launch entry 
Details: Failed to change to directory '/home/MyDir' (Permission Denied)

Totem cannot be used either. Does some one know how to solve this rather basic problem 
about accessing.

---

### Post by mrchrisblau on 2006-04-12
Total newbie guess here.. but who knows, it might help.

I read somewhere that ubuntu will have a hard time changing/writing files if those files are in an NTFS filesystem (the one most XP installs use). Ubuntu can view and copy NTFS files but can not edit nor make (if I remember correctly). 

Once again, a shot in the dark.

IF that is the case then you need to install winxp using FAT32 (ubuntu will be able to read/write/edit/etc in FAT32).

---

### Post by pitkali on 2006-04-12
Does launching movie player through sudo (like 'sudo totem file_name' in some terminal window) helps?

Regards,

---

### Post by taurus on 2006-04-12
You may want to look at the permission of the file you just copied from Windows to your home directory!  Sounds to me like a permission problem...

---

### Post by ububaba on 2006-04-12
[QUOTE=taurus]You may want to look at the permission of the file you just copied from Windows to your home directory!  Sounds to me like a permission problem...[/QUOTE]

Thanks man. You hit the nail on the head. It _is_ a [COLOR="Red"]permission[/COLOR] problem. I came to
the conclusion after having checked other messages. Now I am trying to figure
out, how do I get that permission? I am the only user/administrator. :-k

---

### Post by aysiu on 2006-04-12
Applications > Accessories > Terminal ```
sudo chown -R ububaba:ububaba /home/MyDir
sudo chmod -R 755 /home/MyDir
```

---

### Post by ububaba on 2006-04-12
[QUOTE=aysiu]Applications > Accessories > Terminal ```
sudo chown -R ububaba:ububaba /home/MyDir
sudo chmod -R 755 /home/MyDir
```[/QUOTE]
Thanks guys. I think I am getting somewhere. Fun to find out when things go your way.

---

