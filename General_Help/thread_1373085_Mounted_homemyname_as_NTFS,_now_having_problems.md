---
title: "Mounted home/myname as NTFS, now having problems"
date: 2010-01-05
forum: General Help
---

### Post by Pernig on 2010-01-05
I have installed a RAID array in my computer so I have had installed Ubuntu again. Last time I had a large NTFS partition mounted as /home/james/files, so that I can share it between Windows and Ubuntu. This time I decided to just mount it as /home/james (my home folder) to make it a bit easier. I knew it would be a bad idea to mount as /home, but thought I would be OK to mount as this. However I have been having some problems.

The first problem that occurred was when I went to start Firefox, it wouldn't allow me to create a profile in my home folder. Secondly, when I went to import my Evolution mail and settings (located at /home/james/Downloads/evolution-backup.tar.gz), when it got to removing the backup file it stalled. Also when I went to install Opera there was an error along the lines of being unable to install due to write permissions.

So I have gathered that Ubuntu is having problems writing settings files etc in the NTFS partition (/dev/mapper/efjggbac4) with me having mounted it where it is. Is there any way around this eg. changing the permissions in /etc/fstab, or is it really not a good idea to mount an NTFS partition to this location at all? If so I will probably reinstall and use symlinks to avoid further hassle.

Thanks in advance for your help.

---

### Post by rax_m on 2010-01-05
I think it's probably a bad idea to mount that partition to your home directory. Ubuntu and other applications will use the home directory to store configurations and other local files. If you mount the partition there, those config files will not be available and will probably cause quite a few apps to fail. 

It's a much better idea to share it one below your home directory. Or the other popular place (for me at least) is /media/share

---

### Post by audiomick on 2010-01-05
Hi.
If "James" is your user name, you will have problems.
My user name is "mick" and my /home has my stuff in /home/mick
I don't think you will be able to write any config stuff to ntfs, and I don't think you should put an ntfs partition at a mount point that the system wants to use.

I would suggest going back to what you had before,
/home/James/and_don't_spare_the_horses 
(sorry, couldn't resist that...;) )

If you want things like open office to store to there by default, you can change that for nearly everything in the options of the relevant program.

---

### Post by Pernig on 2010-01-05
Thanks for the quick replies. I will have it mounted as something other than there then.

---

### Post by rockyjones on 2010-01-05
I don't have any problems with Ubuntu writing config data to a NTFS share.  I use the technique where I have a large NTFS partition that I mount to a directory I create in my home directory as Share (/home/joe/Share).  I then use sym links to all my standard directories (documents, viedos, music, etc.) that are on the NTFS partition as well as .mozilla and .mozilla-thunderbird.  

Firefox has no problems using the NTFS partition through the sym links and neither does Thunderbird.  By doing this, I can isolate all my data from whatever OS I'm currently using (makes upgrading much easier), test other distros, or use windows on a second hard drive and have access to all my data and email.

---

