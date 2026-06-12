---
title: "Cannot get bash script to run"
date: 2011-10-14
forum: General Help
---

### Post by ZaphodFJ on 2011-10-14
On my old PC (Ubuntu 10.04), I wrote a nice little script for backups.  It worked fine, from a portable hard drive.

Here it is:
```
#!/bin/sh 
mkdir study 
cd study 
mkdir embryo 
cd embryo 
mkdir .wine 
cd .wine 
mkdir drive_c 
cd drive_c 
mkdir PMAIL 
cd .. 
cd .. 
cp -R -v ~/.wine/drive_c/PMAIL ./.wine/drive_c/PMAIL 
cp -R -v ~/Desktop ./Desktop 
cp -R -v ~/Documents ./Documents 
cp -R -v ~/Pictures ./Pictures 
cp -R -v ~/public ./public 
cp -R -v ~/.thunderbird ./.thunderbird 
cd .. 
mkdir finished 
rm -r -v grandfather 
mkdir removedgfather 
mv -v father grandfather 
mv -v son father 
mv -v embryo son
```

Then I moved to a new PC, running 11.04 and it does not work.

So far, I have:

[LIST]
[*]Done everything I can think of with chmod.  Nomatter what I do, even if I sudo it, permissions remain as -rw-------
[*]Go through Nautilus, find the file, right-click to look at Properties and set permissions.  The "allow executing file as program" box unchecks itself, as soon as I check it.
[*]Changed the top line to #!/bin/bash - still no response.
[/LIST]
Yet if I run the commands from a prompt, it all works and I get a new backup, with the old 'generation' of backup renamed.

Somebody reading this is thinking "This is easy" - please share your wisdom :-)

---

### Post by TeoBigusGeekus on 2011-10-14
Is the script located on an ntfs file system?

---

### Post by ZaphodFJ on 2011-10-14
Yes - it was before though.

---

### Post by TeoBigusGeekus on 2011-10-14
Ntfs cannot understand the meaning of file permissions.
Move the script to a linux file system (ext3, ext4, etc.), change its permissions and then move it back to your ntfs drive.

---

### Post by ZaphodFJ on 2011-10-14
I move to ~/temp, change permissions and... it works.

I move back to /media/LaCie and... read-only.

weird.

---

### Post by TeoBigusGeekus on 2011-10-14
Is the ownership of the /media/LaCie mountpoint ok?
Can you run other scripts/apps from there?

---

### Post by gnush on 2011-10-14
```
sudo chmod +x script.sh
sudo chown yourusername script.sh
```

Does that work? Are you the owner of /media/LaCie?

---

### Post by ZaphodFJ on 2011-10-15
In answer to the Qs and suggestions:

- no, other scripts do not run
- yes, mountpoint ownerships look fine
- chown and chmod suggestions do nothing.

The ownership shows as my username.  This was also my username on the old PC.  Is it possible the two are confused?

---

