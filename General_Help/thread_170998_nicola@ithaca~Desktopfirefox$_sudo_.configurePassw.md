---
title: "nicola@ithaca:~/Desktop/firefox$ sudo ./configure
Password:
./configure issue"
date: 2006-05-05
forum: General Help
---

### Post by ncappel1 on 2006-05-05
I am trying to install firefox 1.5.0.3 on a fresh install of breezy. 
I downloaded the file from the mozilla website, then I ran apt-get install build-essential. when I extract the .tar.gz into the desktop and run ./configure, i get the following.
```
nicola@ithaca:~/Desktop/firefox$./configure
bash: ./configure: No such file or directory

```

is there a step I am skipping over?

---

### Post by glotz on 2006-05-05
I'm a total Linux newbie, but I managed to install the new Firefox by following this [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

(Maybe you can't configure it because it's binary?)

---

### Post by ncappel1 on 2006-05-05
the guide worked well, but I still don't really understand what I was doing wrong. I'll have to try to understand the process a bit better.

---

### Post by towsonu2003 on 2006-05-05
[QUOTE=ncappel1]the guide worked well, but I still don't really understand what I was doing wrong. I'll have to try to understand the process a bit better.[/QUOTE]
when you download firefox.tar.gz from mozilla main page, it's a self-contained binary file (Portable Applications in Windows). so you unzip it and start using it. That is the reason behind the second section (Quick Dirty Firefox Installation) of the wiki page that a previous poster linked. 

the ./configure; make sequence is made for source code. that is to change the source code into a binary. once you change it to binary, you do either sudo make install or sudo make checkinstall, by which you basically copy the binary file and its friends to where ever it wants to go, than start using it.

---

### Post by ncappel1 on 2006-05-06
towsonu2003, I think I understand now, you mean that the program was ready to go and be run right when I extracted it to the folder? I guess the problem was that when I was running the "firefox" command, it was still being associated with the old version. That's what the guide was telling me to change! It is all starting to make sense. thank you!

---

### Post by towsonu2003 on 2006-05-06
[QUOTE=ncappel1]towsonu2003, I think I understand now, you mean that the program was ready to go and be run right when I extracted it to the folder? I guess the problem was that when I was running the "firefox" command, it was still being associated with the old version. That's what the guide was telling me to change! It is all starting to make sense. thank you![/QUOTE]
Yes, that's pretty much it :) you're most welcome. 

when you run command "firefox", it looks for the command under /usr/sbin and so on. so it launches firefox that came with ubuntu. to the contrary, when you do:
cd /home/username/firefox
./firefox
than it runs the "firefox" under /home/username/firefox. The ./ in the second line means "run firefox that is located right where I am now".

---

