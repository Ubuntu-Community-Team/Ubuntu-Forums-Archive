---
title: "Xtreamer on lucid lynx"
date: 2010-06-19
forum: General Help
---

### Post by Baboontu on 2010-06-19
Hi 
Has anyone managed to get Xtreamer work with ubuntu.
i would prefer making it work via nfs but via samba will be also good as long as it works. 
I had to switch to windows 7 because of this and 
I don't want to abandon ubuntu or linux 
thanks

---

### Post by Baboontu on 2010-06-21
still waiting for a reply? Xtreamer+Ubuntu? anyone?

---

### Post by Baboontu on 2010-06-22
So you've never heard of Xtreamer?
:cry:

---

### Post by Oded Dwek on 2010-11-10
Hello,

I've managed to stream media (videos) to Xtreamer using software called Fuppes, it seems to work with NTFS drives as well.

There is a guide explaining how to set it up on ubuntu 9.10, but it also works for ubuntu 10.10
[http://www.uluga.ubuntuforums.org/showthread.php?t=1310511](http://www.uluga.ubuntuforums.org/showthread.php?t=1310511)

---

### Post by a-user on 2010-11-10
what is your problem connecting to your linux machine via samba? if you can connect to a windows machine it should work more or less the same with a linux machine + samba.

i don't use xtreamer but other things that do this very well via samba (in most cases better than with windows).

---

### Post by Baboontu on 2010-12-03
O.K I'll try it and report
Thanks

---

### Post by Baboontu on 2010-12-04
I've upgraded to ubuntu maverick. It seems that "Fuppes" is too complicated. I tried to do it with samba. earlier I could see my computer in [COLOR="Blue"]Xtreamer[/COLOR] network menu and it asked for username and password. I entered my login name and password( as I did when I was working on Windows),but I didn't manage to access my shared folders ("connection failed" message).
I've attached /var/log/samba/samba.log
Thanks

---

### Post by Baboontu on 2010-12-26
I managed to get it work!
I used a clean samba.conf with a text editor **not** using any other configuration tool. I followed xtreamer's forum instruction on samba and voile! :p

---

