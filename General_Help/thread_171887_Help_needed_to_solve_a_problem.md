---
title: "Help needed to solve a problem"
date: 2006-05-07
forum: General Help
---

### Post by jdm2 on 2006-05-07
Note:  Before I begin your kind heart thoughts and messages are welcome but if possible please keep them out of this thread.  Thanks you in advance.  

My grandma just past away and I will be going up to her house this summer because my dad and aunt needs to take care of the things.  I'm new to linux and ubuntu but I want to be able to work on it but I don't think my parents want me to drag it from one place to the other.  I would like to be able to access it from a windows xp home machine so I can mess with it.  I would like you to help me get this setup or lead me in the right direction.  Thank you

---

### Post by elamericano on 2006-05-07
Are you wanting to remotely access your current Ubuntu computer, or will this be a new computer and you want the option to boot either one when you turn the computer on?

---

### Post by jdm2 on 2006-05-07
I will be using a pc at my grandma's house running xp home and I want to access the ubuntu partion here at home.  My pc with ubuntu on it is a dual boot pc that has xp home and ubuntu on it.  If the way to access it is remote desktop then yes.

---

### Post by Face1 on 2006-05-07
you can install the ssh server (search in synaptic) on your ubuntu computer, and then you can install the free program [PuTTY]("http://www.chiark.greenend.org.uk/~sgtatham/putty/") on the windows box.  That way, you can get a shell on the windows computer that might as well actually be on the linux computer.  Additionally, you can install [Cygwin/X]("http://x.cygwin.com/") on the windows computer, which will allow you to run gui programs over SSH.

---

### Post by jdm2 on 2006-05-07
Is there a guide or faqs on doing a remote desktop for linux or ssh?  Thanks

---

### Post by Face1 on 2006-05-07
[QUOTE=jdm2]Is there a guide or faqs on doing a remote desktop for linux or ssh?  Thanks[/QUOTE]
Setting up ssh is really very simple, the only steps are the ones that I listed.  The ssh server has a very adequate default setup so that doesn't matter.  PuTTY is very easy to setup on a windows machine (it uses a normal windows installer).  Cygwin/X is a tad trickier, but there's a pretty good instruction set on the Cygwin website.  

Once Cygwin/X is properly setup, the only thing you need to make sure to do is change the one setting in PuTTY to allow X to export the display across ssh, which is somewhere in advanced options...If you look through them you can't miss it.

---

### Post by jdm2 on 2006-05-07
Thanks for the help.  Lets see if i got this right install ssh on the ubuntu machine and use putty and cygwin on the windows machine.  I use putty to login remotely and cygwin for x session.  I hope I got it right.

---

### Post by jdm2 on 2006-05-08
I want to remote login with me being able to see the screen as if I'm right in front of it not in a terminal.  I want something like gotomypc program but free or a server that will do that for me.

---

### Post by the_tiger on 2006-05-08
Try this
[http://www.ubuntuforums.org/showthread.php?t=172190](http://www.ubuntuforums.org/showthread.php?t=172190)

Always try searching the official wiki for advice.

---

### Post by elamericano on 2006-05-09
Or you can run vncserver on your Ubuntu box and access it with a VNC client from Windows (e.g. RealVNC) You did say remote desktop...

Oh wait, that was the link. Why didn't you say so? :confused: 

I love VNC. I use it everywhere. I only wish that Ubuntu had a better VNC client available. Scaling is so much better than scrolling.

---

### Post by jdm2 on 2006-05-09
So I could install a vnc server on my ubuntu machine and the client on another computer and I could remote access it but do I have to be on my network or can I be on anybodyies network with the client software?  Thanks

---

### Post by the_tiger on 2006-05-09
You can be on anybodys network so long as you open the correct ports to your server for vnc and ssh.

---

### Post by jdm2 on 2006-05-09
Thanks
I think I understand it now except for which ones the easiest for newbies to linux and ubuntu and should I do ssh and vnc or just one of them.

---

