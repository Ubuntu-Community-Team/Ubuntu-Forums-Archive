---
title: "ssh disable password authentication not working."
date: 2010-08-16
forum: General Help
---

### Post by gozo311 on 2010-08-16
Hi wonderful world of ubuntu users.  I have a problem with ssh.
I followed this guide:
[http://lani78.wordpress.com/2008/08/08/generate-a-ssh-key-and-disable-password-authentication-on-ubuntu-server/](http://lani78.wordpress.com/2008/08/08/generate-a-ssh-key-and-disable-password-authentication-on-ubuntu-server/)

and no matter what I try, I still can't disable password authentication.  I want users to require a private key to prevent from brute force hackers.

---

### Post by stlsaint on 2010-08-16
Attach your sshd_config from server here.

---

### Post by HermanAB on 2010-08-16
Howdy,

Did you restart sshd after making the change?

---

### Post by gozo311 on 2010-08-16
Thanks, 
Here is what is not commented in my server's ssh_config:

<code>
Host *

    RSAAuthentication yes
    PubkeyAuthentication yes
    ChallengeResponseAuthentication no
    PasswordAuthentication no
    UsePAM no
</code>

And yes, I reload /etc/init.d/ssh every time I change something.
It's weird to me.  I also tried reinstalling ssh on the server.

Wait.  Am I being silly and editing the wrong file?  What's the difference between sshd_config and ssh_config?

---

### Post by gozo311 on 2010-08-17
Yeah, that was the problem.  Apparently:
ssh_config is the SSH client configuration file (i.e. is used by the ssh program itself). sshd_config is the SSH daemon configuration file (i.e. is used by sshd).

---

### Post by CharlesA on 2010-08-17
Yup. You'd need to edit sshd_config to make changes to the server. :)

---

### Post by gozo311 on 2010-08-17
Thanks, y'all.

---

