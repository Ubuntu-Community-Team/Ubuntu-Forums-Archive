---
title: "Ubuntu on PS3 - Mac running Parallels Win 7 - share mount issues"
date: 2009-11-20
forum: General Help
---

### Post by FJMerlin on 2009-11-20
Hello Ubuntu forums!!!  This is my first post so please go easy on me.  Ive been searching this forum and many others for a couple of months.  Ive been able to get Ubuntu loaded on my PS3 and access it via SSH with my MacBook Pro.  I was then able to setup everything needed to mount a drive from my MBP to my Ubuntu and rip blurays to it.  I load up Windows 7 in Parallels and use AnyDVD HD to mount the virtual drive and then tsMuxer to mux it.  Then the m2ts file to Handbrake in Mac to convert it to an mkv file.  Everything was working just fine until....

I bought an iMac and attempted to implement the same process.  So first thing I tried to do was SSH into Ubuntu with the new iMac.  No dice.  As you all probably already know, the SSH key was tied to my MBP, so I had to do a ton of crap and change some settings, to be honest I cant even remember what I did, but I finally got it working with the help of searching these forums.  

But now the hard part.  Im able to SSH into Ubuntu, but when I try to mount my drive it keeps failing on me.  Error 111 or something.  So I check my smbclient list for my iMac and it gives me... NT_Connection_Refused.  
code...
sudo smbmount //10.0.1.12/BlurayRips /home/merlinps3/blurayrips -o username=merlinps3,password=abcdefg,uid=1000,mask=000
This is the same code I use to mount from my MBP which works.  Granted I change the IP to my MBPs IP.  So Im assuming Samba/SMB is still tied to my MBPs IP somehow.  If I plug that same external drive back into my MBP, it mounts just fine.  

Ive been in my Samba smb.conf file multiple times and still dont know what to change.   Ive changed Wins = yes.  Ive added 10.0.1.12 to the Wins server field.  I even added some other code I found online and no dice.  Still the same error messages.  

Im starting to think there is a permission problem somewhere, but I simply cant find it.  Ive tried adding accounts to all machines, like a guest account for example, that I added to my Mac, and my virtual machines still doesnt let me mount or view the smbclients.  Is there an SMB client file I need to modify to add my new IP to?  

Now the tricky thing... when I go to Ubuntu, Im able to view everything on my iMac via SFTP.  I can even see the volume I want to mount right there but cant mount it or link it.  

Im running 8.10 currently but started the upgrade process to 9.10 (or was it 9.04) last night before bed.  This morning I woke up to Ubuntu asking what I wanted to do with the smb.conf file.  I had a bunch of choices but picked "replace current file with distributors".  I figured if it isnt working now, whats the harm in replacing it?  

As you may be able to tell, Im fairly new to Linux but I am willing to learn and try different things.  So I would really appreciate any suggestions or advice you guys might have.  Even if you tell me to go pound sand!  Im at work till 5pm, so I cant post my smb.conf file until later.  

Thanks!!

---

### Post by FJMerlin on 2009-11-20
I forgot to mention, I also formatted my PS3 and reloaded Ubuntu just to see if that would do it.  No dice, still an issue.  

Also, I changed the SSH key as I mentioned above to allow SSH access from my iMac, in ddoing so I mustve removed the key from my MacBook Pro.  So when I tried to SSH in from my MBP, it didnt work.  Is there a way to add both IPs so I can SSH from either?

Thanks again.  This forum moves so fast, I posted this an hour ago and its already on the 4th page!


EDIT:  I found an option in OS X I forgot to check on my iMac, hopefully this one takes care of it.  i think I forgot to turn on SMB file sharing in OSX.  That would be funny.

---

