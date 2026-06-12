---
title: "Nautilus or share-admin?"
date: 2010-04-09
forum: General Help
---

### Post by Steven_S on 2010-04-09
While trying to fully understand networking in a Windows-Ubuntu mixed environment, I have been reading up on mounting ntfs disks with full permissions, changing file permissions, samba and making shares through Nautilus. 

In one thread, I read an instruction to use "share-admin". 

My question is: when creating and managing shares, is gksudo share-admin better (safer, less chance of things going wrong, plays nicer with applications such as OpenOffice, ...) than gksudo nautilus? 

Both are GUI, but I of course don't know if the commands it runs are the same or similar (wish there was an option to see what the application is doing in the terminal, so that I can better learn what is happening).

---

### Post by gradinaruvasile on 2010-04-09
Just use shares-admin. That one uses samba configurations directly and its more stable than the nautilus share. Also normally you dont need root rights to share from nautilus.

---

### Post by Morbius1 on 2010-04-09
There is nothing less stable about about nautilus-share. By default nautilus-share allows a user to share any directory he owns which is why you don't have to become root. I would contend that for the average user nautilus-share is all he would ever need. It still follows the samba rules and smb.conf can still control many aspects of it's operation.

There are many advantages to nautilus-share including:

ease of share creation
no need to restart any services
visually see which directories are shared in Nautilus ( although there is a known bug - so that still needs a little work )
can create shares from the command line
can always get a quick list of what's shared and how they are shared by using: net usershare info

But let's be clear, there are limitations to Nautilus-share.

Everything about Nautilus-share is at a global level. If you create two shares that require authentication then everyone with a samba password can access both shares. Nautilus-share cannot allow John to only have access to one share and Mary to only have access to another. ( Actually there is a way to do that but it's not pretty ).

Classic-share can do that plus a whole lot more. Nothing can match the kind of control you can have with Classic-share.

The choice is yours obviously but I would recommend that you use one method or the other and not both. It's technically possible to use both but you really have to be on top of things. You might inadvertently use both methods on the same target directory, or one method on a parent directory and another on a child directory, for example, and things start getting gummed up.

---

### Post by gradinaruvasile on 2010-04-09
I disagree about the stability. Nautilus share sometimes just did not work for me. I dont know exactly why, but sometimes the folders were not visible on other computers. 

Shares-admin on the other hand always worked consitently for me. And i didnt had to restart services either. Also, the shares are more simple to control at least for me.

---

### Post by Steven_S on 2010-04-09
All very good to know, thanks! I'll stick with share-admin for now, as I am the only one setting things up. Share-admin uses classic shares then?

But... I have messed about with nautilus also. If I want to start "clean", is it enough to just restore my samba config file to the default?

---

### Post by Morbius1 on 2010-04-09
Actually, I would argue that nautilus-share is less susceptible to user errors or at least bad user experiences. For example, let's say I create a public share at /home/morbius/Documents using shares-admin. I will end up with a share definition that looks like this:

> [documents]
path = /home/morbius/Documents
available = yes
browsable = yes
public = yes
writable = yesI was brought up using classic shares and I'm fairly certain that is correct. There's only one problem. It won't work. The remote user will not be able to write to that share despite the share being "writable".

Why? Because for file sharing to be successful samba authorizations and linux file permissions need to be in sync. The permissions on the target are:
> drwxr-xr-x 2 morbius morbiusNo matter how hard samba tries, the only person who can write to that share is morbius. The new linux user walks away bewildered.

Do the same thing with nautilus-share:
> [documents]
path=/home/morbius/Documents
comment=
usershare_acl=Everyone:F,
guest_ok=y
If you've never seen a nautilus-share definition before you'll just have to trust me that this is equivalent to the classic-share definition above.

This works. Why? Because the very last step of the share creation process in Nautilus asks me the following question:
> Nautilus needs to add some permissions to your folder "Documents" in order to share it

The folder "Documents" needs the following extra permissions for sharing to work:
  - write permission by others
Do you want Nautilus to add these permissions to the folder automatically?Clicking "Yes" will reset the linux permissions to
> drwxrwxrwx 9 morbius morbiusI do apologize, it appears I've turned into an evangelist for nautilus-share :oops:.

To answer you question, you don't need to reset smb.conf to rid yourself of the Nautilus-shares. Just go into Nautilus and "unshare" them. Run the terminal command: **net usershare info**  ( which shows you all your current nautilus-shares ) and when it comes back blank they should all be gone.

---

### Post by Steven_S on 2010-04-10
Many thanks, Morbius! Figuring out HOW it all works is, to me, equally important to making it all work...

---

