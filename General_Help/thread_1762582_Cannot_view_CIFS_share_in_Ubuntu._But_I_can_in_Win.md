---
title: "Cannot view CIFS share in Ubuntu. But I can in Windows..."
date: 2011-05-19
forum: General Help
---

### Post by Roasted on 2011-05-19
I have a FreeNAS server running CIFS shares. I just tried out Deja Dup on my home directory and backed it up to my CIFS share. This is about 200gb worth or so, I believe. 

After it was done, I went to browse into the directory. I've restarted the CIFS service on the server, rebooted the server, and rebooted Ubuntu, I STILL cannot browse my directory. It says:

Sorry, could not display all the contents of "jason": Invalid argument.

Yet I can SSH into it and do an ls listing and see all of the .tar.gz packages that Deja Dup created. Likewise, I can browse to it just fine in Windows.

What is Ubuntu doing that it doesn't like to see these files? It's a huge, huge pain in the rear... How can I fix it?

---

### Post by apollothethird on 2011-05-19
> **Roasted said:**
> I have a FreeNAS server running CIFS shares. I just tried out Deja Dup on my home directory and backed it up to my CIFS share. This is about 200gb worth or so, I believe. 

After it was done, I went to browse into the directory. I've restarted the CIFS service on the server, rebooted the server, and rebooted Ubuntu, I STILL cannot browse my directory. It says:

Sorry, could not display all the contents of "jason": Invalid argument.

Yet I can SSH into it and do an ls listing and see all of the .tar.gz packages that Deja Dup created. Likewise, I can browse to it just fine in Windows.

What is Ubuntu doing that it doesn't like to see these files? It's a huge, huge pain in the rear... How can I fix it?

Are you able to browse any other Windows or Samba shares from this Ubuntu computer?

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by Roasted on 2011-05-19
Yes. I can. I can actually browse this exact share when it's empty or has other data in it. But once I run the backup and it pushes several hundred .tar.gz compressed data bits over to it, suddenly I begin to get invalid argument.

I just spoke to a samba dev in an IRC room and he wants me to run some commands later and see what it comes up with. So far he presumed it to be a bug with samba, as I had the same issue with PCMan/Thunar/Nautilus/Dolphin, but like I said, worked fine in Windows and worked fine on the FreeNAS server itself.

Even using smbclient and navigating to it in terminal I couldn't view it.

smb: \> cd jason
smb: \jason\> ls
Invalid packet length! (65588 bytes).
Receiving SMB: Server stopped responding
Read error: Success listing \jason\*
Error in dskattr: Read error: Success
smb: \jason\>


But like I said, once I delete the .tar.gz data, I'm fine. Weird...

---

### Post by Roasted on 2011-05-19
Well, a lot has happened since I posted here.

I went into the Samba IRC and talked to some friendly Samba developers. One helped me out extensively and ultimately found this bug:

[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/500195](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/500195)

This bug was directly involving FreeNAS and CIFS. We began to think, what if it's Nautilus? What if it's .gvfs? So I installed PCMan, Dolphin, Thunar, and Nautilus. All 4 reacted the same.

Instead of re-typing what I put in the bug report where I commented, I'll just copy and paste:




I can confirm similar findings even on newer software, although my findings were slightly different.

Server = FreeNAS 8 (64 bit). Running a ZFS Raid1 Array on two 500gb drives.
Client = Ubuntu 11.04 (64 bit).
Running the latest SMB/CIFS available on 11.04.
(I also duplicated the issue on a different FreeNAS 8 (64 bit) box using two 80gb drives in ZFS Raid1 as well)

I ran into the issue spoken above, though I didn't run into it at 627 files. I ran into it at 575 files. From there I got prompted "Invalid Argument." If I had 574 files on the server (all 1.0MB in size), I could browse just fine. Once I added the 575th file, I could not browse. If I SSH'd into the FreeNAS box and removed one single file, I was able to browse again.

I got the same results with PCMan, Thunar, Nautilus, and Dolphin. When I repeated the same steps with an Ubuntu 10.04 machine being the server instead of FreeNAS 8, I did NOT exhibit any issues. I was able to write thousands of files with no issues at all. These files were written from an Ubuntu 11.04 (64 bit) client.

Oddly, I did NOT have this issue when I connected to the FreeNAS server from a Windows 7 client. It seems to be something to do with Samba/CIFS in Linux (Ubuntu in particular is what I tested) versus FreeNAS 8.

I formatted my FreeNAS 8 box and put FreeNAS 0.7.2 (64 bit) on it. I also set up a ZFS based array. I did NOT exhibit any problems there. FreeNAS 0.7.2 performed as expected well beyond thousands of files.

Due to all of the scenarios I applied these findings at, it's definitely something with FreeNAS 8 and/or ZFS. I'm doubtful it's a ZFS issue due to my ZFS success on 0.7.2. I made the FreeNAS developers aware in the "freenas" IRC chat room. I'm not sure what movement will happen from here, as it is out of my hands.

Until then, I will be utilizing Linux on my file server instead, as I have not had any CIFS/SMB related issues to any degree in the Linux-to-Linux or Windows-to-Linux scenarios.

---

### Post by captainsquinty on 2011-05-29
> **Roasted said:**
> 
...

After it was done, I went to browse into the directory. I've restarted the CIFS service on the server, rebooted the server, and rebooted Ubuntu, I STILL cannot browse my directory. It says:

Sorry, could not display all the contents of "jason": Invalid argument.


I'm having a very similar problem, with a NAS device that runs a Samba server, a "NexStar FX".  I am able to access the share and files without any trouble using Vista, but with Ubuntu 11.04, I can access the share, but when I try to open 'most' of the subdirectories, I get the same error, "Sorry, could not display all the contents of..."

The one subdirectory that will open is empty.  It smells a lot like an older issue I found here:
[http://ubuntuforums.org/archive/index.php/t-762525.html](http://ubuntuforums.org/archive/index.php/t-762525.html)
or 
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/217137](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/217137)

I'm pretty new to Ubuntu, and stumped. Anyone know what to do?

---

### Post by Roasted on 2011-05-30
I'd have to do a little research to see what NexStar is based on, as I've never heard of it. But I ended up ditching FreeNAS all together because of this issue.

The reality is, it may work on Windows, but that doesn't mean it works 100%. Considering with my issue Ubuntu works flawlessly until you tack FreeNAS into the picture, it paints an obvious issue there. Ubuntu via CIFS works fine with other Linux machines, Windows machines, etc etc. That's why I stopped using FreeNAS because I had to use what did the job for me, and whatever bug I was seeing was preventing me from using it.

The best you could probably do is post a bug to NexStar. I may be wrong, but I really just don't see how it's an Ubuntu issue if it works fine with all other systems except the one acting as the file server. That was just my experience. I may be totally wrong, but my current setup with Linux as a file server is working great, for what it's worth. :popcorn:

---

### Post by JoeAshley on 2012-10-28
Hey guys.. I know this is an old post but I am experiencing a "similar" issue. I am accessing FreeNas 8.2.0 CIFS share from Ubuntu 11.04. All 64 bit BTW. The difference here is I was able to access a folder with well over 8000 folders under it. I was consolidating music folders. My problem started with i added more files with strange names. Using the LS command I would see a "<F6>" in the file name of some files. Again prior to adding these files I could play/view the folder with well over 18000 total files in the tree.

Thanks for the great forum.

---

