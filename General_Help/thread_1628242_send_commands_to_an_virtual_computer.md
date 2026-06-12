---
title: "send commands to an virtual computer"
date: 2010-11-22
forum: General Help
---

### Post by sandermans16 on 2010-11-22
Hello all, 

I want to make a virtual computer with virtualbox running ubuntu. 
But I want a command that I can send FROM my normal computer (the one who runs the virtual machine) TO the virtual computer.

And I want this done by the console, but if through a program that is not a disaster. as long as you can't see anything showing up on the virtual computer.

So this is what I want: I have the virtual machine wich is running ubuntu and installed smplayer and I want a command from my computer that is running the virtual machine to send the virtual this command: smplayer --send-action pause or smplayer --send-action play.

SO  I JUST WANT TO SEND MY MULTIPLE VIRTUAL COMPUTERS A COMMAND SO THEY WILL PLAY A MOVIE ALL AT THE SAME TIME

I have seen you can set a listening port so you can send commands to smplayer but I do not know how I can connect the virtual machine and then can type the commands 

please help me as  fast as you can 

Sincerely, 

sandermans16

sorry if i have bad english

---

### Post by lukeiamyourfather on 2010-11-22
See the manual for VirtualBox for the networking configuration. 

[http://www.virtualbox.org/manual/ch06.html#natforward](http://www.virtualbox.org/manual/ch06.html#natforward)

---

