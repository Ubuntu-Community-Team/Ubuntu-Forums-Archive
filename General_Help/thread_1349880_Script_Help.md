---
title: "Script Help"
date: 2009-12-08
forum: General Help
---

### Post by Hunter2379 on 2009-12-08
I've recently started learning about scripts. I learned a bit about batch but I'm faced with a  few problems.
1) Don't have any ideas on what to do. Any help?
2) how do i start a new shell with bash. In XP i would type in Start echo <whatever> and it would print it out. How can i do this in bash?
Any help is appreciated.

---

### Post by andrew.46 on 2009-12-08
Hi Hunter2379,

Can I ask what you are trying to accomplish with this script? 

Andrew

---

### Post by whitethorn on 2009-12-08
1) Just google "bash introduction" and you'll get a ton of webpages which will help you on your way. 

2) i) Start an editor either in the terminal or with it's own gui.  

```
gedit helloworld
```

then add the following lines

> 
#!/bin/bash
echo "Hello World!"

Save it.  Open the terminal and cd to the folder you saved your file in.  

```
cd /home/youusername/...
```

you can check if the file is in there with ls (ls = dir in windows)
Next you need to add the execute permission.  

```
chmod +x newscript
```

then you need to run the file.  The ./X before the X mean run the program in this folder called X.

```
./helloworld
```

Once you get the hand of bash scripting then it'l a lot of fun.  I've written a ton of them to start programs with some special values or some to help me download and convert youtube videos.

---

### Post by Hunter2379 on 2009-12-08
I'm trying to get the shell to install different things. 
Like run script>opens multiple shells that install multiple things. 
These things are like wireshark,nmap,aircrack,and ettercap, I'm going to use it for different drivers too. Basically to make things easier for me. Plus i got a few friends to switch from windows to linux ;). This'll help em out hopefully.

---

### Post by Hunter2379 on 2009-12-08
> **whitethorn said:**
> 1) Just google "bash introduction" and you'll get a ton of webpages which will help you on your way. 

2) i) Start an editor either in the terminal or with it's own gui.  

```
gedit helloworld
```then add the following lines


Save it.  Open the terminal and cd to the folder you saved your file in.  

```
cd /home/youusername/...
```you can check if the file is in there with ls (ls = dir in windows)
Next you need to add the execute permission.  

```
chmod +x newscript
```then you need to run the file.  The ./X before the X mean run the program in this folder called X.

```
./helloworld
```Once you get the hand of bash scripting then it'l a lot of fun.  I've written a ton of them to start programs with some special values or some to help me download and convert youtube videos.

Thanks for the reply. I already know this, what im looking for is to make the script open another shell, and to have this new shell run commands from the script.

---

### Post by whitethorn on 2009-12-08
You weren't very clear in your first post.  But here you go

This is how I usually do it.  You have to be careful about installing multiple things at once though I'm pretty sure it's not possible. The new shell is then xterm, -e run following command, top = command to run.

```
xterm -e top
```

also works with gnome-terminal -x command

---

### Post by Hunter2379 on 2009-12-08
> **whitethorn said:**
> You weren't very clear in your first post.  But here you go

This is how I usually do it.  You have to be careful about installing multiple things at once though I'm pretty sure it's not possible. The new shell is then xterm, -e run following command, top = command to run.

```
xterm -e top
```also works with gnome-terminal -x command
Thank you

---

### Post by Hunter2379 on 2009-12-09
xterm doesn't let the original script keep running unless you finish the newly opened one. Anyone know a fix for it, and is there a way to run multiple commands rather than just one with xterm?

---

### Post by Hunter2379 on 2009-12-09
And is there also a timer i can set incase the command is running too long the timer will shut it down?

---

### Post by Hunter2379 on 2009-12-09
...

---

