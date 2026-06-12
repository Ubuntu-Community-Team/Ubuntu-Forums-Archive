---
title: "How to setup 1.6.22 java applet and skype on maverick"
date: 2010-10-29
forum: General Help
---

### Post by cmcx_linux on 2010-10-29
I apologies if this is a double post.

What I did:

1. Enable the Canonical Partners repos.
 This is for kde users, in gnome might be a little different.
So, go to Software Management -> settings -> Edit Origins -> Type in your password -> Other Software-> check the Canonical Partners Repo.

2. Skype and java 6 from sun will become available, so update sources and install:

skype sun-java6-jre sun-java6-plugin 

This update of skype is not available on their website yet.
 IT FIXES THE UPSIDE DOWN WEBCAM PROBLEM FOR CNF7129 cams.

3. For the java part you need to go to your konsole/terminal and type in the following:
 sudo update-java-alternatives --plugin --jre --set java-6-sun

4. Restart your browser and go to :
[http://www.java.com/en/download/installed.jsp](http://www.java.com/en/download/installed.jsp)

You should have the latest java installed.

I've tested this setup on Kubuntu 10.10 x64 and I must say that it works like a charm. I am very surprised of the latest java update. The javaFX applets load as fast as flash applets. 

Hope it helps someone.

---

