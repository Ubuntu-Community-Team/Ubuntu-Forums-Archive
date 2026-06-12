---
title: "Salvaging data from a misbehaving installation"
date: 2012-05-30
forum: General Help
---

### Post by nash black on 2012-05-30
Hi all,

I've been having quite a bit of trouble since accidentally filling my ubuntu partition. I learned the hard way that one does not simple log in after doing so.

Anyway, I cleared some space with the live CD and rebooted with no problems. I immediately updated to 12.04 and have been having serious issues since. 

I cannot log in for more than a minute without the system freezing, especially if I do anything window intensive. I did manage to disable the Nvidia 173 driver but this didnt change anything.

After filling the hard drive, I would get weird messages about it being set to read only mode, I still get them sometimes when I'm trying to run things in terminal from the live CD or from the Recpvery Console login.

example after loging out after a partial freeze:
"/var/lib/sudo/*my name* read only file system"

A few times when logging out after a partial freeze I got a message stating the the Gnome Settings Daemon is not responding - is this what is causing the system to lock up?

I'm running 12.04 (although I suspect the install didn't completely work... I think Ive seen 11.10 in a few places...) with Win XP installed on a separate drive. The Ubuntu drive also has a partition for GRUB, etc and another storage partition that both OSs use. The storage partition seems to to functioning well.

I wanted to remove my data and just reinstall becuase I have a feeling this is one of those times, but I can't get to my data in the main (admin) login. It appears to be encrypted. When I boot into the live CD and run nautilus, the files in that folder arn't there, only the "access your private data" executable and the corresponding read me file are visible. Same when I use a windows-based executable to view the ubuntu partion. In either case, the executable does nothing and the command line entry does even less.

I can only log in through Ubuntu very briefly, too briefly to transfer any significant files off the drive. Although all of my critical data is backed up, there is a lot on there that I would really like to have.

Is there a way to me to access and backup this data? Anyone have any idea what is going on? Is there a way to reinstall without losing the files on this admin login - i don't care about programs, just the personal files.

Thanks and sorry for the book!


Edit: one other weird thing. I can't reboot, I have to shut down and restart. If I try to reboot I get errors before and after GRUB like "cannot read file" or "hd1 out of disk" It never seems to have issues logging in to Windows. I thing I was getting those after filling the partition before, but I definitely have at least 10 GB free on every partition now - cleared out of the recycle bin as well...

---

