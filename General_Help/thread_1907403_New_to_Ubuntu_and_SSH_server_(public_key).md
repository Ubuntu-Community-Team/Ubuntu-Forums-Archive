---
title: "New to Ubuntu and SSH server (public key)"
date: 2012-01-11
forum: General Help
---

### Post by xl97 on 2012-01-11
Hi, this is my first install on Ubuntu. I am trying this because I could not get freeSSHd (or other flavors) of SSH Server to work on an older XP Pro box.

We have a client that wants to send us their datafile over SSH. They are on a UNIX/AIX environment, nothing windows, and want to send file automated. We need to comply, and offer an SSH account/access for this. They have sent over a 'public key' file that is supposed to be placed [somewhere] so it authenticates them as them being them and us being us.. =)

I installed Ubuntu on an old machine, and found an tut to install the SSH server
(simple enough).. I went to my Windows box and used putty to test it.. and it seemed to log in fine using a username/password combo (testing locally using LAN IP, I have not even tried to test from outside the firewall and having an SSH request forward over to the Ubuntu machine to handle the rest)..

I then went back to the Ubuntu install, and made a new user account on the system user: 'xxx' which was a standard account, and gave it password...

went back to Windows machine again, tested, using the new user account name/password, and it also worked.

At this point I am bit stumped on how to get these key files our client sent over to us, that are supposed to be placed in some directory (no clue how to even navigate this to directory.. I dont see anything when I am searching through GUI explorer form home folder..etc)

Anybody provide a first timer with some help/advice?

Appreciate any replies.

thanks!  :popcorn:

---

### Post by Buntumatic on 2012-01-11
Have you tried Google? Below is the first hit.

[http://www.debian-administration.org/articles/530](http://www.debian-administration.org/articles/530)

---

### Post by i.r.id10t on 2012-01-11
Your client will generate a public/private key pair.  Then they need to get you the public key, and simply cat the file into ~/.ssh/authorized_keys

If you need multiple keys to be able to connect, just append the keys to the file

cat id_rsa.pub-1 >> ~/.ssh/authorized_keys
cat id_rsa.pub-2 >> ~/.ssh/authorized_keys

etc

---

### Post by xl97 on 2012-01-11
I did.. which is how I got the SSH Server installed to begin with.

however begin 'new' to all this.. the key stuff is a bit confusing.


How do I get the public key files our client sent us, 'installed' to the correct directory?

I dont even see a .ssh directory in the home directory?

What am I missing?

This is my first Ubuntu install (never Linux anything before)..and new to SSH..

thanks

---

### Post by xl97 on 2012-01-11
> **i.r.id10t said:**
> Your client will generate a public/private key pair.  Then they need to get you the public key, and simply cat the file into ~/.ssh/authorized_keys

If you need multiple keys to be able to connect, just append the keys to the file

cat id_rsa.pub-1 >> ~/.ssh/authorized_keys
cat id_rsa.pub-2 >> ~/.ssh/authorized_keys

etc

thank you.

Yes.. they did send us the public file(s).. 3 actually.

This is the part I am having trouble with.  (maybe more of a basic Ubuntu user question?)

when you say I 'simply' cat the files.. do you mean copy? Is that what 'cat' means?


I have 3 files they sent  filename.dat,   filename2.dat    &    filename3.dat

I drag-dropped them form our fileserver to the Ubuntu desktop.. (in its own folder)

so this 'cat' is this done form the terminal screen? 


thanks


I tried to do as suggested, not sure if my syntax or pathing/scope is wrong here?

admin_user_name@admin_user_name-GE-PRO-M2:~/Desktop/SSH_keys$ cat id_epcdvmt01.dat >> ~/.ssh/authorized_keys
bash: /home/admin_user_name/.ssh/authorized_keys: No such file or directory
admin_user_name@admin_user_name-GE-PRO-M2:~/Desktop/SSH_keys$ 


Do I need to so this under the NEW user account I created on the system for our client to be able to use and log-in to the SSH server?

thanks

---

### Post by xl97 on 2012-01-11
ok.. after some trial error..

I think I got the public keys our client sent us installed to the .ssh/authorized_keys file


in theory.. "I" shouldnt be able to log-in...right? to test the account?

because I dont have their (private?) key installed on any client.. I only have the public key(s) they sent us...to be installed on the Ubuntu SSH server authorized_keys file...right?



If I go to my Windows machine (same network).. and open 

WS_FTP Pro:

create an SFTP/SSH account with the clients username & password (same as the client account on the Ubuntu machine user/pass)..

and try to log-in.. 

I am prompted with message that says: unknown public keys: trust, dont trust options..

if I trust..I am brought to the users HOME directory on the Ubuntu machine (not sure how that can be changed?..or even to a sub directory in that users HOME directory?)


bt should I be able to lgo-in? since I dont have the other half of the key from the client?

(a bit unclear on how it all works)


second results..

if I use PUTTY to try to log-in..

open it up.. enter in local IP of Ubuntu SSH server machine..

it prompts for user name: (enter) 

then prompts for password:  (enter)

it seems to accept it..then putty closes immediately???


so 3 questions, outstanding issues:  (if anyone has any help to suggest) :)


