---
title: "Samba will not connect."
date: 2012-09-14
forum: General Help
---

### Post by MrWestwood on 2012-09-14
I have a clean install of 12.04 and I wish to connect to my CentOS fileserver via Samba. I previously ran 10.04 and it connected perfectly. Now, on 12.04, all I get is the username and password prompt. 

Is anyone else suffering from this? Is there a fix? It's really getting tedious now. I'm considering going back to Windows.

---

### Post by MrWestwood on 2012-09-14
Anyone? I would really appreciate some help here.

---

### Post by SlugSlug on 2012-09-14
have you filled al the boxes in correctly - if I remember right you need a / in path or folder I forget which

& due to knowing said CentOS box ;) you need your username like domain\user

---

### Post by SlugSlug on 2012-09-14
> **MrWestwood said:**
>  I'm considering going back to Windows.


pfft

---

### Post by MrWestwood on 2012-09-14
> **SlugSlug said:**
> have you filled al the boxes in correctly - if I remember right you need a / in path or folder I forget which

& due to knowing said CentOS box ;) you need your username like domain\user

Done all of that. It's horribly wrong. 12.04 is really annoying me at present.

---

### Post by MrWestwood on 2012-09-14
> **SlugSlug said:**
> pfft

You know how much I love Ubuntu but 12.04 is crap in many ways. Have you read my thread about the aptd crash I get every time I boot my home PC?

I just can't be bothered with it lately.

---

### Post by MrWestwood on 2012-09-14
Forgto to add. It's the gui connection in Nautilus and I keep getting prompted for username and password all the time.

---

