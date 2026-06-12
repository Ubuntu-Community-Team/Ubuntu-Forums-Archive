---
title: "Disable PasswordAuthentication using public/private key with ssh. What about sftp?"
date: 2010-03-27
forum: General Help
---

### Post by leesiulung on 2010-03-27
[FONT=Arial][SIZE=1]So after tinkering for a while, I was able to configure ssh for private/public key authentication and disabled[/SIZE][/FONT]  [COLOR=black][FONT=&quot][FONT=Arial][SIZE=1]PasswordAuthentication. 

In the past I had some issues with people brute force trying passwords/usernames so I want to avoid this, but I need some form of secure FTP that now doesn't work due to the aforementioned setting.

What other options do I have?
[/SIZE][/FONT][/FONT][/COLOR]

---

### Post by leesiulung on 2010-03-27
Is there a way to use the private key with the sFTP for authentication instead of the password?

---

### Post by leesiulung on 2010-03-28
Thought I follow up on my own post and let others that find this thread in the future know of my solution.
 
 It turns out that SFTP is automatically configured for whatever setup I do for ssh. Thus, SFTP DOES support public key authentication and you just have to use the ftp client properly.
 
 In my case, I used FileZilla and to authenticate myself I just added the key by going to edit->settings->Connection->SFTP  and added key. Further instructions about this was found at the [FileZilla wiki about public key authentication]("http://wiki.filezilla-project.org/Howto#SFTP_using_SSH2:_Key_based_authentication").

It works for me. I hope it works for you!

---

