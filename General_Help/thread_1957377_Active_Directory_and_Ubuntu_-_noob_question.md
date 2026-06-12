---
title: "Active Directory and Ubuntu - noob question"
date: 2012-04-12
forum: General Help
---

### Post by mrwoo on 2012-04-12
Greetings.

I am probably an advanced windows user. I have dabbled in different unix/linux distros over the years, mainly to see what has changed from time to time. I support too many people (you know, the family/friends) and use windows too much at work and home to really switch over, although I am not really opposed to the idea, just don't have a need.

Anyway, the school my kids go to has asked me to help solve a problem for them.

They have a server (of what capacity I don't know for sure, but new-ish, probably core2 era or newer) with vmWare ESX, running a PDC and BDC with windows 2008 server. They recently switched to terminals basically, rather than workstations, using terminal services (or is it RDP now lol). They have about 200 accounts and are using Active Directory.

They want to create a file server, running a linux flavor, so that thier files are available should the PDC go down. While I am no slouch in using a console, or in learning anything new, the linux world is just unknown to me.

So here is the question. I don't expect anyone to do the work for me, just maybe give some good resources and tips.

I need to install ubuntu server on the ESX server (no problem). I need to install samba (no problem). I need to have it join the domain (don't forsee a problem). I need to create the directories on the ubuntu server (not really a problem) and set the rights (maybe a problem), and most likely install LDAP and other packages (probably a problem).

Now, I do understand the rights, at least in the windows world. I have messed with ADS a bit, and while not intimately familiar, I am not without the basics I believe. I am wondering, is there a way (I assume via scripting) that I can create all the shares on the ubuntu server that the active directory currently is using? Home shares I think is what they use. As well, not having a domain at my house, when the ubuntu server joins, does it import all the necessary rights?

I am assuming here there are some tricks to this to make it easy. I was not exactly jumping with joy when I thought about creating the file (share) structure on the ubuntu server, and then having to set all the parameters. There are a lot of parameter I know nohting about, so not only would it take a good deal of time to create, but an even greater deal of time to learn.

Now, I am not opposed to learning, but I also know one can be smart and glean the experiences of others. I guess that is what I am looking for ;)

Thanks to anyone interested enough to help me out.

MrWoo.

---

### Post by raja.genupula on 2012-04-12
[https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto)

---

### Post by mrwoo on 2012-04-12
Thank you. I have visited many pages already, but not seen that one yet.

MrWoo.

---

### Post by raja.genupula on 2012-04-12
ok if that helps you to solve your issue please mark the thread as solved , if its not then let us know whats giving the issue . we will try our best to help you .

---

### Post by mrwoo on 2012-04-13
okay. It will take some time to see if i get it all working, but I will be sure to do as you suggest.

I will likely have to first set some machines up to mimic a small domain, as I cannot mess with thier current system until I am sure I have it ready.

Thanks again.

mrwoo.

---

