---
title: "Terminal size when started"
date: 2010-05-04
forum: General Help
---

### Post by Smart Viking on 2010-05-04
Hi all, is there any way i can make the terminal have a different resolution when i start it, so i don't have to resize it all the time?

And also, can I make a simple script, that launches the terminal in a certain directory?

:popcorn:

---

### Post by inameiname on 2010-05-04
As for your first question, easy...just open terminal, go to Edit > Profile Preferences and change Default Size.

---

### Post by Smart Viking on 2010-05-04
> **inameiname said:**
> As for your first question, easy...just open terminal, go to Edit > Profile Preferences and change Default Size.

I don't have that option. :)

---

### Post by inameiname on 2010-05-04
Are you using the default gnome terminal? If so, that's weird.

---

### Post by Smart Viking on 2010-05-04
> **inameiname said:**
> Are you using the default gnome terminal? If so, that's weird.

Yes I'm using gnome-terminal. And running 9.10. :)

---

### Post by inameiname on 2010-05-04
Oh I'm sorry, I forgot to ask about the version. I'm on Lucid, so perhaps they implemented that for it in the latest release.

I found a link to someone with a similar issue:

[http://ubuntuforums.org/showthread.php?t=465670](http://ubuntuforums.org/showthread.php?t=465670)

---

### Post by anaconda on 2010-05-04
You can edit your gnome-terminal launcher. Just put eg: this on the  launch "Command:" Or you can make your own launcher..

```
gnome-terminal --geometry 120x50 --working-directory=/home/anaconda/Desktop/
```

--geometry sets the geometry in characters. window size will be 120x50 characters

to try different settings, you can try different commands on terminal...

---

### Post by Smart Viking on 2010-05-04
> **anaconda said:**
> You can edit your gnome-terminal launcher. Just put eg: this on the  launch "Command:" Or you can make your own launcher..

```
gnome-terminal --geometry 120x50 --working-directory=/home/anaconda/Desktop/
```--geometry sets the geometry in characters. window size will be 120x50 characters

to try different settings, you can try different commands on terminal...

Thank you, i will replace my terminal shortcut with this command. :)

EDIT: It worked perfectly, gnome-terminal --geometry 80x40 --working-directory=/home/anaconda/Desktop/ was just as i wanted it :)

EDIT2: Oh not quite, anakonda = SmartViking... xD

---

### Post by inameiname on 2010-05-04
Thanks Anaconda. I know this isn't my posting, but I was curious about his last question myself and couldn't figure it out. Awesome.

---

