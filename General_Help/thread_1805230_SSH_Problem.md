---
title: "SSH Problem"
date: 2011-07-15
forum: General Help
---

### Post by renegadeandy on 2011-07-15
This is odd, I have a remote machine which I have git etc running on. Today I attempt to ssh into the box and this is my response! How can I fix it - baring in mind this machine is remote and I have no direct access to it :)

Below is the message it gives me :)



andy@andy-laptop:~$ ssh [email]andy@novo.dyndns.tv[/email]
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@       WARNING: POSSIBLE DNS SPOOFING DETECTED!          @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
The RSA host key for novo.dyndns.tv has changed,
and the key for the corresponding IP address 94.174.193.128
is unknown. This could either mean that
DNS SPOOFING is happening or the IP address for the host
and its host key have changed at the same time.
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
ca:2f:88:64:05:00:a3:a6:c7:4d:cb:b5:f2:a4:0e:a8.
Please contact your system administrator.
Add correct host key in /home/andy/.ssh/known_hosts to get rid of this message.
Offending key in /home/andy/.ssh/known_hosts:1
RSA host key for novo.dyndns.tv has changed and you have requested strict checking.
Host key verification failed.


Cheers:o

---

### Post by papibe on 2011-07-15
It is a common situation when using a dynamic DNS service like dyndns.

What is happening is that your laptop remembers the last time you connected to the other box, and it saves both name and IP. Since that IP may change (main reason to use dyndns), ssh will take the safest path, which is to warning you, and denied the connection.

To revert that, you can, as suggested on the warning, delete the file ~/.ssh/known_hosts, or even the whole ~/.ssh directory.

Bad news is this is going to happen again, and again. The solution that I know is to setup a public key authentication system. Take a look at this tutorial to learn how to do it: [Beginning SSH on Ubuntu]("http://principialabs.com/beginning-ssh-on-ubuntu/").

Hope it helps.

---

### Post by luckyu on 2011-07-15
This message means the RSA encryption that gets initializes when you first connect via SSH don't match. This is caused by stuff in the warning in the message. Most likely you either deleted the .ssh folder on your remote computer, or changed the remote system by reinstalling Ubuntu or Upgrading.

To fix this problem rule out any nasty stuff.
> IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY
If not, then proceed with deleting the .ssh folder in your home directory.
```
/home/username/.ssh
```
Note
.ssh is a hidden folder hence the . infront of ssh

---

### Post by renegadeandy on 2011-07-15
ty pipibe - hit the nail on the head.

---

