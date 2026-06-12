---
title: "Halp: my system wen un got brokend"
date: 2011-02-26
forum: General Help
---

### Post by LiteDrive on 2011-02-26
All I was trying to do was change the folder permissions of my /usr/share folder so I could add a .exe file to my menu. 

So, then I typed 

```
sudo chdmod -rwx------ /usr/share
```

After looking at some documentation regarding file permissions, and found out that in fact was wrong. 

And now I can't boot into Ubuntu at all: my splash screen will load, and then suddenly the screen goes blank. Is there anything I can initiate via the command line to reverse this? 

Edit: 

I was reading a post by someone back in 2006. Whoever posted it seemed to be going through a similar issue. According to someone who posted in his thread, I'm pretty much screwed. I also doubt that in the last five years there have been any recent advances which could seriously do anything major to help my predicament. 

If this is the case, how would I go about recovering my data. Should I make an image of the hard drive and use ddrescue with Windows?

I'm on a dual boot Windows partition currently - that's all I can use. 

I really screwed up, I know.

---

### Post by doas777 on 2011-02-27
well first boot into [Recovery mode]("https://wiki.ubuntu.com/RecoveryMode"), and run this command:
```
sudo chmod -R 755 /usr/share
sudo reboot
```
and see if everything comes up correctly now.

---

### Post by LiteDrive on 2011-02-27
Doing it right now...

I'll keep you posted, and thanks again.

---

### Post by LiteDrive on 2011-02-27
So far everything seems to be working. 

Thanks again!

---

