---
title: "Removing all traces of browsing history from the computer (Ubuntu 10.10)"
date: 2010-12-27
forum: General Help
---

### Post by Ir0nMa1deN on 2010-12-27
I have the vlc media player plugin which lets me open up videos in my browser instead of having to download them. Sadly, this plugin is very buggy and makes videos freeze sometimes. This happened to me while watching a video and I right clicked it to see if I can save it to my hard drive from there. I saw an option to "Open in Movie Player" so I did, and it played the video perfectly. I shut down my computer and turned it back on later, and when I opened up Movie Player, under File>, the videos still show up, and I can play them. I tried removing all browsing history from Google Chrome and checked my flash video settings (removed all sites and cookies) but the videos still show up in Movie Player. Also tried emptying the temp folder. Is there any way I can get these videos off my computer?!?!

---

### Post by Casper35th on 2010-12-27
Have you installed Ubuntu Tweak? You can use it to clean system cache and other hidden files. Go to applications>Ubuntu Software Center> Search Ubuntu Tweak

---

### Post by karthick87 on 2010-12-27
To install ubuntu-tweak,
```
sudo add-apt-repository ppa:tualatrix/ppa
```
```
sudo apt-get update
```
```
sudo apt-get install ubuntu-tweak
```

---

### Post by Ir0nMa1deN on 2010-12-27
I downloaded and installed Ubuntu Tweak but what do I do now? I see "clean cache" - is it safe to remove all those files? And I don't really see anything here connected to temp/flash files so I'm not sure that'll fix my problem. Btw, whenever I try to play one of those videos in Movie Player, it says location not found- i think that's because i deleted some folder. but it still shows up and i can't get rid of it. it's really annoying me >:o

---

### Post by Casper35th on 2010-12-27
Yes it's safe to delete those cached items, Those cached items are temp items from installing software on your hdd

---

### Post by Casper35th on 2010-12-27
Out of curiosity when you removed your browsing data the drop down box next to "clear data from this period" Does it say "Everything"?

---

### Post by Ir0nMa1deN on 2010-12-27
yes i made sure it said everything. so it deleted all traces of the websites i went to as well as the cookies. i think the files are gone now since Movie player can't open them, now it's just a matter of cleaning up or "resetting" Movie Player so that it forgets recent items.

---

### Post by thenamelessone on 2010-12-27
install ubuntu tweak to solve the problem.

---

### Post by ubuntu27 on 2010-12-27
If what you want to do is to erase your traces or eliminate your history and cache, install [BleachBit]("http://bleachbit.sourceforge.net/")

It is in the repository.

---

### Post by mcduck on 2010-12-27
Just go to Places/Recent Documents/Clear Recent Documents. And of course use the similar function in your web browser. 

No need to install any additional software for such a trivial task. :)

Edit:
...and next time you want to do some private browsing, I recommend using the Guest Session, available from the shutdown applet. It will create a new temporary user which will get completely wiped out afterwards. Great when you want some extra privacy, or somebody else wants to use your computer.

---

### Post by Ir0nMa1deN on 2010-12-27
i'll try that guest session thanks. don't have my laptop with me right now so i guess i'll clear those recent documents later. thanks everyone for your help.

---

### Post by lovinglinux on 2010-12-28
The VLC standalone player is awesome, but the plugin is not.

To watch videos, remove vlc plugin and totem-plugin and install gecko-mediaplayer.

```
sudo apt-get remove mozilla-plugin-vlc
sudo apt-get remove totem-mozilla
sudo apt-get install gecko-mediaplayer
```

---

