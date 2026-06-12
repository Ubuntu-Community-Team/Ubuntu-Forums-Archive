---
title: "Easier way to setup email server?"
date: 2010-04-17
forum: General Help
---

### Post by DanB91 on 2010-04-17
I followed this tutorial to setup a mail server [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/) to no avail.  The server also has an apache2 web server that uses a no-ip.org address.

Whenever I try to send mail to that server using [email]root@mail.mydomain.no-ip.org[/email] it doesnt work, it says the domain name doesn't exit, so I know it can't be just the wrong user.  Am I just sending it to the wrong domain name or is there an easier way to set up postfix than the one in the tutorial (I am willing to reinstall it if necessary).   

Thank you very much

---

### Post by zvacet on 2010-04-17
See if [this]("https://help.ubuntu.com/8.04/serverguide/C/index.html") helps.

---

### Post by DanB91 on 2010-04-17
thanks for the help.  I followed this and when i enter "telnet mail.mydomain.no-ip.org 25" it says it cannot be found (though when it's just "mydomain.no-ip.org" it works.  

please help thanks

---

### Post by DanB91 on 2010-04-18
bump (srry if not allowed to bump)

---

### Post by DanB91 on 2010-04-18
bump again srry

---

### Post by itiswhatitis on 2010-04-18
First, you should see if postfix is listening.  On the server type:

```
telnet localhost 25
```

If you connect and get a response, then you know you it's working.  If it's not, start postfix 

```
sudo /etc/init.d/postfix start
```

Then try telnet again.  

If you can connect, try from a remote computer.  If you can't, it's probably a firewall issue.  Could be that your router is not set up to forward port 25 traffic to your server.  (home routers need this configured)  Could also be that your firewall on the box is blocking the port 25 traffic.

---

### Post by DanB91 on 2010-04-18
"telnet mydomain.no-ip.org 25" works fine but "telnet mail.mydomain.no-ip.org 25" doesnt work (probably because I havent set up subdomain "mail" which I dont know how.


So it does seem that postfix is working.  when i send email to [email]postmaster@mydomain.no-ip.org[/email] it seems to go through, though i dont know where the message is stored.  When I try to send mail using the server it doesnt work.  

So using this tutorial you can only send mail to the server, or should u be able to do both?

EDIT: I am assuming I should install all of the mail related services as seen in the second post.  I will try that and edit this post
EDIT2: It seems I don't need use exim since im gonna use postmaster

---

### Post by lisati on 2010-04-18
There are multiple answers to this.

If you have [webmin]("http://ubuntuforums.org/showthread.php?t=1445655") installed on your server, you should have an option severs->postfix->user mailboxes which will let you read your mail.

---

### Post by DanB91 on 2010-04-18
> **lisati said:**
> There are multiple answers to this.

If you have [webmin]("http://ubuntuforums.org/showthread.php?t=1445655") installed on your server, you should have an option severs->postfix->user mailboxes which will let you read your mail.
I am looking at that.  so if I just install webmin, it should come with postfix and wont touch my current apache site? 

I do not have access to the actual computer right now as I am doing everything via ssh and the debian package for some reason doesn't want to install (i am using dpkg -i and it says need access option).

I just discovered where the mail was so it did receive my mail!

One problem though, I installed exim and I didnt like that too much so I installed postfix.  I can telnet the server but once i do, the ehlo command (or any command for that matter) doesnt work anymore (it did before i installed exim).  Is there anything i have to do?   should i just uninstall postfix completely?  thanks

---

### Post by lisati on 2010-04-18
> **DanB91 said:**
> I am looking at that.  so if I just install webmin, it should come with postfix and wont touch my current apache site? 


If you choose to install postfix, you'll have to do it separately.

---

### Post by DanB91 on 2010-04-19
I am trying to access webmin from a remote computer, but it won't work.  what do i have to do to make accessible to the world?

---

### Post by DanB91 on 2010-04-19
bump

---

### Post by lisati on 2010-04-19
> **DanB91 said:**
> I am trying to access webmin from a remote computer, but it won't work.  what do i have to do to make accessible to the world?

You might need to set up https: and/or forwarding of port 10000 in your router.

---

### Post by lucaspr on 2010-04-21
[qoute]
"telnet mydomain.no-ip.org 25" works fine but "telnet mail.mydomain.no-ip.org 25" doesnt work (probably because I havent set up subdomain "mail" which I dont know how.


So it does seem that postfix is working. when i send email to [email]postmaster@mydomain.no-ip.org[/email] it seems to go through, though i dont know where the message is stored. When I try to send mail using the server it doesnt work.

So using this tutorial you can only send mail to the server, or should u be able to do both?

EDIT: I am assuming I should install all of the mail related services as seen in the second post. I will try that and edit this post
EDIT2: It seems I don't need use exim since im gonna use postmaster 
[/qoute]

I'm reading this and thought about this.. 

Can you ping to your server from a remote pc? ping mail.mydomain.no-ip.org

What does that come up with? is it the same IP as without the mail. (before mydomain....)

just a thought maybe I'm searching in the wrong direction.

---

