---
title: "rsync through a ssh secure tunnel?"
date: 2012-08-24
forum: General Help
---

### Post by held7over on 2012-08-24
A friend of mine helped me set up a ssh secure tunnel between my local machine and a remote machine. This ssh tunnel links my local port 9273 to the remote machine's port 9273. So, to get in, I simply type on the command line on my local machine:

ssh -p 9273 IP_Address

I have been trying to get rsync to use this same secure tunnel set up. Below is my crude attempt to construct a rsync statement which transfers the contents of directory dir-a from my local machine to directory dir-b on the remote machine. (Hopefully, it would do this recursively.) 

$ rsync -avz ssh -p 9273 /home/user_name/dir-a/ other_user_name@IP_Address:/home/other_user_name/dir-b/

But this, and other versions I have tried, gives me the following error--

ssh: connect to host IP_Address(this is the remote machines IP) port 22: 
No route to host
rsync: connection unexpectedly closed (0 bytes received so far) [sender]

It seems to me, that I need it to use port 9273 on both machines. 

What am I doing wrong? 

Thanks for your help and thoughts on this! :D

---

### Post by held7over on 2012-08-24
Hey! I have it working!!! 

My statement may not be pretty, but it seems to work! Hopefully the secure shell tunnel thing is still being used! I also had to change some of my file names that used double "-" because they were converting into long hyphens on the command line for some reason.

$ rsync -avzh --progress --inplace -e 'ssh -p 9273' --rsh='ssh -p 9273' /home/user_name/dir-a/ other_user_name@IP_Address:/home/other_user_name/dir-b/

---

### Post by papibe on 2012-08-24
Hi held7over.

Glad you found it out.

BTW, the option '-e' and '-rsh' are the same, so one would suffice.

Regards.

---

### Post by held7over on 2012-08-24
Thanks papibe. Good to know they both accomplish the same thing!

I guess I am kind of confused concerning how to give the port numbers being used by the local and remote machines in the statement....

Are you saying that using a single -e 'ssh -p 9273' expression in the statement would have caused the tunnel to go from port 9273 of the local machine to the port 9273 of the remote machine?

How would the statement have been constructed, if I needed to go from port 8000 on the local to port 9000 on the remote???

Thanks! :D

---

### Post by papibe on 2012-08-24
> **held7over said:**
> I guess I am kind of confused concerning how to give the port numbers being used by the local and remote machines in the statement....
You can't actually map ports with rsync. You use what is already set.

> **held7over said:**
> 
Are you saying that using a single -e 'ssh -p 9273' expression in the statement would have caused the tunnel to go from port 9273 of the local machine to the port 9273 of the remote machine?
No. May be it will be clear with the next example.

> **held7over said:**
> 
How would the statement have been constructed, if I needed to go from port 8000 on the local to port 9000 on the remote???
First, you create a tunnel using ssh:
```
ssh -L 8000:remotehost:9000 user@remotehost
```
That is actually create the port 8000 on localhost, which is mapped to remotehost's port 9000.

Then, if you want to use that tunnel with rsync:
```
rsync -av -e "ssh -p8000"  source/  user@localhost:destination
```
Note that 'user' would have to be a valid user on 'remotehost'.

Does that helps?
Regards.

---

### Post by held7over on 2012-08-26
That explains a lot! I get it now what my linux friend did, when he set things up. Thanks!

---

