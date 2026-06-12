---
title: "Citrix ICAClient gives SSL Error 61"
date: 2012-07-20
forum: General Help
---

### Post by yesterdayman on 2012-07-20
It's Friday night and I'm feeling frustrated. :(

I am a complete Linux newbie and every time I think I have found a solution to a problem a new one pops up to bite me on the backside.  I am trying to get Citrix to work under ubuntu 12.04.  I can get to the point of logging in to the host site but when I click on the application I want there I get a "SSL error 61" message.

I thought I had found a command line solution by searching this site, but it doesn't work for me.  The command line is:

sudo cp /usr/share/ca-certificates/mozilla/* /opt/Citrix/ICAClient/keystore/cacerts

So then I thought I would copy and paste.  I was able to copy alright but I wasn't able to paste in to the destination folder - no permission, and I couldn't change the permissions because I am not the owner of the folder.  The owner is root.  That maybe explains why the command line didn't work.  So how do I log in as root?  Or is there a workaround?

---

### Post by yesterdayman on 2012-07-24
With a bit of research (thanks Mr Google) I fixed it myself.  I found out that if I run the Terminal app then type 'sudo -s' it changes to root user status with a # prompt, then type the command without 'sudo' at the front it works.  Then 'exit' from the root user status.

However, as originally stated, when using the Alt-F2 command function it would not work.  This may seem obvious to experienced Linux users, but to a newbie it is not.

---

### Post by honzag on 2012-09-07
I do not understand why everyone is satisfied with this solution (cp /usr/share/ca-certificates/mozilla/* /opt/Citrix/ICAClient/keystore/cacerts or similar ln -s ...)
This did not help me until I made the export of Thawte SSL CA  certificate into the file (*.crt) and put it into /usr/share/ca-certificates/mozilla/ .

---

### Post by ebeyer on 2013-03-04
> **yesterdayman said:**
> With a bit of research (thanks Mr Google) I fixed it myself.  I found out that if I run the Terminal app then type 'sudo -s' it changes to root user status with a # prompt, then type the command without 'sudo' at the front it works.  Then 'exit' from the root user status.

However, as originally stated, when using the Alt-F2 command function it would not work.  This may seem obvious to experienced Linux users, but to a newbie it is not.

You lost me.  Could you please walk me through how you did this, step by step?  Many thanks in advance.
EB

---

