---
title: "Run (compute) remotely installed software locally"
date: 2012-10-12
forum: General Help
---

### Post by ObeyTheDiode on 2012-10-12
I am using simulation software that is hosted on a server at work. I SSH from my machine to the server and run the software on the server.

I have seen that it is possible to run this software locally (i.e. the computations are done on my machine) but I have no idea how to set it up that way. I do suspect I have to mount the software's directory somehow and set environmental variables (maybe) so that when I launch the software locally it goes looking for it in the remote one. Essentially, I need the remote directory to behave as a local one without manually doing SSH.

My home directory on the server gets mounted in my Ubuntu; the software is installed on a directory to which I have read-only access.

What I do:
1) localuser@local_machine: ssh server_username@the_server
2) server_username@the_server: the_program
-> Program runs on the_server and the display is tunnelled to me.

What I want to do:
1) localuser@local_machine: the_program
-> Program runs locally.

---

### Post by cool110 on 2012-10-12
Are are you mounting your server home directory with NFS or SFTP?

---

