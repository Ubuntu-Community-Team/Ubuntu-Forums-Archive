---
title: "Can you use your windows partition as you Wine directory?"
date: 2010-05-27
forum: General Help
---

### Post by rmkscrambler on 2010-05-27
Sorry if I posted this in the wrong location but I was wondering if their is a way to use my windows partition as my wine directory.

I do have a dual boot system vista and ubuntu but thought it would be nice if I didn't have to switch back and forth for some things. 

Since I all ready have windows installed with all the required files, directory, and registry is their any way ubuntu could pick those up for running windows programs. Instead of emulating them in wine. 

In theory I could install my programs under windows and run them under ubuntu if ubuntu recognized my windows partition as c drive instead of OS.

Just some thoughts I had I am a new user to ubuntu and still learning.

---

### Post by wilee-nilee on 2010-05-27
If you have MS already running wine is a waste of time. Rebooting is like 2 minute job at most.

---

### Post by rmkscrambler on 2010-05-27
True but then I could just use windows.

I know some install Qemu or such emulators. 

I just thought if you could use the existing directory it would be less (fat) so to say. and give me more options to stay in ubuntu.

---

### Post by wilee-nilee on 2010-05-27
> **rmkscrambler said:**
> True but then I could just use windows.

I know some install Qemu or such emulators. 

I just thought if you could use the existing directory it would be less (fat) so to say. and give me more options to stay in ubuntu.

You might have the thread put in the wine forum as their is at least one person who is the self appointed master of the universe and all things it contains, I have them blocked.

---

### Post by Darkness Des on 2010-05-27
Yes. Yes you could. All that needs to be done is to make a symbolic link. Thought seeing as your windows partition is PROBABLY not going to be named "drive_c", I suggest making symbolic links within the ~/.wine/drive_c directory. This can be done by:
```
ln -s /path/to/real/file /path/to/imaginary/file
```
An example being around the lines of
```
ln -s /home/des/bin /home/des/Documents
```
That would put a symbolic link in my documents that points to my scripts.

---

### Post by rmkscrambler on 2010-05-27
I have been trying to switch since MS decided my Digital camera should be blocked from my xp computer via their c:\windows\inf\srusbusd.inf file
which block devices they don't like so to say. sure I can alter the file after every update but it just makes me mad that they do it. Sorry for the rant but some things aren't right.

---

### Post by rmkscrambler on 2010-05-27
thanks I will try that

---

