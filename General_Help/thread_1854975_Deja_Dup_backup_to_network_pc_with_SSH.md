---
title: "Deja Dup backup to network pc with SSH"
date: 2011-10-05
forum: General Help
---

### Post by Benchrest on 2011-10-05
I use SSH , have it installed client and server on both my machines on my home network. I use it for both manual and Unison backup.
I have installed Deja Dup for a more automated back up. attempting to setup a simple backup from one machine to backup to the other a small folder for test, but every time I run it I get a message "backup failed" "ssh program unexpectedly exited"
The only required parameter is the address of the other machine. I have tried adding the optional data such as folder name where to store and it fails too.  I can find no examples of how to set up SSH to another machine for Deja Dup on a local network but it doesn't really look that difficult. 

I

---

### Post by Benchrest on 2011-10-05
So I'm senile, don't remind me. I had my other machine as 192.168.0.101 and it should have been 192.168.1.101  
I then had another problem with a message that "Backup failed Permission denied" 
This was because I had the path wrong. The error message is not very clear.  There are no examples to follow so it was try this and try that.  Defining:
Backup location - SSH
Server - 192.168.1.101
Folder - /home/usernameofserver/backuptofilename

Worked

---

