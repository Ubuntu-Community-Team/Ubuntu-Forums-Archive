---
title: "anyone have luck getting evolution to work in 9.10?"
date: 2009-11-16
forum: General Help
---

### Post by zeth01 on 2009-11-16
it receives but doesnt send just puts messages into outbox folder when sending rather than sent.

---

### Post by audiomick on 2009-11-16
send yourself a mail. If it arrives, things are working, and evolution has got confused about where it keeps its' records. Mine has done that once or twice. If it doesn't arrive, the access data for your outgoing server is messed up.

---

### Post by zeth01 on 2009-11-16
did that it dont work so um yeah.  oh and i use gmail.  ill keep trying...

---

### Post by doas777 on 2009-11-16
sounds like your smtp settings are not quite right.
here are mine
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=136518&stc=1&d=1258416606[/IMG]

---

### Post by id10twork on 2009-11-16
Evolution works fine for me after the upgrade. I agree that it sounds as though perhaps you SMTP settings are not quite right. Make sure that if you do tell it to authenticate, you'll also have to have your port #s correct.

---

### Post by Mattos on 2009-11-16
Hey guys

Take this opportunity to ask how can I back up my emails. I wanna upgrade my email client from Evolution 2.26 to 2.28.

So I have some doubts about it, like:


[LIST=1]
[*]Where evolution downloads my emails from server to my pc
[*]Can Evolution do it by itselft or I have to install another software to make a backup.
[*]Can I save the configuration of my account, I'd say like a file or something 'cause all works fine and I don't wanna lose any little parameter of my account (still nooby :P ) and later I have to wonder what'ss wrong ;)
[/LIST]
Regards.

Ubuntu 9.04
Evolution 2.26

---

### Post by audiomick on 2009-11-16
> **Mattos said:**
> Hey guys

Take this opportunity to ask how can I back up my emails. I wanna upgrade my email client from Evolution 2.26 to 2.28.

So I have some doubts about it, like:


[LIST=1]
[*]Where evolution downloads my emails from server to my pc
[*]Can Evolution do it by itselft or I have to install another software to make a backup.
[*]Can I save the configuration of my account, I'd say like a file or something 'cause all works fine and I don't wanna lose any little parameter of my account (still nooby :P ) and later I have to wonder what'ss wrong ;)
[/LIST]
Regards.

Ubuntu 9.04
Evolution 2.26

There is a function is the newer versions of Evolution that exports a .tar.gz that has everything in it. It is in the file menu. When the new one is installed, you can re-import it.

---

### Post by Mattos on 2009-11-16
> **audiomick said:**
> There is a function is the newer versions of Evolution that exports a .tar.gz that has everything in it. It is in the file menu. When the new one is installed, you can re-import it.

Thanks for answer. Yeah, indeed it was there :p and I didn't see it before :oops:

Once again, thanks a lot.

---

### Post by dogooder on 2009-11-19
> **doas777 said:**
> sounds like your smtp settings are not quite right.
here are mine

This fixed my problem. Thanks.

---

