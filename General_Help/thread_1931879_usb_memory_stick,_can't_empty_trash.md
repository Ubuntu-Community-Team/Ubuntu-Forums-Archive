---
title: "usb memory stick, can't empty trash"
date: 2012-02-26
forum: General Help
---

### Post by goodbye-windows(tm) on 2012-02-26
Hi All,

I have an old-ish 1 GB usb memory module. When I try to empty the trash, it won't let me-xubuntu says the drive is already full. In fact, it is not full, I cleared everything from it, so it's actually empty.

It has no trash can that is visible, but it does have a hidden folder called .trash-1000. I think this is supposed to be the trash can. Inside the hidden folder, there are 2 folders, one called 'info' and the other called 'files'. In order to empty the trash and restore the module to a useful status, the 'files' folder has to be deleted or the files in the 'files' folder must be deleted.

I also use SD cards and a small SD drive, which has the same trash can configuration, which is how I know what I need to do in order to make the usb memory stick functional again.

When I try to delete the 'files' folder, I get an error, 'unable to move folder to trash, unable to create trashing info file, no space left on drive.

I also tried to delete the contents of the folder by selecting the files inside 'files' folder and deleting them, but I get the same error.

I did notice the permissions for the folders does not allow any access (says none). When I try to change the permissions so I have read and write permission, the screen immediately changes back to 'none' again. Maybe this is my problem? 

I might be able to reformat it using gparted, but without a hidden trash folder, I'm not sure that I actually fix anything-

Any idea what i need to do to restore the usb memory stick to useful service again?

TIA.

Art

---

### Post by sudodus on 2012-02-26
Recently I had a similar problem. I think you will get and should allow to have a trashcan according to this line from the output of ```
ls -la
```
```
drwx------  5 sudo sudo 4096 2012-01-21 11:59 .Trash-1000
```

Then it should work in your file browser to delete = move to trashcan, and later to recover if you like or to delete definitely.

But as you write, you can also clear the trashcan manually. If you do so using terminal commands, it should work. But if you have no access to the trashcan, it won't. So first you must set the permissions and maybe also the ownership using ***chmod*** and ***chown***. If that does not work either, you had better repartition or at least reformat your stick.

---

### Post by westie457 on 2012-02-26
Hi, what I usually do to recover that lost space and remove the .Trash folder at the same time is run the file browser with root privileges ```
gksudo nautilus
```
and use Shift+Delete to permanently remove the folder.

Warning.... **be careful what you delete** as you will be able to delete any and all files while the root file browser is open.


Just realised you are using Xubuntu so the command might not be the correct one for the file browser if you do not have nautilus installed.

---

### Post by goodbye-windows(tm) on 2012-02-26
TY both.

Just as I finished the original question, my wife passed by (with her laptop in tow) and commented she had used the same usb memory stick previously, and she had to manually remove the data from the trashcan too. She uses a brand W OS for her work computer, her employer makes her use the brand W laptop. It's the only other brand W system in the house though and it rarely comes to the house.

I gave it to her and she plugged it in to her system. She brought it back 10 minutes later, said she had no problem deleting the 'files' and 'info' folder.

When I plugged it back into my system, it was working fine. The 2 folders in the trash folder were automatically created again, and I tested everything. Everything worked. I filled the drive again, and deleted everything without issues. 

So, the brand W OS did something to the memory stick, although I have no idea what::> After the trip though her work computer, the permissions for the trash folder and it's internal folders looked the same as before though!!  

I'll mark the thread as solved, and thank you so much for the info on the command line permission changes.

Regards,

Art

---

### Post by goodbye-windows(tm) on 2012-02-27
The plot thickens............... 

After testing the heck out of the memory stick on my xubuntu system, I thought I was home free. But, this morning I woke up and found my primary computer would not accept my password! I have no idea how to proceed, and I'll post a separate message as the password problem might not be related to the fix of the memory stick at all.

Still, I can't help but wonder what the brand W OS did to that memory stick while it was connected....

---

### Post by sudodus on 2012-02-27
> **goodbye-windows(tm) said:**
> The plot thickens............... 

After testing the heck out of the memory stick on my xubuntu system, I thought I was home free. But, this morning I woke up and found my primary computer would not accept my password! I have no idea how to proceed, and I'll post a separate message as the password problem might not be related to the fix of the memory stick at all.

Still, I can't help but wonder what the brand W OS did to that memory stick while it was connected....
Yes, probably it is not related, but who knows ...

Anyway use this link to reset your password
[[COLOR="Red"]_http://www.psychocats.net/ubuntu/resetpassword_[/COLOR]]("http://www.psychocats.net/ubuntu/resetpassword")

---

