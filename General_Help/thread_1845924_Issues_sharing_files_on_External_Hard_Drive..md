---
title: "Issues sharing files on External Hard Drive."
date: 2011-09-18
forum: General Help
---

### Post by Dividex on 2011-09-18
Hello Everyone,

I've been trying to share an external drive connected to a Ubuntu machine.  I've been able to successfully share just about everything i needed, but I've ran into a few issues.  I'm sharing these folders to windows machines.  When I set a shared folder with "Guest" access I get a "windows cannot access \\xxx\xxx message.  If I try to access the other folders without the "Guest" access permission, everything works fine.  Windows will ask me for user-name/password.

Once I input my password, I'm also able to access those folders with the "Guest" access permission located on the external.  If I make a "guest' folder on the machines Internal hard drive, there's no issue accessing it through the windows machines.

I'm only a novice when it comes to Linux, but I'm guessing its some weird permission issue with the mounted drive.  When I right click the drive>Permissions i get " The permissions of disk1 could not be determined".

Device is mounted at /media/disk1   EXT4 File system

Any help is appreciated

Thanks! :P

---

### Post by PYearwood on 2012-01-08
I just read your posting and your possible solution. I tried it with Windows 7 and got the request to sign in.
I went back to my external hard drive and checked the permissions I had granted. I had the guest permissions checked. On what my brother in IT calls a W.A.G. , I unchecked the Guests (allow everyone) I was able to access the external folders. 

Now, when I boot into Ubuntu 11.04, I use Gigolo to connect automatically. I found that it works if the Guest permissions are again unchecked. 

I home this helps.

Paul

---

