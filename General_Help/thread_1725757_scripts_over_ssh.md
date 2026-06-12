---
title: "scripts over ssh"
date: 2011-04-10
forum: General Help
---

### Post by emosms on 2011-04-10
Hi,
The case is:
-Local machine running XP
-Remote machine running ubuntu server, headless
-I want to run some scripts stored on the local machine
-Generally, I would preffer to click_on .bat files to execute some procedure on the remote server. The .bat file calls .sh or python scripts, all stored on the local machine

-Dont know where to start from and if it is possible at all.
-First open ssh connection supply it with an argument another script?
-The major point is, i DO NOT want to upload anything unnecessary on the server, storing and working on the scripts ENTIRELY on my local machine
-The task further complicated to logon to a database instance on the remote server and sending scripts from the local machine on the remote.
-Appreciate if u give me some clue

Best Regards

---

### Post by Ranko Kohime on 2011-04-10
I'm going to tentatively say not possible.  Generally a shell script has to run on the machine on which it's going to do the work, although it can be called via SSH.  I could be wrong, and it could be possible, though.

Though, wouldn't it be easier just to build the scripts into a menu which could be accessed via SSH?

---

### Post by emosms on 2011-04-10
Ok thxs
But if I state it that way - to send commands as strings over ssh, not typing them? 
Maybe if a xp .bat script establishes connection to remote via ssh and sends text strings instead of typing commands?
Even if it is required an extra script to read the script files residing on the local machine and send them as text string commands over ssh?

The point is that I do not feel comfortable to edit and test the scripts usig VI, and the purpose of the linux box is purely to serve as a server, dont wanna turn it into desktop

Finally , what about a folder syncronization between the local and remote machine? Any thread?
(in case I keep a local copy of the scripts for editing and synchronize with the remote before execution)
 
Best Regards

P.S.

Just found smth. seems that it works and it is really easy as I hoped. Using putty and plink
-in a .bat file:
> plink user@remoteIP -pw pass -m local_script.sh
pause

-then put some commands in local_script, it executes on the remote and shows output within the xp cmd at double-click

Now I will try it with the python scripts, hope it works

---

### Post by iponeverything on 2011-04-10
you might look at "expect" - it allows you to interact with the remote machine via a local script.

---

