---
title: "Can you do this in bash?"
date: 2011-07-23
forum: General Help
---

### Post by sectshun8 on 2011-07-23
Pondering today on how to expand a bash script I recently made... it lead me to this.

Can I:

1) Switch user to root and automatically enter in PW without being prompted

2) Login automatically using sftp as I can with ftp (because the -n option does not work)

3) Outside of the script, if logged in as root, why can I not assign an alias the same as a regular user?

Thanks in advance for anyone who can help.  If I can't end up doing these things no big deal.. just playing around, trying to make the shift go by quicker :D

On top of that... not looking to hear secuirty risks of using root in a script or any of that... nor comments about, Well why dont you use such and such to do that.  I want it bash if possible.

---

### Post by sectshun8 on 2011-07-23
The reason I need to be able to do these is this.

I'm on a Solaris machine and want to transfer soem files to my Red Hat machine.  The Red Hat machine has no ftp server, nor can I install one.  I can however sftp.  Well if I try and run the sftp command as my normal user it will not allow me to enter a user on the the remote machine and only prompts for a password.  If I switch to root on my local machine and sftp then it just asks for the root PW and I can get in... however I cannot set the alias in root on the local machine so it's easy for the other people on shift to run the script.

SO if I can either switch user to root automatically with no prompts in the script... OR login automatically via sftp as root... then this will work.  Otherwise, I'll just drop the idea.

---

### Post by sectshun8 on 2011-07-23
Okay... got eh script to do everything I want except the only downfall to full automation is I have to enter in a password when the sftp starts.  

If anyone knows how to get around that.. that'd be sweet.

---

### Post by fdrake on 2011-07-23
did you try with setuid?  write or own the script with root user, then make it excutable to everyone and then set the uid to the script so it will have the same permissions as root even if is not lunched by root.

ps:you have to read the man setuid cannot remember exactly the options.

---

### Post by fdrake on 2011-07-23
this link is what ur lookifn 4:
[http://www.cyberciti.biz/faq/unix-bsd-linux-setuid-file/](http://www.cyberciti.biz/faq/unix-bsd-linux-setuid-file/)

---

