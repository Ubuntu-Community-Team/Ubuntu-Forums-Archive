---
title: "setting up apache, got problem with php 5."
date: 2012-02-02
forum: General Help
---

### Post by jamstir on 2012-02-02
Hi people, i have tried a few things to get a web design page logged onto my server though apache and hit on the php not being set right, have read a few post on the matter but no one really given clear answer.

I dont know if i should try and conf.. apache or php or both, in the terminal window it says i have php 5 installed, when i try to call it up though root i get this..

jam@jam-desktop:~$ su
Password: 
root@jam-desktop:/home/jam# /etc/php5/apache2/php.ini
bash: /etc/php5/apache2/php.ini: Permission denied
root@jam-desktop:/home/jam# 

Anyone throw ideas my way please.

If anyone else is at the start of setting there own server at home using apache please jump on board, so far i got apache  server, got some free tools from ubuntu for web design, filezilla etc. 
At the stage now of trying to get the first web page uploaded. PHP 5 is my nut. hahaha.

---

### Post by Dumbestcrayon on 2012-02-02
Did you install PHP and Apache with the [LAMP]("https://help.ubuntu.com/community/ApacheMySQLPHP") package?

---

### Post by jamstir on 2012-02-02
> **Dumbestcrayon said:**
> Did you install PHP and Apache with the [LAMP]("https://help.ubuntu.com/community/ApacheMySQLPHP") package?


Thanks for reply, no i got apache from somewhere else,  please forget about this problem, i thought i found the problem and gave a few root commands, turned out i made the problem worse.
I have now uninstalled apache... should i take php5 of to along with other package SQL. etc.

I new to ubuntu, i near sure i followed unbuntu how to install apache and php, right from the start i had a problem with php not being at localhost. I tried everything that ubuntu told me and nothing seemed to get php to say it was working with apache.
I have got rid of apache due to another site i went to for help, but the commands removed certain things and really lost where i was with apache due to this.

I have now downloaded xampp to desktop, i extracted the file to desktop then tried to move it into home folder, which leads me to my problem. lol

I called the home folder to open, it sits there and try,s to load then it stops without loading ,, i then try and close it and i end up having to force quit.
Any ideas??
While it was trying to load for the 4th time i throw the file from desktop [ xampp ] into it, then went to sudo, but sudo says its not there.

---

