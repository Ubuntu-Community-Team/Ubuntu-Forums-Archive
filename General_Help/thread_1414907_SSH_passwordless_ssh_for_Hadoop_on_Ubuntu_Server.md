---
title: "SSH passwordless ssh for Hadoop on Ubuntu Server"
date: 2010-02-24
forum: General Help
---

### Post by JesperUtoft on 2010-02-24
Hello.

Sorry if i have posted the wrong place.

I have for a while been trying to setup ssh so hadoop can ssh without a password to all it's nodes. (Currenly 2 nodes)
But i can not get the ssh to login without either asking for a password or just getting access denied (public key)

I have been following two guides
First:
[Setting up SingleNode Cluster]("http://www.michael-noll.com/wiki/Running_Hadoop_On_Ubuntu_Linux_(Single-Node_Cluster)")
Then after:
[Setting up Multinode Cluster]("http://www.michael-noll.com/wiki/Running_Hadoop_On_Ubuntu_Linux_(Multi-Node_Cluster)")

I have also done various ssh tutorials on setting up ssh.

I got to the point where i do the command bin/start-dfs.sh

Then it begins asking for passwords. Which it should'nt.

The problem is that ssh is not setup correcly.
And whatever i try i get problems with logging in.

the computers are called.

hadoop1.utoft.be (Namenode and JobTracker)
hadoop2.utoft.be
hadoop3.utoft.be
hadoop4.utoft.be (Will be added to the cluster later)

Can anyone help me with this issue.

Thanks Jesper

---

### Post by JesperUtoft on 2010-02-24
In short i can not make passwordless ssh work.

---

### Post by JesperUtoft on 2010-02-24
Hello.
After some more reading i found this command which i of cause make's sense after i used it...

ssh-copy-id -i ~/.ssh/id_rsa.pub username@mystery

I found it here:
[http://www.debian-administration.org/articles/152](http://www.debian-administration.org/articles/152)

Sorry for the "spamming"

Cheers Jesper

---

