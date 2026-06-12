---
title: "Is it possible to send a message to a computer which is connected to internet..?"
date: 2010-06-15
forum: General Help
---

### Post by karthick87 on 2010-06-15
I would like to send a pop-up message to a computer using its ip address which is connected online,how it can be done..?

---

### Post by LoneWolfJack on 2010-06-15
you will need a software that listens on the network for incoming messages.

instant messaging through MSN/ICQ is supported through pidgin by default.

---

### Post by quadproc on 2010-06-15
> **getyourkarthick said:**
> I would like to send a pop-up message to a computer using its ip address which is connected online,how it can be done..?
This would only be possible if that system (the recipient) has a port enabled to receive messages and if suitable software is running on it.  In the non-server versions of Ubuntu, no port has receive enabled by default so you would not be able to send anything to such a system.

You might be able to send to a system running Windows; I have no idea how loose the Windows environment is, but it seems likely that many people run their Windows security very loosely.  That contributes to the easy spread of viruses.

There used to be a Unix program named _talk_.  It does not appear to be part of the standard Ubuntu distribution but it may be available for download.  That program will allow two users on two different networked computers to talk to each other.  But this doesn't appear to be what you want.

If you have suitable software installed at each machine, you could use ssh to connect to the target machine and do something like create an editor on the target with a text message piped into the editor.

quadproc

---

### Post by karthick87 on 2010-06-15
What type of software is needed to run on both systems..?

---

### Post by quadproc on 2010-06-16
> **getyourkarthick said:**
> What type of software is needed to run on both systems..?
I can't speak for anything using Windows, but if both systems are running Linux or some variation of it then you would use ssh.  You also need to be able to use TCP/IP port 22 so if you have a firewall then you must enable that port for both systems.  Please note that enabling port 22 can make your system subject to infection if you don't appropriately limit access.

You can find a good article on enabling _ssh_ in an Ubuntu system [COLOR=Red][here]("http://http://www.unixtutorial.org/2009/05/ubuntu-ssh-how-to-enable-secure-shell-in-ubuntu/")[/COLOR].  That article shows you how to get the program but Ubuntu already has it present - you just need to set things up to be able to use it.

You may find that the Secure Shell program in the Ubuntu software center will work for you - I haven't tried it so I can't vouch for it.

I have also installed ssh on a Puppy Linux system and it works well there.

quadproc

---

### Post by cbrunhaver on 2010-06-16
In windows, there is at least one way communication using the messenger service (not MSN messenger).  It is used for system alerts etc., normally.

---

### Post by karthick87 on 2010-06-16
But i am using Dynamic IP..Is this matter..?

---

### Post by quadproc on 2010-06-16
> **getyourkarthick said:**
> But i am using Dynamic IP..Is this matter..?
You need to somehow specify the IP address that you wish to connect to.  If you know what the numerical address is (for example, 207.154.37.215) then you can use that directly.  If you have name (such as [email]someuser@someISP.com[/email]) then that name will have to be known to your DNS.

quadproc

---

### Post by karthick87 on 2010-06-16
Ok thank you :) but in windows i have used the [COLOR=Indigo]net send[/COLOR] command to send message to another computer.Is there any equivalent command here..

---

### Post by quadproc on 2010-06-17
> **getyourkarthick said:**
> Ok thank you :) but in windows i have used the [COLOR=Indigo]net send[/COLOR] command to send message to another computer.Is there any equivalent command here..
Since I don't do Windows I cannot say for sure, but I think that the Ubuntu _write_ command might be close to what you are describing.  _Write_ sends text to terminal window(s) at the recipient's end, provided that _mesg_ is set to yes.  If the recipient wants to respond then the recipient also needs to run _write_ in order to send things to the originator.

quadproc

---

### Post by fragos on 2010-06-17
> **quadproc said:**
> You need to somehow specify the IP address that you wish to connect to.  If you know what the numerical address is (for example, 207.154.37.215) then you can use that directly.  If you have name (such as [email]someuser@someISP.com[/email]) then that name will have to be known to your DNS.

quadproc

On your LAN you can address any computer by it's host name. My Desktop is "Geo" so other computers address it as "Geo.local" regardless of what NAT address was assigned by DCHP.

---

