---
title: "Web site videos"
date: 2009-12-19
forum: General Help
---

### Post by waltwin on 2009-12-19
[SIZE=2]I am using ubuntu 9.04. I have noticed that recently, I cannot play videos on various websites and Youtube. I know that the videos work as I have tried them on my only remaining Windows machine. I have also noticed that my ubuntu machine has slowed down significantly. I keep my updates current. Any ideas will be appreciated[/SIZE].

[SIZE=2]waltwin[/SIZE]

---

### Post by Puck7 on 2009-12-19
In which browser did you try to play the flash contents. I say flash content, because you say that you can't play the youtube videos.
What version of flash are you running?

Try installing flashplugin-nonfree
```
sudo apt-get install flashplugin-nonfree
```

After this you can try in firefox to watch the videos on youtube, if you installed it while Firefox was running, you may want to restart it.

---

### Post by waltwin on 2009-12-19
I am using Firefox as my browser. I did as you suggested and it has allowed me now to open the majority of Youtube videos. No luck with specific websites. Thank you for the help

waltwin

---

### Post by Puck7 on 2009-12-19
Which are the other websites? Are they all using flash to display the videos or other formats?

---

### Post by waltwin on 2009-12-19
The other website is Americas Test Kitchen. I am not sure if it is a Flash video. I am not sure how to tell. As a web browser I also use opera. I did a cold start on my machine and tried the same site using Opera and it worked fine. No joy with Firefox.

---

### Post by Puck7 on 2009-12-19
If we're talking about [this]("http://www.americastestkitchentv.com/cookstv/preview/default.asp?req=1&station=mainChannel&video=s8/stuffedroastbeeftenderloin") then it's flash. Weird that it doesn't work in Firefox. Which version of Firefox are you running on what Ubuntu version?

---

### Post by waltwin on 2009-12-19
Sorry to be so long in answering but I was trying to determine what version of Firefox I am using. I just upgraded to version 3.5.6. Still no joy on the flash video which you identified. I am using ubuntu 9.04. I tried to install 9.10 but it slowed my machine down very badly.

---

### Post by Puck7 on 2009-12-19
I really have no clue what the issue could be here. I'm also on 9.04, with Firefox 3.0.16 and the latest flash from the repo's. I hope someone can stumble upon your post and help you further than this.

---

### Post by serpantman on 2009-12-19
> **waltwin said:**
> [SIZE=2]I am using ubuntu 9.04. I have noticed that recently, I cannot play videos on various websites and Youtube. I know that the videos work as I have tried them on my only remaining Windows machine. I have also noticed that my ubuntu machine has slowed down significantly. I keep my updates current. Any ideas will be appreciated[/SIZE].

[SIZE=2]waltwin[/SIZE]

Who needs to watch flash videos?

Install flash plugin to this dir

/usr/lib/firefox/plugins

should work for other plugins too in the future. Enjoy!

EDIT: by install i meant just copy it to that dir, not when firefox is running though, that sometimes messes it right up

---

### Post by waltwin on 2009-12-20
I just can't figure out how to install the information into a directory. How do I find the directory?

---

### Post by Puck7 on 2009-12-21
You can open nautilus as root, press F2 and type
> gksudo nautilus
you can navigate to the desired folder. Please be cautious you can damage your system if you move or delete something you shouldn't.

---

