---
title: "Samba share can be written to by Windows, but not Ubuntu"
date: 2011-11-26
forum: General Help
---

### Post by dragonfire22 on 2011-11-26
I have Samba install on an Ubuntu Server that I'm using for a home file sharing server. However, for some reason only my Windows PCs can read and write to the shares correctly. When I use Ubuntu, I can create a folder and save a document onto the root of the share. But when I do, a lock icon appears on the folder or document and I can't write to the subfolder and the document then only opens in read-only mode.

I've read who know how many forums and articles to try and fix the problem. I just can't figure out what I'm doing wrong. Currently I have one samba username that is used by all my computer wanting to use the share, so shouldn't each computer have the same permission problem? I've tried nearly ever single force mask command I could find by still nothing. When ever I make a directory or document with Ubuntu, the permissions become -rwxrwxr-x no matter what mask I apply. The shares themselves have the owner of Nobody and are assigned to Nogroup. I have attached my smb.conf file if any one would like to look at it. Any ideas would be greatly appreciate.

---

### Post by bluexrider on 2011-11-26
> **dragonfire22 said:**
> I can create a folder and save a document onto the root of the share.  But when I do, a lock icon appears on the folder or document and I can't  write to the subfolder and the document then only opens in read-only  mode.

Think about this. You are saving it to ROOT and a lock appears! Which means you don't have the permissions set correctly to access.

Why would you save it to ROOT anyway? 

Choose another folder to "share" give it read-write, excitable permissions. Or set up anonymous user.

[Samba Configuration]("https://help.ubuntu.com/10.04/serverguide/C/samba-ldap.html#samba-ldap-samba-configuration")

---

### Post by dragonfire22 on 2011-11-26
Even if I go into a subfolder it does the same thing, I have full rw access set on both shares on the server side.

---

### Post by dragonfire22 on 2011-11-26
I understand it's a permissions issue, but I don't know what is happening to cause it. Also, I just figured out that if I browse to the share from Nautilus I have full permissions like I should, but if I mount it like a hard drive from the terminal, the permissions are messed up.

---

### Post by bluexrider on 2011-11-26
Check your NETBIOS and WINBIND settings

---

### Post by dragonfire22 on 2011-11-26
I'm sorry but I don't understand, where are these settings and what do I need to look for?

---

### Post by bluexrider on 2011-11-26
This is a checklist to help diag you problem.

[http://samba.org/samba/docs/man/Samba-HOWTO-Collection/diagnosis.html](http://samba.org/samba/docs/man/Samba-HOWTO-Collection/diagnosis.html)

**The Official Samba 3.5.x HOWTO and Reference Guide**


[http://samba.org/samba/docs/man/Samba-HOWTO-Collection/](http://samba.org/samba/docs/man/Samba-HOWTO-Collection/)

---

### Post by dragonfire22 on 2011-11-26
I did the tests and everything came out fine. However, the tests were for a Unix server and Windows client. My Windows PCs are working fine, it's my Ubuntu computer that's having the permissions issue.

---

### Post by Jacobonbuntu on 2011-11-26
> **dragonfire22 said:**
> I did the tests and everything came out fine. However, the tests were for a Unix server and Windows client. My Windows PCs are working fine, it's my Ubuntu computer that's having the permissions issue.

please don't take my word as an absolute truth, but shouldn't the mask settings be 0755 instead of 0777?
see this manual [https://help.ubuntu.com/11.04/serverguide/C/samba-fileserver.html](https://help.ubuntu.com/11.04/serverguide/C/samba-fileserver.html)

My samba share is set to creation mask 0755, and all works fine from windows as well as Ubuntu, as well with the permissions as the ownership of new documents.

edit: again don't take my word as the absolute truth, and someone correct me if I am wrong, but you might be mixing up the mask settings with the chmod-commands

---

### Post by dragonfire22 on 2011-11-26
I tried that an still no luck. What I don't understand is when I browse to the share I have the correct permissions, if I mount the share, anything I create is given the permissions -rwxrwxr-x no matter what mask I use.

What do you mean mixing them up?

---

### Post by Jacobonbuntu on 2011-11-26
> **dragonfire22 said:**
> I tried that an still no luck. What I don't understand is when I browse to the share I have the correct permissions, if I mount the share, anything I create is given the permissions -rwxrwxr-x no matter what mask I use.

What do you mean mixing them up?

be aware of the fact that I am working on a "need to know" base, so I am no expert. Having said that, I just managed to get the job done in my case, :), after finding out that permissions can be a pain in the *** :).

In my case, the way in which the share was mounted was the problem also. in the end, this entry to my /etc/fstab file worked fine:
//192.168.0.102/share /home/jacob/satellite cifs auto,iocharset=utf8,uid=jacob,gid=users,credentials=/root/.cifscredentials,file_mode=0775,dir_mode=0775 0 0

as you can see, you also will have to create a .cifscredentials file in /root, with the entries:
user=username
password=password

**edit:** I guess I was wrong about the chmod/mask thing and the "0777" (although 0755 should work too) just read a little more about it. The mix up was mine :oops:. I do believe however that the way my share is mounted should work for you to. I had exactly the same thing, going into the share via network was ok, mounting it otherwise was the problem.

---

### Post by Morbius1 on 2011-11-26
I'm getting confused. When you add a something to the share it shows as being locked where? On the server or the client?

If it;s the client how are you mounting the share. Through Nautilus or do you have your own mount command or fstab entry?

---

### Post by dragonfire22 on 2011-11-26
> In my case, the way in which the share was mounted was the problem also. in the end, this entry to my /etc/fstab file worked fine:
//192.168.0.102/share /home/jacob/satellite cifs auto,iocharset=utf8,uid=jacob,gid=users,credential s=/root/.cifscredentials,file_mode=0775,dir_mode=0775 0 0

This completely fixed my problem, thank you so much! I've been messing with this thing for I don't know how long, thank you!

---

### Post by Jacobonbuntu on 2011-11-26
> **dragonfire22 said:**
> This completely fixed my problem, thank you so much! I've been messing with this thing for I don't know how long, thank you!

ah, fantastic!!

I must give the credits to this site
[http://www.mattvanstone.com/2007/11/automatically-mounting-windows-smb-shares-in-ubuntu-v3/](http://www.mattvanstone.com/2007/11/automatically-mounting-windows-smb-shares-in-ubuntu-v3/)
that was my guide to automounting my NAS
great that it worked for you too!!

---

