---
title: "A couple of questions about SSH and FTP"
date: 2011-08-23
forum: General Help
---

### Post by CookieCutter on 2011-08-23
I have installed Ubuntu 11.04 onto my PS3 and I am trying to figure out how to SSH onto it with my laptop through the internet and run a FTP program. I have mostly figured out how to set up openssh but I can't figure out how to implement the SSH keys. I've gone through this guide: [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys) and have generated the keys but I don't know how to use them.

I'm also trying to figure out how to run an FTP program through the CLI. I am completely lost on this. I have doodled around with Filezilla but it doesn't seem able to run through CLI.

Any thoughts or suggestions would be very helpful. Thanks

---

### Post by papibe on 2011-08-23
I found this [guide]("http://principialabs.com/beginning-ssh-on-ubuntu/") much more useful.

As you are implementing ssh, you should take advantage of sftp. Its interface behaves almost identical as ftp, but uses ssh underneath so is very secure. Also, if you are able to connect using ssh, then sftp is already configured and ready to use.

Regards.

---

### Post by CookieCutter on 2011-08-23
I think I know my problem. I'm trying to ssh from a windows laptop onto a linux box and these guides assume you're using two linux boxes. I'm using PuTTY which works but can I still employ SSH keys? If not, can I set a different password for logging in through SSH then the one used for sudo commands and logging in locally?

---

### Post by papibe on 2011-08-23
Sure you can, check this [video]("http://www.youtube.com/watch?v=ioGYnsxzL94") tutorial that explains how to use Putty to connect to a VPS running Ubuntu.

Hope it helps,
Regards.

EDIT: Just to be more explicit, I meant, sure you can use **keys**.

---

### Post by CookieCutter on 2011-08-23
You are amazing thank you so much.

---

### Post by CookieCutter on 2011-08-28
Sorry for the double post. I have run into a problem when I try to sftp from my Windows laptop onto my Ubuntu box. I get "Server sent command exit status 128" This also happens for Filezilla so it must be a server side issue. I am completely stumped. Is there something I should install before I am able to sftp onto my ubuntu box? Some threads on Google also suggested that I change the permissions of my home folder to 755. Perhaps I'm entering the command wrong? I'm entering
```
sudo chmod 755 /home
```

It still does not solve the problem however.

---

### Post by YesWeCan on 2011-08-28
On your Ubuntu box you have to have ssh installed, which includes sshd - not installed by default
sudo apt-get install ssh

Test it from the cli on the Ubuntu box itself.
ssh your-username@localhost

---

### Post by CookieCutter on 2011-08-28
I installed ssh and tested it out on the box and I get the following error

```
Permission denied (publickey).
```

---

### Post by YesWeCan on 2011-08-28
I think I picked up the wrong end of the stick here.
You have SSH working ok now but SFTP produces that error. How are you doing SFTP...are you using Putty's PSFTP?
This link might be helpful: [http://ask-leo.com/how_do_i_create_and_use_public_keys_with_ssh.html](http://ask-leo.com/how_do_i_create_and_use_public_keys_with_ssh.html)

---

### Post by CookieCutter on 2011-08-29
I'm doing psftp using WinSCP on my Windows laptop. I enter in all my information and select my private key and try to connect to it. It then connects and authenticates and asks me for my password. When I enter in my password, an error message pops up saying that the connection unexpectedly closed and the server sent exit command 128. Under that it says "Cannot initialize SFTP protocol. Is the host running a SFTP server?"

---

