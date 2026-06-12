---
title: "Qt browser is slow"
date: 2010-01-28
forum: General Help
---

### Post by shariefbe on 2010-01-28
hello,
   I installed Qt X11 browser in my netbook which consist of ubuntu 9.10. All are fine but when i start qt browser it is slow. I dont know why. Can anyone please help me?

---

### Post by shariefbe on 2010-01-29
didnt get the solution for this. so i tried to compile QtEmbedded for my x86 processor (ie)intel processor. This time it compiles well and when i start the browser i am getting this error. Please help me
```

sharief@sharief-laptop:~/plugins$ ./browser 
Qt for Embedded Linux data directory is not owned by user 1000
Aborted
sharief@sharief-laptop:~/plugins$ ./browser 
Qt for Embedded Linux data directory is not owned by user 1000
Aborted
sharief@sharief-laptop:~/plugins$ sudo ./browser 
QWSSocket::connectToLocalFile could not connect:: Connection refused
QWSSocket::connectToLocalFile could not connect:: Connection refused
QWSSocket::connectToLocalFile could not connect:: Connection refused
QWSSocket::connectToLocalFile could not connect:: Connection refused
QWSSocket::connectToLocalFile could not connect:: Connection refused
QWSSocket::connectToLocalFile could not connect:: Connection refused
No Qt for Embedded Linux server appears to be running.
If you want to run this program as a server,
add the "-qws" command-line option.
sharief@sharief-laptop:~/plugins$ sudo ./browser -qws
^C
sharief@sharief-laptop:~/plugins$ ./browser -qws
Qt for Embedded Linux data directory is not owned by user 1000
Aborted
sharief@sharief-laptop:~/plugins$ 

```Please help me. why it happens?

---

### Post by shariefbe on 2010-01-29
I found the answer for this. As it is a "QtEmbedded" it will play in x window. So It require virtual frame buffer. For this we have to create "/dev/f0" device. But i dont know how t o create that device.
I follwed the steps which is given below link. But i didnt get success.
[http://doc.trolltech.com/4.6/qvfb.html#running-applications-using-the-virtual-framebuffer](http://doc.trolltech.com/4.6/qvfb.html#running-applications-using-the-virtual-framebuffer)
In this link it has said the "qvfb" folder will be in /tools but i found in /"src/..../qvfs". And when i configure using "./configure -qvfb" it is getting configured but when i search for qvfb bin its not there. But i the link it has said that "./qvfb". With bin how can i do this. So confused. Please help me

---

### Post by shariefbe on 2010-02-02
Please. Can anyone tell me why my Qt browser is slow in X window. It is working fine in FB0. But when i run on X window it is slow. Can anyone tell me why it is slow?

---

