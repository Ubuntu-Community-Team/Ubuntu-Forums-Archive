---
title: "Smb Share in fstab"
date: 2006-04-11
forum: General Help
---

### Post by jonnymccullagh on 2006-04-11
I have successfully mounted an smb folder using:
sudo mount //server/sharedfolder /home/jonny/documents/myfolder/ -o username=myusername,password=mypassword

I would like to have this automatically mount at boot. I understand that I should use fstab but I'm not sure of the settings and web searches have not helped much. Can anyone point me in the right direction? This is what I have below:

//server/sharedfolder /home/jonny/documents/myfolder/ smbfs uid=myusername,gid=???,dmask=700,fmask=700	0       0

Any help is appreciated - I think this might be a useful addition to the main FAQ.
cheers,
jonny

---

### Post by spanishwasabi on 2006-04-11
//server/share /mountpoint smbfs userid=foo,passwd=bar,rw 0 0

Enjoy,

G

---

### Post by jonnymccullagh on 2006-04-12
I tried this and into the fstab entered:
//server/folder /home/jonny/documents/folder/ smbfs userid=jonathan@DOMAIN,passwd=mypass,rw 0 0

However now when I restart the machine and check to see if the share was mounted the /home/jonny/documents/folder/ directory doesn't even exist now.

I had created it earlier with permissions (chmod 777) but now the fstab seems to have removed it. Am I doing something wrong?
Thanks for the help,
jonny


(
Incidentally:
I had tried it without the domain but got errors when doing
sudo mount -a

The error was: session setup failed: ERRDOS - ERRnoaccess
)

---

### Post by MJN on 2006-04-12
I'm not at my machine right now to check my own config however does your fstab line not need **auto** in it to automatically mount the share at boot?
 
Mathew

---

### Post by jonnymccullagh on 2006-04-12
I added auto but I am still having problems. The folder I created on my own filesystem does not appear but I cannot re-create it as a folder with that name "Could not make folder".

I've now got:
//server/folder /home/jonny/documents/folder/ smbfs userid=jonathan@DOMAIN,passwd=mypassword,rw,auto 0 0

I also see the mounted folder on my dekstop but when I click on it:
/home/jonny/documents/folder/ does not exist

Please help - I can feel Windows-users eyes boring into me!

thanks, 
jonny

---

### Post by terryroe on 2006-04-12
Jonny,

I'm not an expert (yet), but I've been able to successfully mount my Windows shares following the guidance in this article:  [http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html](http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html)

One thing I noticed about your fstab line is that it looks like you're trying to use the Windows login in userid.  You need to use your Linux userid there.  (I don't know if 'userid' is even a valid entry.  See below.)  For the Windows info, use username and password, like this:

//server/share  /mnt/share  smbfs  username=terry,password=yourpassword,uid=terry  0  0

My Windows login and my Linux login happen to be the same.  But username is for the Windows login and uid is for your Linux login.

HTH,

TR

---

### Post by jonnymccullagh on 2006-04-12
Thanks Terry I'll have to bear that in mind. I actually got it working just before you posted.
I used the info in [http://ubuntuguide.org/](http://ubuntuguide.org/) and created a /root/.smbcredentials file with my windows domain username and password.

and then in fstab:
//server/folder        /home/jonny/documents/folder/  smbfs    credentials=/root/.smbcredentials       0       0

This method worked a treat!
Now I have only 1 major hurdle (and 101 minor ones) to go!
If anyone can help with FTP proxy issues please see my other post,
Thanks for the help,
jonny

---

### Post by jonnymccullagh on 2006-04-13
ok,
I still need help - I do not have write access to these network shares. I tried adding ,dmask=777,fmask=777 like so:

//server/folder /home/jonny/documents/folder/ smbfs credentials=/root/.smbcredentials,dmask=777,fmask=777 0 0

but I cannot paste or write to the folders as they seem to be owned by root of group root - how can I get this to be owned by jonny of group users??

Thanks in advance for any help,
jonny

---

### Post by jonnymccullagh on 2006-04-13
Sorry - answering all my own questions here but I hope this helps someone else. I get read and write permissions I followed a good tutorial at:
[http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html](http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html)

So I now have the following and it works!

//server/folder        /home/jonny/documents/myfolder  smbfs    credentials=/root/.smbcredentials,uid=jonny,gid=jonny      0       0

Thanks to everyone in the community for help,
jonny

---

