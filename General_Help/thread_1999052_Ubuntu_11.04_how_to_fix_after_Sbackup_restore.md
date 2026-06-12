---
title: "Ubuntu 11.04 how to fix after Sbackup restore"
date: 2012-06-07
forum: General Help
---

### Post by CunManny on 2012-06-07
I've been using Ubuntu for about 2 years now, and I've managed to find solutions to all my problems without having to personally ask for help, but now I found a problem and I can't find any information via google or searching the forums.

I usually never turn off computer, yesterday when I woke up the desktop background picture had disappeared, and when I went to open Evolution for my emails, the first time use wizard started.  (Dogs might have walked over keyboard at night and started the problem).

I did have Sbackup (simple backup) installed and running.  I figured I would just restore from Sbackup.  I tried to restore, it had errors, and when I logged in I had a different looking ubuntu screen, and even though I could select my user name and enter a password it wouldn't let me log in.  

I booted with a CD, cleared the Ubuntu partition, and started with a fresh install of 11.04.  After the fresh install, i download Sbackup from the ubuntu store, and I restore from a full backup of May 30th (/etc, /home, /usr/local, /var) I am able to restore all 4 directories without errors.

After I restore, I then reboot.  Once I reboot I get my background picture on the desktop, and all my files.  However, when I click on the ubuntu store I can get a list of "installed software" and it seems all the programs I use are listed, however when I try to find and run the programs I can't find them.

If I try to update either via update manager or by terminal, it creates an error (lists firefox as error), then I am not able to do anything else with the programs.  if I open the software center after that, i get an error message that reads "items cannot be installd or removed until the pacakge catalog is repaied.  do you want to repair it now".  If I try to repair it just crashes

I was under the imperssion that with sbackup, I could easily change a hard drive, use the restore file, and have my ubuntu desktop just as I had it, but that doesn't seem to be the case.

Any ideas of how I can resolve the issue?  I was thinking doing another fresh install, then somehow get a list of all software I had installed, install all the software that I need, and once software is installed, then do a restore, would that work?

Thanks in advance for any help or tips

---

