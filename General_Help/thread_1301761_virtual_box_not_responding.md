---
title: "virtual box not responding"
date: 2009-10-26
forum: General Help
---

### Post by yanvolking on 2009-10-26
Hello Community,

Suddenly, after week working without a hitch, I could no longer get virutal box to run.  I clicked on APPLICATIONS->SYSTEMS TOOLS->VIRTUAL BOX, but the application would not start.  I uninstalled the whole package (complete removal) and then re-installed it.  But during the installation process I got a message saying :

"A copy of VirtualBox is currently running.  Please close it and try again. Please note that it can take up to ten seconds for VirtualBox (in particular the VBoxSVC daemon) to finish running."

How can something that's been completely removed be running?  What can I do?

Thanks

---

### Post by blur xc on 2009-10-26
I'm not an expert, but maybe try ```
ps -aux | grep virtualbox
``` to see if there's anything running.  I'm sure others could be better help.  Did you try to reboot?  I don't know if zombie processes can exist after removing a program or not and rebooting is the only way that I know to kill a zombie process.  Other than that, give the VBox forums a try, those guys can be quick to answer, but they can also be a bit rude.  I think they get tired of answering the same newb questions regarding stickied topics over and over again.  Do a search and read the FAQ's and sticky's if you can before posting.

Good luck.  
BM

---

### Post by yanvolking on 2009-10-27
Hi and thanks for your reply.  I ran the command you suggested but there seemed to be no trace of vbox on my machine.  

I reinstalled vbox using the command lines suggested on : 

  	 	 	 	 	 	  [http://www.marlonj.com/blog/2009/04/instalacion-virtualbox-220-en-ubuntu-904/comment-page-1/](http://www.marlonj.com/blog/2009/04/instalacion-virtualbox-220-en-ubuntu-904/comment-page-1/)


[URL="http://www.marlonj.com/blog/2009/04/instalacion-virtualbox-220-en-ubuntu-904/comment-page-1/"][COLOR=Black](sorry, it's in Sapnish)[/COLOR]
[/URL]
 
and it worked.  However, at a certain stage in the installation process, a message popped up saying something about something already exisiting on the kernel and asked if I wanted to overwrite it or create a new one.  I chose to create a new one.  When the installation process was over, I rebooted and virtual box worked.

From this experience I can say that there are many virtualbox installations available including ones on synaptic.  The one listed above is the only one I've found to date which works on my machine.

---

### Post by darkksyde on 2009-10-27
Have you tried deleting the .VirtualBox folder in your home folder?

---

