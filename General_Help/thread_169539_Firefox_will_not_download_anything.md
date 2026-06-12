---
title: "Firefox will not download anything"
date: 2006-05-02
forum: General Help
---

### Post by digsby on 2006-05-02
I just installed a fresh copy of Ubuntu with the 2.6.8 kernerl. And Firefox will not download anything. The first thing I did was try to install an extenstion with firefox. Did nothing. Then i tried to download an mp3 from a website, never saw the download progress screen, and the song wasnt in the folder i specified to download it to.

Any thoughts?
digsby

---

### Post by towsonu2003 on 2006-05-02
try to launch it from the terminal and watch if it outputs any errors (from terminal, type firefox). 

try wget to see if downloading actually work. I found that google download wasn't working in my system not firefox via wget. the relevant command will be:
wget -c -t 0 [http://blablabla](http://blablabla)

-c means continue (will continue if interrupted)
-t 0 means try infinite times
[http://bla](http://bla) is the link to the file itself. 

it will download the file to whereever you run the command. for example:
cd ~/Desktop
wget -c -t 0 [http://blablabla](http://blablabla)
will download it to your Desktop. 

You can also check if the ownerships are correct. I usually do a quick
chown -R username:username ~/.mozilla
to make sure I have the ownerships.

---

### Post by digsby on 2006-05-02
The permissions look right for the user, drwx------
I used wget to download a version of the DVD instsall package. (ran out of blank cdrs and only have dvds) But the DVD iso wont finish downloading, and gives an error about calculating something and says "file >= o bits"

So next i tried lynx to get the new version. but it crashed at 99%. 

The wierd thing is, ive installed this version of ubuntu with the same cd on the same pc before, and its been flawless.

digsby

---

### Post by digsby on 2006-05-02
oh and running firefox in the terminal gave no errors

---

### Post by towsonu2003 on 2006-05-02
[QUOTE=digsby]But the DVD iso wont finish downloading, and gives an error about calculating something and says "file >= o bits"

So next i tried lynx to get the new version. but it crashed at 99%. 
[/QUOTE]
you tried both with wget right? can you copy-paste outputs? 

also, try downloading a file with epiphany:
```
sudo apt-get install epiphany-browser
```
just to see if this is systemwide or local to firefox.

---

### Post by towsonu2003 on 2006-05-02
oh, and, try doing them after a system update
```

sudo apt-get update
sudo apt-get upgrade

```

---