### Post by SlugSlug on 2012-09-14
try this
[http://askubuntu.com/questions/128393/how-do-i-mount-an-active-directory-windows-share](http://askubuntu.com/questions/128393/how-do-i-mount-an-active-directory-windows-share)

I agree on 12.04 mate - it's gutting  :(

Have you tried any other DE?

---

### Post by MrWestwood on 2012-09-14
> **SlugSlug said:**
> try this
[http://askubuntu.com/questions/128393/how-do-i-mount-an-active-directory-windows-share](http://askubuntu.com/questions/128393/how-do-i-mount-an-active-directory-windows-share)

I agree on 12.04 mate - it's gutting  :(

Have you tried any other DE?

Doesn't work fella. I wouldn't mind if I was trying to connect to a Windows machine but I'm trying to connect to a CentOS server. Every other piece of software, even my Android mobile can connect but 12.04, nothing.

I'm not sure how they expect it to get a share. 

Any suggestions for another distribution? 

I may just try Debian. If I get time I might play at weekend. 12.04 has really taken the fun out of Ubuntu.

---

### Post by SlugSlug on 2012-09-14
can you see anything in the smb logs on both server and client

---

### Post by Morbius1 on 2012-09-14
Crikey, 

Run the following command on your Ubuntu machine:
```
testparm -sv | grep encrypt
```
If you get back this:
> encrypt passwords = No
Fix it:

Edit /etc/samba/smb.conf as root and find the " encrypt passwords = No" line and change No to Yes. Restart smbd if you have samba installed.

---

### Post by MrWestwood on 2012-09-14
> **Morbius1 said:**
> Crikey, 

Run the following command on your Ubuntu machine:
```
testparm -sv | grep encrypt
```If you get back this:

Fix it:

Edit /etc/samba/smb.conf as root and find the " encrypt passwords = No" line and change No to Yes. Restart smbd if you have samba installed.

Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_DOMAIN_MEMBER
    encrypt passwords = Yes
    cups encrypt = No
    smb encrypt = auto


I get that back pal.

---

### Post by MrWestwood on 2012-09-14
> **SlugSlug said:**
> can you see anything in the smb logs on both server and client

From the log for today and yesterday. I didn't bother trying to connect yesterday.

[2012/09/13 14:01:26,  0] smbd/server.c:1051(main)
  smbd version 3.6.3 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2011
[2012/09/13 14:01:26.214747,  0] smbd/server.c:1107(main)
  standard input is not a socket, assuming -D option
[2012/09/14 12:20:30,  0] smbd/server.c:1051(main)
  smbd version 3.6.3 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2011
[2012/09/14 12:20:30,  0] param/loadparm.c:7969(lp_do_parameter)
  Ignoring unknown parameter "client ntlmv auth"
[2012/09/14 12:20:30.472347,  0] param/loadparm.c:7969(lp_do_parameter)
  Ignoring unknown parameter "client ntlmv auth"
[2012/09/14 12:20:30.473610,  0] smbd/server.c:1107(main)
  standard input is not a socket, assuming -D option

Looking at the CentOS Fileserver, there are no entries in the log for the times listed above. I find that strange as I am constantly prompted for username and password.

The problem has to be something in 12.04 as 10.04 and everything else connects.

Work are said to be buying me a lappy with Windows. I love Ubuntu but this is just silly. Forgive me guys, I'm feeling quite negative today.

---

### Post by SlugSlug on 2012-09-14
found this

in /etc/samba/smb.conf add the following to the bottom of the [global] section:  client lanman auth = yes client ntlmv2 auth = no

---

### Post by MrWestwood on 2012-09-14
> **SlugSlug said:**
> found this

in /etc/samba/smb.conf add the following to the bottom of the [global] section:  client lanman auth = yes client ntlmv2 auth = no

Tried all of that earlier fella.

The only other message in my machine's log is: 

[2012/09/14 13:38:48.647872,  0] smbd/server.c:1107(main
)
  standard input is not a socket, assuming -D option

---

### Post by SlugSlug on 2012-09-14
u sure your filling the boxes in right?

it might need /shared in folder box

---

### Post by Morbius1 on 2012-09-14
** How long before you told us about this:
> Server role: ROLE_DOMAIN_MEMBER** More importantly: When do you expect to receive your Windows Laptop.

** I am not your pal.

---

### Post by MrWestwood on 2012-09-14
> **SlugSlug said:**
> u sure your filling the boxes in right?

it might need /shared in folder box

There's three boxes on Nautilus connect. It hasn't changed. It asks for username, domain and password. I check the remember password forever box and it just keeps bringing the box up.

---

### Post by MrWestwood on 2012-09-14
> **Morbius1 said:**
> ** How long before you told us about this:


In that post, what relevance does it have? It's the default samba config.

> **Morbius1 said:**
> 
** More importantly: When do you expect to receive your Windows Laptop.


Knowing my employer, after 12 meetings between finance, the technical director and whoever else wants to have a go. It will then sit on the MDs desk until he stops acting like a baby with a slapped **** and decides that in order for staff to function correctly, they need the correct tools.

> **Morbius1 said:**
> 
** I am not your pal.

My apologies, I was rolling off and it popped out. Wouldn't want to upset one with informalities.

---

### Post by SlugSlug on 2012-09-14
when you first click connect to server there should be some boxes asking server and folder 

am pretty sure its that folder box thats screwing you

---

### Post by MrWestwood on 2012-09-14
> **SlugSlug said:**
> when you first click connect to server there should be some boxes asking server and folder 

am pretty sure its that folder box thats screwing you

Just realised you and I don't connect the same way. I have just tried your way and now it just says verify password. Even though password is there and verified.

---

### Post by SlugSlug on 2012-09-14
> **MrWestwood said:**
> Just realised you and I don't connect the same way. I have just tried your way and now it just says verify password. Even though password is there and verified.


yer i go to places > connect to server

in there theres some boxes to fill am sure I've had this issue due to not filling that box in right it needs a shared folder or something  or maybe the path box :)

---

### Post by MrWestwood on 2012-09-14
> **SlugSlug said:**
> yer i go to places > connect to server

in there theres some boxes to fill am sure I've had this issue due to not filling that box in right it needs a shared folder or something  or maybe the path box :)

Cheers for your help pal. ;)

I will leave it for now. 12.04 has already wrecked enough of my productivity for today.

I seem to be aggravating users too. I'll look into it after the weekend when I have time.

---

### Post by SlugSlug on 2012-09-14
if I didn't have all that jazz with email server web etc etc i'd flatten 12.05 and put 10.04 back on

---

### Post by MrWestwood on 2012-09-14
> **SlugSlug said:**
> if I didn't have all that jazz with email server web etc etc i'd flatten 12.05 and put 10.04 back on

That's what I'm thinking at the moment for my home machine. I get the strangest error with /usr/sbin/aptd on that one. Apparently there's a dist upgrade available and it broke during install. I get that error everytime I boot up. Again, fresh install with just a few standard bits of software (From the repos) installed.

---

