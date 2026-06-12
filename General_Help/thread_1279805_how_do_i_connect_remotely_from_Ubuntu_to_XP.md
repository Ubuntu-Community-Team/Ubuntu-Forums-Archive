---
title: "how do i connect remotely from Ubuntu to XP"
date: 2009-10-01
forum: General Help
---

### Post by TDKING on 2009-10-01
Hey guys can someone tell me how i can connect to my freinds computer using remote desktop ? i am on ubuntu and he is on xp

---

### Post by karlson on 2009-10-01
> **tdking said:**
> hey guys can someone tell me how i can connect to my freinds computer using remote desktop ? I am on ubuntu and he is on xp

tsclient

---

### Post by TDKING on 2009-10-01
will we both have that ? how can we set this up could you possibly give me more info

---

### Post by mikewhatever on 2009-10-01
Pls, use descriptive thread titles.:icon_frown:

---

### Post by TDKING on 2009-10-01
i will use more decriptive ones in future i do appologise

---

### Post by badger_fruit on 2009-10-01
> **TDKING said:**
> will we both have that ? how can we set this up could you possibly give me more info

Install the TSCLIENT onto the Ubuntu Machine
On the windows computer (or remote-firewall), ensure that port number 3389 is opened and forwarded to the local IP address of the windows computer.
Tell your friend to use his Windows PC and browse to [www.whatismyipaddress.com](www.whatismyipaddress.com)

This will give his "Public" IP address.

You then run tsclient from your Ubuntu machine and in the IP address or computer name field, enter his public IP address, select "RDP" for protocol and click connect.

It should then hook you into his PC but bear in mind, remote-desktop will blank or lock his screen, he won't be able to use the PC at the same time as you.

If you want "shared" access, tell him to install VNC onto his PC.
You then use TSClient as above but in the protocol, use VNC.

VNC uses TCP ports 5800 and 5900
RDP uses TCP port 3389.

I hope this helps.

---

### Post by TDKING on 2009-10-01
ho do i get him to change his port number or check this ?  he is using xp home if that makes a difference?

---

### Post by prem1er on 2009-10-01
> **TDKING said:**
> ho do i get him to change his port number or check this ?  he is using xp home if that makes a difference?

He doesn't need to change his port number, he only has to make sure the correct port is forwarded from his router to the LAN IP address.

---

### Post by TDKING on 2009-10-01
i have tried doing it that way and it wont so got him to install vnc on his machine could some one talk me through connecting to his machine as i dont know what to put in all the feilds


like the feilds its asking me for are 
Computer :
protocol:
username:
password : blanked out
Domain:
Client Hostname:
Protocol File:

---

### Post by Gernot74 on 2009-10-01
Windows Home Versions do NOT have a Remote Desktop option.

unless you have Win XP Pro on the other side, you will not be able to use this.

---

### Post by TDKING on 2009-10-03
Where going to do it through vnc 

just need some help with getting it all set up please can someone help me :)

---

### Post by akakingess on 2009-10-03
I don't know that we here will have those answers for you, but Computer, should put in the "public" IP address that your buddy got from [www.whatismyipaddress.com](www.whatismyipaddress.com) as mentioned earlier, username and password should be what your buddies username and password are (I believe) and protocol will now be VNC. I would highly suggest reading the docs with the VNC software for the answers as to what they want for each field.

---

