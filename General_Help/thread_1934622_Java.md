---
title: "Java"
date: 2012-03-02
forum: General Help
---

### Post by leandromartinez98 on 2012-03-02
Hi all.

The Java I had installed in all my Ubuntu machines (10.04 and 11.10) all stopped working with the internet banking of my bank (Santander in Brazil).

This is very unfortunate, as I have no reason to use any other OS, but this issue is becoming problematic. Everything worked fine before, some months ago, in all my machines.

I don't know what Ubuntu finally decided on that Java license thing, but anyway it is not working now.

Do you know if other distros (like Mint) kept their Oracle Java installations and updates? 

Have someone tried some PPA which worked well? I've tried some but with no success.

(no mention that OpenJDK does not work).

Thanks.

---

### Post by lykeion on 2012-03-02
You could try the oracle java jre 6 repository of duinsoft, instructions here: [http://www.duinsoft.nl/packages.php?t=en](http://www.duinsoft.nl/packages.php?t=en)

Otherwise read the community docs on java  here: [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by gunksta on 2012-03-02
Interesting.

Do you still have some form of Java installed on your computer? [Here's a test.]("https://www.java.com/en/download/testjava.jsp") In order for this to work, you will have to enable Java to run in your browser, but given the content of your first message, I would be surprised if you have disabled this.

Beyond, does not work, can you provide any details?. Note - Be careful what you post. I don't want your banking info.

Finally, you can download the 'authorised' version of Oracle Java ,[here]("https://www.java.com/en/download/linux_manual.jsp?locale=en"), but it takes a little bit of work to install since they apparently only distribute RPM files. Install, alien and you should be fine.

---

### Post by dragonfly41 on 2012-03-02
A few minutes ago I updated my java configuration using this tutorial ..

[http://www.shinephp.com/install-jdk-7-on-ubuntu/](http://www.shinephp.com/install-jdk-7-on-ubuntu/)

---

### Post by QIII on 2012-03-02
There wasn't much for Canonical to agree on.  Oracle withdrew the license.

Depending on how the website is set up, it may balk at Java 7.

Try Java 6 Update 31 first.

And the tutorial I recommend is

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

I don't like where they put the symbolic link, but it works.

duinsoft is mentioned and linked in there, if you'd like to do it that way.

If you need Java 7, you can follow the same directions using the correct .bin and changing the commands appropriately.

---

### Post by leandromartinez98 on 2012-03-02
Thanks lykeion! The duinsoft repository worked for me!
Thank you all for the replies.

Leandro.

---

