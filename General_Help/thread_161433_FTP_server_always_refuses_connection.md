---
title: "FTP server always refuses connection"
date: 2006-04-17
forum: General Help
---

### Post by northjerry on 2006-04-17
Hello Everyone, and thanks in advance for any hints on this.
Both WU-ftpd and now Pro-ftpd have been installed in my Ubuntu 5.10, but both have given me the same error:

root@terabyte:/etc# ftp 192.168.0.100
ftp: connect: Connection refused

I also tried from a Windows client, same problem. So I have tried everything I've seem in forums, like changing inetd.conf, checking that the hosts.deny does not have an entry for the ftp, and that the hosts.allow does, etc.

My router didn't have a problem when I had the ftp server on Win2k, but I still created allow rules on the firewall of the router for ports 20 and 21, just in case.

So far no luck, and in any of the "learn Linux" books looks like a very easy process. So I wasted my weekend on "exercise no.1" with a ver frustrating experience, please help me if you have a chance :S

Jerry.

---

### Post by Trajan on 2006-04-17
have you tried ssh'ing into it first to see if it gives you access at all ?
 I had the same problem when I installed mine, it seems that you have to add a user to the server machine (ftp account) and select the main folder that you will give them access to.

---

### Post by northjerry on 2006-04-17
Thank you very much for replying! Well, I tried SSHing and got:

root@terabyte:/usr/bin# ssh 192.168.0.100
The authenticity of host '192.168.0.100 (192.168.0.100)' can't be established.
RSA key fingerprint is d7:aa:96:09:33:23:b1:e4:12:79:7d:d2:89:33:2a:89.
Are you sure you want to continue connecting (yes/no)? y
Please type 'yes' or 'no': yes
Warning: Permanently added '192.168.0.100' (RSA) to the list of known hosts.
root@192.168.0.100's password:
Linux terabyte 2.6.12-10-386 #1 Sat Mar 11 16:13:17 UTC 2006 i686 GNU/Linux

So I take it is working fine, right?

Also, I copyed a configuration file from the ProFTPD site for basic login, and created the ftp user and group that it requires.

After that I tried using gFTP this time and set it to use anonymous, port 21, and ftp protocol, and connection refused, then instead of ftp I selected ssh2, and then this appeared and it got stuck there, so I hope we're getting on the right track :P

Opening SSH connection to 192.168.0.100
Running program ssh -e none -l ftp -p 21 192.168.0.100 -s sftp

I'll keep trying stuff out...might even switch back to wu-ftpd and try again there :S

---

### Post by dmizer on 2006-04-17
what is the ip address of the machine you are trying to ftp from?

---

### Post by northjerry on 2006-04-17
[QUOTE=dmizer]what is the ip address of the machine you are trying to ftp from?[/QUOTE]
The IP is 192.168.0.100 and I'm trying to ftp from itself;I also tried 127.0.0.1, but same luck.
I figure I should try and make it work locally first then start testing it with other clients :)
Thanks!

---

### Post by dmizer on 2006-04-17
have you added a new user account for ftp access on this machine like Trajan suggested?  that's the only thing i can think of at this point too.

trying different clients isn't going to correct this problem.  if you can't ftp with the shell, you're not going to be able to get it to work through a gui.

edit to add: there could also be a problem with your router.  you might try rebooting it by unpluging the power and reconneting.

---

### Post by northjerry on 2006-04-18
Hey Guys, thank you so much for your help. I did so much stuff to my FTP and while I though I restarted services and all, I guess I didn't 'cause today when I turned on the PC the FTP now takes logins, hehe. Only weird thing is now my primary user account doen't work, but I just created a new one and it's all smooth saling from here.
Thank you Trajan, and thank you dmizer!!! Greetings from Mexico!

---

