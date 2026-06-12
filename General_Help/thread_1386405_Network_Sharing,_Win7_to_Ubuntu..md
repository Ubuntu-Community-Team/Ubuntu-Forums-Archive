---
title: "Network Sharing, Win7 to Ubuntu."
date: 2010-01-20
forum: General Help
---

### Post by rob86 on 2010-01-20
I'm trying to get network file sharing working between two computers, one with Windows 7 and the other with Ubuntu Jaunty. I (assume I) have Samba. Sharing files FROM Ubuntu to Win7 was a breeze - I can easily read files from Ubuntu on the Windows PC, but the other way around doesn't seem to be working. I can't 'see' files from Windows on Ubuntu. 

I'm not too experienced with Windows 7. I right clicked on a folder and clicked Share (or whatever), and then Share with Homegroup. I don't know if that's right or not. I'm looking in the "Network" area of Nautilus, and I see "Windows Network" but when I click on it, it's empty.

I have both computers hooked up to a dlink router.

Any suggestions on how to get it working?

---

### Post by kegansjack on 2010-01-21
i see your problem, windows 7 shares files in a really annoying way, anything you share with "homegroup" computers can only be seen by other windows 7 computers connected to your home group, an effort to make network file sharing easier, as well as locking people into windows 7.  

to share things with any smb enabled device you need to right click the folder, go to properties and then go to sharing and security (may be slightly different for you, im running 64 bit build 7600) then enable sharing of the folder, you also have to go to security and change the folder permissions to allow read/write access to the group everyone.

after you do that it should work, if it still doesnt however go to control panel and change advanced sharing options to allow visibility and the lower encryption methods, also double check that whatever client on linux you are using (smb4k or whatever) is on the same workgroup as windows 7 (NOT HOMEGROUP) you can check your workgroup by right clicking computer in start menu and going to properties. 

if your doing intensive file sharing (lots of large files) id just install filezilla ftp server on the windows machine and mount it in ubuntu, smb shares suck.

---

