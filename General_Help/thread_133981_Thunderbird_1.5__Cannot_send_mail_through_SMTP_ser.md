---
title: "Thunderbird 1.5:  Cannot send mail through SMTP servers"
date: 2006-02-21
forum: General Help
---

### Post by taelatus on 2006-02-21
(Note: This message was originally posted in a different thread.  I thought it a better idea to create a separate thread in order to get more attention.)

I just downloaded and configured Thunderbird 1.5 and installed a webmail extension I found online. The webmail extension allows me to check Hotmail. It works just fine. I also configured my school's IMAP mail. It works fine as well (I also happen to be on the same network as the mail server). My problem is when I try to access Gmail and Optimum Online (ISP) mail. When I try to send mail with either of these mail accounts, Thunderbird never seems to connect to the SMTP server. I just see the "connecting to smtp.domain.net" forever. I do know that when I first configured the webmail plugin, I had to specify a port higher than 1024 in order to be connected. My first thought regarding my current problem was that I am somehow blocked by default from accessing ports lower than 1024. I don't know this to be the case but at this point I don't know what to do. I've tried every security setting I can find in Thunderbird and I've checked all the port requirements and logon styles of the accounts I'm trying to configure. Has anyone encountered a problem similar to mine?

In case it helps:
Ubuntu 5.10
Firestarter is NOT installed.
I am on a school network. I have no router or local networking equipment to tweak.
I have not installed any networking packages that I'm aware of.
I can receive mail with Optonline and Gmail but not send it.

---

### Post by akiro.yamamoto on 2006-02-21
The Gmail SMTP server requires SSL Authentification. This was the only problem I encountered. I think it's port 465.

---

### Post by rudiz on 2006-02-21
Check if u fill in the right username in the smtp configuration.

Do you mistakenly used the email address instead of ur account username?

---

### Post by ember on 2006-02-21
A lot of admins nowadays block Port 25 (except for their own mailserver). Sometimes you can work around this by connecting via SSL or as in my case when your provider has an alternative SMTP-Port (e.g. 587).

Otherwise you will have to use you school's mailserver.

---

### Post by batty505 on 2006-02-21
Hi

could you post the instructions for installling thunderbird 1.5?
Im still on 1.07, and would like to upgrade.

Ive done the upgrades from synaptic, but I am unable to install the package.

mike

---

### Post by taelatus on 2006-02-21
Ok I've checked and rechecked settings.  I've tried all the suggestions that were given as well, all without results.  My school's network must block this kind of network traffic.

As for installing Thunderbird 1.5, I never installed the Ubuntu package.  I just downloaded the precompiled binary from the mozilla site, extracted and ran it.

---

