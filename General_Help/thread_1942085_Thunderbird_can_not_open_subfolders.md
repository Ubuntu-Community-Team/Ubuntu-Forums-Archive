---
title: "Thunderbird: can not open subfolders"
date: 2012-03-16
forum: General Help
---

### Post by WinfriedG on 2012-03-16
I have several problems since some days with Thunderbird and my system:
a) I receive mail from several clients and I distribute them from the general mail intray via filters to subfolders of the local subfolder.
Since some days I get messages, that the files can not be written into the subfolders since the datasystem is read only; however, the filemanger does not say that; all are for me as owner read write 
b) the subfolders do not open so I can not see the mail in them

I tried to repair the indexfiles of the subfolders; however they are not repaired; it seems that Thunderbird considers the folder, which contains as THE LOCAL FOLDER all emails after sorting  into the subfolders, as read only

It may be connected to the observation that since the same period I can not reach root anymore via the command su; it says then authentification failure.

It seems as if something or someone via the Internet had changed my system settings.

I observe these problems since I installed dropbox. I have removed it but unfortunately the problems remain;
I hope someone can make something out of this mass and has a solution for my problem.

Strange enough, I restored my system from a backup, which I made at a time where I could without any problems root by using the command su. But with this system now restored on my netbook the su error persists: authentification failed.

---

### Post by imachavel on 2012-03-16
to be completely honest I ditched thunder bird and just use evolution. So what can I say... not a huge fan or whatever. Have never tried trouble shooting this far into mail client that isn't outlook or something beyond pop.gmail.com or smtp.gmail.com

Wish I was weathered a little further so I could help you out.....

---

### Post by imachavel on 2012-03-16
> 
I observe these problems since I installed dropbox. I have removed it but unfortunately the problems remain;
I hope someone can make something out of this mass and has a solution for my problem.

Strange enough, I restored my system from a backup, which I made at a time where I could without any problems root by using the command su. But with this system now restored on my netbook the su error persists: authentification failed.

drop box? Would you have any problem just uninstalling drop box and getting an Ubuntu one account? So much simpler, try the client interface instead of the web interface worked better for me. Not sure that will address the issue once drop box is uninstalled from the repository. But give it a shot

---

### Post by WinfriedG on 2012-03-17
> **imachavel said:**
> drop box? Would you have any problem just uninstalling drop box and getting an Ubuntu one account? So much simpler, try the client interface instead of the web interface worked better for me. Not sure that will address the issue once drop box is uninstalled from the repository. But give it a shot

As I said I uninstalled dropbox. I tried also Ubuntu one and found dropbox by far simpler to use. But with dropbox I have the suspicion now that it changed the files of Thunderbird.
I found that I don't really need the cloud. So I will work neither with dropbox nor with Ubuntu one.

But I have to say it is not dropbox or ubuntu one which concerns me for the moment it is thunderbird, since if I can not use it anymore I loose many many e-mails, which I need.

And I find it even more  irritating, that I can not root my system with su.
Strange enough, when I start synaptic package management it asks for the password and that works ;also with gparted; and when I open the folder with filemanager as root, it accepts the password. However, it does not consider me as root since I can not change the permissions. I get again the message that the folder is read only?????

---

