---
title: "Skype Doesn't work!!!!!!!!!!!!"
date: 2006-02-12
forum: General Help
---

### Post by bratanche on 2006-02-12
Hi
I just install ubuntu and i am trying to install skype. When i install it from Terminal, I can see the start icon from Applications -> internet-> Skype but it doesn't starts at all. I red and did allmost everything that one could find in internet but it still doesn't works ! I also tried to start "add application" but it doesn't work too.The programmes just doesn't starts. PLEASE HELP i dont know what is going on

---

### Post by Xappe on 2006-02-12
you'll need libqt3-mt for skype to work. fire up a terminal and write:
```

$ sudo apt-get install libqt3-mt
```

---

### Post by bratanche on 2006-02-12
Shall i restart or...... I have no idea. I did as you said (as root of course) than tried to start skype again. Did not work again.  I tried first from Applications, then i tried something i red i few hours ago than i start terminal and just wright skype than i got this messege:
user@12.13.186:~$ skype
skype: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

what that means? That i haven't install Skype properly? i have no idea :confused:  
P.S. Sorry but i am complite Linux n00b! :)

---

### Post by Xappe on 2006-02-12
what skype package do you use?

---

### Post by kaamos on 2006-02-12
[QUOTE=bratanche]user@12.13.186:~$ skype
skype: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory[/QUOTE]
Hello!

Try this
```
sudo apt-get install libstdc++5
```

---

### Post by paulmilliken on 2006-02-12
Bratanche,
Did you follow the instructions on this link: [https://wiki.ubuntu.com/SkypeHowto?highlight=%28skype%29](https://wiki.ubuntu.com/SkypeHowto?highlight=%28skype%29) ?
Also, please advise what version of skype you tried.
Paul

---

### Post by Red Knuckles on 2006-02-12
Use Automatix: [http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563) 
_***OR***_ this how to:
[https://wiki.ubuntu.com/SkypeHowto?highlight=%28skype%29](https://wiki.ubuntu.com/SkypeHowto?highlight=%28skype%29)
and you should be able to get Skype up and running. I've done both and they both worked for me. Automatix is amazing, every distro should have something similar but they don't.:D

---

### Post by ivanhelguera on 2006-02-12
Hi, 
can anyone elnighten me as to why is there no official ubuntu skype package, while, say, acrobat is available? 
By the way - once you have your skype up and running, there's a bug about closing the microphone resulting in 'audio setup error' message from skype. check out this, could be helpful: 
[http://www.skype.com/help/guides/soundsetup_linux.html]("http://www.skype.com/help/guides/soundsetup_linux.html")
Best, 
IH

---

### Post by bratanche on 2006-02-13
THX now it works :P:P:P:P With Sudu apt-get install .... I used the Ubuntu unofical start  guide on the wiki. THX very much \\:D/

---

