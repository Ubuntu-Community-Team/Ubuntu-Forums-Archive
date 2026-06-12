---
title: "How can CTRL+key combos be executed from script?"
date: 2009-12-15
forum: General Help
---

### Post by YosefKaro on 2009-12-15
Since this is General Help, I guess that I can ask my question here.  I am trying to write up a small script, a function, but I am getting stuck where I normally would use CTRL+Z to pause a process.  From what I found on the web, it appears that I could use KILL -STOP and KILL -CONT but then I would have to know the exact number of the process.  (I have also tried using & at the end of the last command but that doesn't work.)  Let me explain.

I use a broadband dongle that can't be used with network-manager (yet).  This dongle has a storage device so when I first plug it in, ubuntu doesn't 'see' it as a modem but as a USB storage device.  So the first thing that I have to do is 'eject' this and then ubuntu 'sees' my modem.  After this, I use wvdial to connect to the internet but then I have to keep the terminal open to stay connected to the internet because the process is running in the foreground. (here I have tried sudo wvdial nova & but it doesn't work.)  So I have to use CTRL+Z to pause the process and then bg to put the process in the background.  Then I don't have to leave the terminal dedicated to this process.

As you can see, that is a lot to do just to get on the internet each time.  So I am trying to write up a function to do it all in one swoop but I am getting stuck where I would normally type CTRL+Z.  Any ideas?

-Yos

---

### Post by YosefKaro on 2009-12-16
Ah, this almost does exactly what I am looking for but it is a bit slow:

> function connect {
	sudo eject /dev/scd1
	sleep 5
	sudo wvdial nova
	sudo kill -stop `pidof wvdial`
	sleep 5
	sudo kill -cont `pidof wvdial`
}

---

