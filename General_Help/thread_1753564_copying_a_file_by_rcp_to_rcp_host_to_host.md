---
title: "copying a file by rcp to rcp host to host"
date: 2011-05-09
forum: General Help
---

### Post by powpow45 on 2011-05-09
:confused:

Hi Guys, 
I am a bit of a n00b when it come to linux but I am setting up a test environment were I have a appliance monitoring network traffic. Part of my test requires me to copy a file via RCP from one host to another host.

I have two ubuntu boxes. 
I have allowed the subnet in the \etc\host.allow for ALL.
I have installed rsh-server

When I try to copy the file it looks like it tried to use SCP instad of RCP because it connects to 22 instead of 544. Also note that traffic must be unecrypted thus me trying to use 

Is there anyway to make ubuntu go old school to allow me to use rcp instead?

```

testuser1@ubuntu:~$ rcp /home/testuser1/test.txt testuser1@10.46.41.38:/home/testuser1
ssh: connect to host 10.46.41.38 port 22: Connection refused
lost connection
testuser1@ubuntu:~$ rcp
usage: scp [-12346BCpqrv] [-c cipher] [-F ssh_config] [-i identity_file]
           [-l limit] [-o ssh_option] [-P port] [-S program]
           [[user@]host1:]file1 ... [[user@]host2:]file2
testuser1@ubuntu:~$ 

```Thanks in advance.

---

### Post by gmargo on 2011-05-09
Install the **rsh-client** package, and then **rcp(1)** will point to the traditional "old-school" rcp instead of scp.

---

### Post by powpow45 on 2011-05-10
thanks gmargo this is a big help. 

Only problem now is I keep getting permission denied.

Both sides have an acccount called testuser1 with the same password. 

When I try to copy I get this error

testuser1@ubuntu:~$ rcp test.txt [email]testuser1@10.46.41.38:test.txt[/email]
Permission denied.

I checked the hosts.allow file and it says
ALL: 10.46.41.0/24 : allow

---

### Post by gmargo on 2011-05-10
To enable password-less access, you need to configure the destination machine, either through a **$HOME/.rhosts** file or through a **/etc/hosts.equiv** file.

See man pages: **rhosts( 5 )** and **hosts.equiv( 5 )**.

---

