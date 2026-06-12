---
title: "What does PAM really mean in my life?"
date: 2012-01-11
forum: General Help
---

### Post by mbuell on 2012-01-11
Ok - I googled, and I forum searched. 

What does PAM authentication REALLY mean in my life? What do I have to do with it? WHEN would I need to actually DO anything to make it work?

It seems to come up at strange times, and to be mentioned in obtuse ways. 

Here - let me tell you what I have. I have a slightly older P4 era machine running gnome, samba, and a testbed Oracle database. I keep gnome on there for two reasons - I'm not entirely knowledgable about managing the server from the command line, and I use the machine as a backup desktop on occasion. I have a newer I-5 desktop - dual boot 10.04 and XP, and a laptop, dual boot 10.04 and Win7. Plus some family windows boxes. 

A year ago I was running 9.something as the server, and I had all the machines recognizing the server by name. I upgraded to 10.04, and I can only get them to find the server by IP. I use the same samba.conf.

So, when LDAP and winbinnd get mentioned, and they refer to PAM - I'm confused. I don't think I should even consider worrying about LDAP - but I'm not sure - maybe there is something there I should be doing but I'm not - to get my server recognized by name again? But if I mess with that, apparently I have to mess with PAM. So I'm not even spending any time on it. 

However, I am following a guide to making my server available through ssh when I am traveling for work. I haven't gotten there yet - but part of the business is setting ssh to keyed security, instead of password. 

Is PAM something I am going to bump into and need to know about? Or is it just something that "just works" - and I can safely ignore until something breaks. ?

Thanks for your thoughts.

---

### Post by lykwydchykyn on 2012-01-11
PAM is a framework for providing a consistent authentication interface for services.  Most services use it "under the hood".

I've been admin'ing Linux boxen for many years, and PAM is still a little bit voodoo for me even though I've made a couple of attempts to get my head around it. 

About the only times I've needed to mess with PAM is when I wanted to create some special sort of authentication setup for a service -- like authenticating a workstation to LDAP, or configuring some complex SSH rules.

Usually there are other "front-end" configs that you can work with instead.

---

### Post by mbuell on 2012-01-14
> **lykwydchykyn said:**
> . . . Most services use it "under the hood".

I've been admin'ing Linux boxen for many years, and PAM is still a little bit voodoo for me  . . .

Usually there are other "front-end" configs that you can work with instead.

Fortunately! I ended up here, like I said, because of something else I was trying to do - and I keep running into definitions and how-tos that refer to PAM with implications that something will be broken if I don't do something deeper - which usually turns out to be only one small aspect of the equation. I end up spending hours and days chasing my tail trying to figure things out, and end up not being far from where I started. 

So, a little frustration was leaking out in that rant! But your answer is reassuring. 

Just yesterday I finally got some completion on the first step in my project - I got an ftp server running and open outside my router. I started getting references to PAM when I got into making the connection secure. 

There are quite a few docs on setting up vsftpd that seem to imply creating a nologin user is the most secure option, which is where PAM gets involved - authentication. 

I started looking at the nologin thing - sounded logical to me - and started finding people pointing out that a nologin user was "not security". That led to another level - they got down to the level of recommending disabling PAM for vsftpd. 

At that I decided that was a bad trail. After all, vsftpd has the reputation, widely repeated, of being written with security as job 1. The default setting on vsftpd is to use anonymous ftp. And, I am sure the people who put Ubuntu together keep security in mind - yet they not only have PAM, but they apply it to vsftpd. So, the nologin trail ended up going against how some very smart people are doing things. I have to have faith in somebody, so I will stick with the original designers. 

Memories of the tar baby!

regards!

---

