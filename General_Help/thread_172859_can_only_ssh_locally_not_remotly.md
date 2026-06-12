---
title: "can only ssh locally not remotly"
date: 2006-05-09
forum: General Help
---

### Post by kyoji on 2006-05-09
Hello, here is my problem.

I just installed openSSH server on one of my kubuntu boxes.  When I try to ssh(openSSH) in to it remotely from the lan or out side the lan, it will just time out. If I try to ssh locally on that same box It works perfectly:confused:  I am able to ping it just fine from any  comp on the lan. 

All the config files are default to the install. The public key for the box I am trying to log in with is in  /home/*/.ssh/authorized_keys.  Seems like its blocking remote traffic to that port. I don’t have a firewall up that I know about. I have a sshd server on my laptop that works great and I tried to copy the config from that to this install and its still doing the same thing. 

Does anyone have any ideas what is going on?

---

### Post by cgjones on 2006-05-09
You need to have the local public key in the remote authorized_keys file.

---

### Post by Packard on 2006-05-09
Hello,

did you check the logs (/var/log/auth.log) after an attempt that doesn't work? You could also try to use the ssh option -v when logging in - then there will be more output and maybe it becomes clear what's going wrong.

Stupid question: are the user names on the two machines the same? If not, did you specify one when you try to log in?  That regularly happens to me, I have different login names on differnet PCs and sometimes forget to chose the right one.

---

### Post by kyoji on 2006-05-09
HI, 

I thought you had to have the public key of the remote host in the server authorized_keys file. I will give that a shot :D 

I have tryed the -v option, it will hang at connect to **** host then time out, with out giving to much info to what is rong, just looks like its never getting the packets to the server. I do have 2 diffrent host names! but the odd thing is that i can ssh in to my laptop server with out giving the diffrent user name. 

Thanx for the ideas. i will try them out when i get home!

---

