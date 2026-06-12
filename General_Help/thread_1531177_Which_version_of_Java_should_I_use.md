---
title: "Which version of Java should I use?"
date: 2010-07-14
forum: General Help
---

### Post by Volfan94 on 2010-07-14
Hey everyone, I installed Ubuntu on my older PC last night and I am REALLY impressed by it! I tried to go to pogo.com to play a few games of online pool. It tells me that I don't have Java so I click on the link to install Java. For Linux, the 32 bit options are "Linux RPM (Self-extracting file), and Linux (self-extracting file). Which one should I install?

---

### Post by akakingess on 2010-07-14
Either should work, but I would recommend the RPM, so try it first and if you have any trouble let us know. Although, I do know that there are some debs out there that are much easier ways to install Java within Ubuntu. You may want to google for a deb version.

---

### Post by howefield on 2010-07-14
Easiest way would be using Synaptic Package Manager, openjdk or if you prefer Sun Java, you would need to enable the partner repository first.

---

### Post by akakingess on 2010-07-14
Will openjdk install the jre as well? I am just curious and not questioning you, just want to know so that I don't have to do both separately in the future.

---

### Post by nmaster on 2010-07-14
> **howefield said:**
> Easiest way would be using Synaptic Package Manager, openjdk or if you prefer Sun Java, you would need to enable the partner repository first.
+1

you can also get the packages by using apt=get or aptitude from the command line, but in any case this will be way easier that downloading a package from the internet. you should read this if you don't know about installing software [https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

---

### Post by KdotJ on 2010-07-14
> **akakingess said:**
> Either should work, but I would recommend the RPM, so try it first and if you have any trouble let us know. Although, I do know that there are some debs out there that are much easier ways to install Java within Ubuntu. You may want to google for a deb version.

Isn't RPM just for Red Hat based distros?

---

### Post by nmaster on 2010-07-14
> **KdotJ said:**
> Isn't RPM just for Red Hat based distros?

yeah, but you can "alien" the package to install it on a debian distro.

---

### Post by sarim on 2010-07-14
there is a package like named "sun java plugin" . install it and you will go fine.

---

### Post by QIII on 2010-07-14
Why make it hard?  Why alien an .rpm?

Sun Java Update 20 is in the partner repo.  When installed from there, it will be updated to a newer version during normal updates when Oracle makes it available in the repo.

No muss.  No fuss.  No worries.

Install it from the repo.  Simple.

Now, what may not be so simple is the continuing controversy over whether Sun Java and OpenJDK can really live together peacefully.  Since OpenJDK can be easily reinstalled if you want to, try removing it before installing Sun Java.

Also be aware that much of the world at large does not recognize OpenJDK as Java yet.  My bank's website won't touch it.  As a matter of fact, when new Sun Java versions come out, I get nasty messages if I haven't updated.

Again back to installing from the repo.  I do my normal updates, my Bank doesn't complain.

KISS.

---

### Post by howefield on 2010-07-14
> **KdotJ said:**
> Isn't RPM just for Red Hat based distros?

Yep, it's poor advice for an Ubuntu installation especially where there is a .deb alternative.

Even when there isn't a deb package, you'd probably want to point out the potential pitfalls and requirements.

---

### Post by TBABill on 2010-07-14
Install via Synaptic. When updates are available you will receive them on regular updates. Downloading from the Internet is not normally a good idea unless there is no alternative. The openjdk was awful on my machine and Sun Java corrected all issues.

---

### Post by howefield on 2010-07-14
> **akakingess said:**
> Will openjdk install the jre as well?

Probably, if you install openjdk-6-jre...

To the OP, for what it's worth, I prefer Sun Java, and the packages I install are, sun-java6-jre, sun-java6-fonts and sun-java6-plugin.

---

### Post by akakingess on 2010-07-14
> **howefield said:**
> Yep, it's poor advice for an Ubuntu installation especially where there is a .deb alternative.

Even when there isn't a deb package, you'd probably want to point out the potential pitfalls and requirements.


Yes, and if you read my whole post I did tell the OP to find/use the deb version of the installer.

---

### Post by howefield on 2010-07-14
> **akakingess said:**
> Yes, and if you read my whole post I did tell the OP to find/use the deb version of the installer.

Must be my mistake then...

You may have told the OP to find a .deb, however your recommendation was to use the RPM first. 

Incidentally, you might want to avail yourself of the CoC, Section II, point 10. No offence, just saying.

---

### Post by akakingess on 2010-07-14
> **howefield said:**
> Must be my mistake then...

You may have told the OP to find a .deb, however your recommendation was to use the RPM first. 

Incidentally, you might want to avail yourself of the CoC, Section II, point 10. No offence, just saying.


Point taken, and I appreciate the heads-up, I just didn't want everyone thinking that I was suggesting using the RPM INSTEAD of the deb, obviously the deb is always the preferred method. I should have reworded my post to point that out, though. My main concern is that the OP gets the help that they deserve. BTW, no offence taken, I take contructive criticism very well (how else can I improve ;)

---

### Post by Volfan94 on 2010-07-14
> **QIII said:**
> Why make it hard?  Why alien an .rpm?

Sun Java Update 20 is in the partner repo.  When installed from there, it will be updated to a newer version during normal updates when Oracle makes it available in the repo.

No muss.  No fuss.  No worries.

Install it from the repo.  Simple.

Now, what may not be so simple is the continuing controversy over whether Sun Java and OpenJDK can really live together peacefully.  Since OpenJDK can be easily reinstalled if you want to, try removing it before installing Sun Java.

Also be aware that much of the world at large does not recognize OpenJDK as Java yet.  My bank's website won't touch it.  As a matter of fact, when new Sun Java versions come out, I get nasty messages if I haven't updated.

Again back to installing from the repo.  I do my normal updates, my Bank doesn't complain.

KISS.

I did that and it's working like a charm! I'm really shocked at the Linux community. You would never get this kind of help online for a Windows machine.

---

### Post by soldier1st on 2010-07-17
i know what you mean, i think i may partialy know why and that they have  to read you a script as the people are paid to follow a script.

---