1.) should I be able to log-in/test the account, since I only have that public key they sent? how do I or they verify? wouldnt it just let anyone in then if they accept/trust the key? So not sure if I have their keys installed right? or why that is happening? thoughts?


2.) PUTTY? why the immediate closing? never done that before?


3.) how can I 'lock' the user into another directory for them to place their file? and NOT just the -root- of their home directory?


thanks!  =):P

---

### Post by Buntumatic on 2012-01-11
1. No
2. Putty ... dunno ... did you disable password authentication in SSH?
3. [http://www.debian.org/doc/manuals/securing-debian-howto/ap-chroot-ssh-env.en.html](http://www.debian.org/doc/manuals/securing-debian-howto/ap-chroot-ssh-env.en.html)

---

### Post by btindie on 2012-01-11
You won't be able to test your clients public key because you haven't got the corresponding private key.

When you create the .ssh/authorized_keys file you need to have the correct permissions set on dir and file. The easiest way for you to do this is:

[LIST=1]
[*]SSH into the Ubuntu server as use 'xxx' and run 'rm -rf ~/.ssh' to remove the existing files
[*]Use [WinSCP]("http://winscp.net/") to copy the public keys your client sent you to the server, place them in the root of the users home directory. It should be something like bill.pub, ben.pub, etc..
[*]Use ssh-copy-id to add the public keys to the user account which automatically sets the correct permissions: ssh-copy-id -i bill.pub localhost
Repeat for each key you need to add
[/LIST]
The above ssh's to the local machine and adds the pub key to the authorized key file. You can do this all manually but this is probably the most straight forward. If the permissions aren't set correctly it won't let you use public key authentication for ssh.

If you want to test that public key authentication is working correctly then you'll need to generate your own public/private key pair with PuTTYgen and add that to your own account.

When you connect to an SSH server for the first time the client will show you the servers key finger print as you haven't got a record of it in your .ssh/known_hosts file. This is primarily to stop man in the middle attacks so you know that you're connecting to the correct server. You can generally just ignore it and select yes to add the key locally.

Does the client need full SSH access to the server or would SFTP/SCP access suffice? There are various programs available that allow you to chroot the user account so they can get else where on the filesystem. They are scponly, rssh and sshd itself - [OpenSSH SFTP chroot() with ChrootDirectory]("http://www.debian-administration.org/articles/590")
[http://www.howtoforge.com/restricting-users-to-sftp-plus-setting-up-chrooted-ssh-sftp-debian-squeeze](http://www.howtoforge.com/restricting-users-to-sftp-plus-setting-up-chrooted-ssh-sftp-debian-squeeze)

Note: If they can SSH to your box then they'll have full access to your internal network so you may want to put the Ubuntu box in your DMZ or limit the access to only allow SCP.

---

### Post by apmcd47 on 2012-01-11
I notice you are asking some basic questions but only the ones surrounding ssh are being answered.

You said you could not see the .ssh directory. Hidden files on Windows rely on a file attribute - on Linux it is as simple as prefixing the filename with a full-stop. On your server go to your home directory and type: ```
ls -AF
``` 
A lot of files you didn't know you had will now appear in the file listing. Any filenames suffixed with "/" are directory names. The following command adds to this list the current directory (.) and the parent directory (..):
```
ls -aF
``` 
You will notice .ssh is there.

**cat** is a file listing program also useful for **cat**enating files into other files.

**>** and **>>** redirect the output of the last command or pipeline into a file, creating it if necessary. If it exists **>** will overwrite the file while **>>** appends to the file.

The client may have sent you a public key file in the wrong format. Check with wc:```
wc -l keyfile.pub
```
If it indicates the file is one line long it is in the correct format, else type:```
ssh-keygen -i -f keyfile.pub > rightkey.pub
```
cat the new file into your authorized_keys file (or rather your client's file).

You may wish to send your client the server fingerprint so that they know they are logging into the right machine first time.

Andrew

---

