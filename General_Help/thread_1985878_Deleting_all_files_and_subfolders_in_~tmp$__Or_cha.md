---
title: "Deleting all files and subfolders in ~/tmp$ ? Or changing ownership ?"
date: 2012-05-23
forum: General Help
---

### Post by computeratin on 2012-05-23
I'm troubleshooting trying to fix a known typo in a driver. I've found 1/2 a dozen tutorials, nothing is working. I've got a bunch of beginner guides open for the terminal commands, bash, etc. I keep running in to permission errors. I've been trying root / sudo/ chown, yada yada. Every time I think I'm making progress I end up nowhere.

So, I had an idea. But, I don't want to blow up my install if it's a bad one.

Part of what I've been playing with is running the .sh w/ --noexec --keep to extract it in to ~/tmp$. Then I need to mod one letter in one file and it's supposed to work. I've tried everything I can think of and everything in the tutorials; none of it works. I keep running in to permission errors when I'm in sudo. And when I'm in root and open the file in gedit there's nothing in it.

I didn't check the contents of~/tmp$ before I started this; so I have no idea what "belongs" there and what is stuff I've extracted messing with this.

Is it like doze? Can I just blow everything out of temp and anything that is needed will write itself back? I'm thinking that maybe part of the problem is that when I try new methods of fixing it that either the files are not being over written with each new extraction attempt or there's some kind of corruption that is causing the permissions to become "stuck".

And just for giggles (since I'm just about hard up enough to try it) what happens if I sudo chown <username>.<groupname>  ~/tmp$ and change it to me.me? Will I blow up my install? I just need it long enough to get this stupid driver fixed and I can reset it to root.root.

I'm thinking (maybe I'm wrong) that if I change the permissions of the parent directory that all of the child objects will inherit those permissions and I can finally get the access I need to fix this stupid thing!

---

### Post by ItsPerryXD on 2012-05-24
log into root if possible.
su root
you'll be prompted for a password if its been set in the past.

Otherwise you have to find out who has ownership 
ls -l (whatever directory it is)
then chown

If i was getting mad at the thing I would find the object and probably chmod 777 (file) to allow read, write, and execute capability.

worst case scenario delete whats in tmp. Tmp is for temporary files anyway.

---

### Post by steeldriver on 2012-05-24
wait... I'm confused

do you really mean ~/tmp$

or ~/tmp

or /tmp

or /tmp$

these are all different things - the first two are dirs in your home directory and nothing to do with the system (although you may have some problems deleting ~/tmp$ since $ is a shell metacharacter and would need to be escaped)

... although nothing in /tmp should be system critical either fwiw

---

### Post by matt_symes on 2012-05-24
Hi

Just reboot. If it's /tmp then its contents will be wiped anyway.

Post a link to the tutorial you are trying to follow and let us help you install the driver.

Kind regards

---

### Post by Habitual on 2012-05-24
> **ItsPerryXD said:**
> ...If i was getting mad at the thing I would find the object and probably chmod 777 (file) to allow read, write, and execute capability.

That doesn't fix a damn thing.

---

### Post by Zvlwab on 2012-05-24
try this:
```
sudo chmod -R a+x+rw
```
-R makes the command recursively set permissions on the items inside the folder too.
a means for everyone.
+x means executable.
+rw means readable and writable.

---

