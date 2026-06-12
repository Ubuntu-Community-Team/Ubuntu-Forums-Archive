---
title: "ssh file transfer"
date: 2010-09-03
forum: General Help
---

### Post by terry f on 2010-09-03
I just started at a new university.  I have access to some linux servers.  I ssh into a public server and then ssh from that session into a private server. I have some work on the server that I need to download to send in for grading.  Can anyone tell me how to transfer the files off the server to my computer?

---

### Post by nothingspecial on 2010-09-03
```
scp -rv /path/to/your/work user@ipaddress:where/you/want/to/put/it
```

---

### Post by terry f on 2010-09-03
That works, but its kinda extensive.  I have to copy files from the linux server to the public server and then to my computer.  Is there are way to do it all in one shot?  I dont know if I was clear earlier.  There is a public server (schoolsName.edu) that I can ssh into from home.  Then, from that ssh session I ssh into a second server.  Is there a way to do it in one line?

---

