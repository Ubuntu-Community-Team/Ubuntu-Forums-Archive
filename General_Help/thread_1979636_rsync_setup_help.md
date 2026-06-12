---
title: "rsync setup help"
date: 2012-05-13
forum: General Help
---

### Post by bakegoodz on 2012-05-13
I'll give you a little background for my setup. I have a little Ubuntu server system that I got permission from my work to do nightly offsite backups to, from my house at night. (Nice fast connections with same ISP) Of course I do a manual copy first with the system directly connected.

They are not going to do anything special for me like port forwarding, so the Backup server is behind NAT (Network Address Translation, 192.168.x.x rather than a public IP)
  This is the setup I decided was to have: the server behind NAT will do a Rsync pull transfer from my home computer back to the server and have it setup as a cron job at night. 

So, the questions about this setup is:
 Does Rsync use encryption by default now? (I remembered as such) How would I port forward Rsync using encryption at my house, is it port 873 or 22? How would I write the syntax to have the remote backup server initiate the sync? Bonus: Were is a good guide for writing cron jobs?

Thank You

---

### Post by rai4shu2 on 2012-05-13
I think if I were attempting something like that I'd try to SSH from the work server to home, then script up something that does rsync via SSH.

see: [https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

---

### Post by agillator on 2012-05-13
Unless it has been configured otherwise, rsync uses ssh for remote connections (see the man page for details). 

As you describe things, you are probably correct in running a cron job on the server at work. That job can either pull from your home server and put the backup on the office server, or vice versa. That will require you to set up ssh on both machines so user intervention with passwords is not required. The one problem you may have, though, is the ip address of your home server. I assume you either have a static ip from your ISP or you are using a dynamic dns service. If not, you will probably need one or the other.

---

### Post by bakegoodz on 2012-05-14
I found a guide online that uses this as an example for pushing
rsync -avzH -e ssh --progress user1@remotehost:/SOURCEDIR/ /DESTDIR

([http://www.lamolabs.org/blog/1766/pushing-pulling-files-around-using-tar-ssh-scp-rsync/](http://www.lamolabs.org/blog/1766/pushing-pulling-files-around-using-tar-ssh-scp-rsync/))

Do I still need the user part if I setup ssh keys?

I would forward port 22, right?

Still need to find a guide for cron and ssh key setup.

---

### Post by jacob.david on 2012-05-15
Yes, you will still need to setup the ssh keys. As mentioned by agillator above rsync by default uses ssh so you don't need -e ssh ( I don't even see this ssh as a valid value for -e in the man pages).
As for setting up ssh keys refer to [http://jacks-tech-ref.blogspot.com/2011/08/secure-remote-connection-without.html](http://jacks-tech-ref.blogspot.com/2011/08/secure-remote-connection-without.html).
Setting up cron should be very simple and refer to the manual pages.

---

