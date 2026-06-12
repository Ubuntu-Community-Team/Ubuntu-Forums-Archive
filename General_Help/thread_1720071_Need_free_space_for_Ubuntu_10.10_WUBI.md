---
title: "Need free space for Ubuntu 10.10 WUBI"
date: 2011-04-02
forum: General Help
---

### Post by marort on 2011-04-02
One of my computers is running WUBI (Win7 + Ubuntu 10.10). Recently, every time I boot  in Ubuntu, I get a Disk Usage Analyzer message:

“This computer has only 143.3 MB disk space remaining. You can free up disk space by removing unused programs or files, or by removing files to an external disk.”

I already clean some files and remove some programs; however, I only got about 200 MB more of free space.

I am not even sure why Ubuntu is complaining about space since I do not have much in it. I only created two profiles (users) but there is practically no user files in it and there are only a few programs that I added (Virtualbox, Wine, Cryptkeeper) to it. I have another computer with only Ubuntu in it for my daily use and this is where I keep all my files. I am aware it is using an small partition (25 GB) but it should be enough for what I have, I believe.

I had Virtualbox running MS Vista temporarily as a test. I remove it (MS Vista, not Virtualbox) but did not get much of space back. So, probably there some other steps I missing here to delete some other hidden files.

There is one more thing I should mention; this very same machine used to run Ubuntu 10.04 under Win7 not too long ago. After having some problems with the upgrade I decided to remove 10.04 and just do a clean install of 10.10. I do not know if some of the old files could still be there and I was supposed to manually removed them once I uninstalled 10.04. I used to have about 7 – 8 gig of user directory  (some in Cryptkeeper).

user@ubuntu:~$ df -Th

Filesystem    Type    Size  Used Avail Use% Mounted on

/dev/loop0    ext4     24G   23G  238M  99% /

none      devtmpfs    1.5G  276K  1.5G   1% /dev

none         tmpfs    1.5G  196K  1.5G   1% /dev/shm

none         tmpfs    1.5G  428K  1.5G   1% /var/run

none         tmpfs    1.5G     0  1.5G   0% /var/lock

/dev/sda2  fuseblk    286G   88G  199G  31% /host

---

### Post by bcbc on 2011-04-02
You've a fixed virtual disk (/ubuntu/disks/root.disk) of 24GB and it reports that you've used 23GB. You tell Wubi how big to make it when you first install and it remains fixed at that size (24GB). So now that it's nearly full it's complaining.

When you uninstall Wubi it removes the virtual disk and everything on it, so it is not possible that some files could have been transferred from a 10.04 install to a fresh 10.10 install.

If you want to figure out what's taking up the 23GB you can run the disk usage analyzer (baobab). I'd run it as root (Alt-F2, gksu baobab), then stop it immediately or it will analyze /host (the windows partition as well), which you have access to but doesn't count towards the 24GB space on your root.disk.
Then go to Edit, Preferences, unselect /host, then click on the drive icon to scan your virtual disk.

---

### Post by marort on 2011-04-02
Thanks for the advise BCBC. It did not occurred to me to run DUA as an admin. I did as you said and found immediately a 'MS Windows Vista.vdi' file taking almost 19 gig of HD (WOW! I did not have any idea how much room Vista could need). I tried to delete within BAOBAB, but it would just move the file from Home to Root. So, I ended up doing if from the terminal. Now I got almost 20 gig free. 

I also have learn that if I am running Virtualbox, once I remove an OS I will also have to remove the files manually.

Have a great weekend!

---

