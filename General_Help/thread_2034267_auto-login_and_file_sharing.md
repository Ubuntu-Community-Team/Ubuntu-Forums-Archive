---
title: "auto-login and file sharing"
date: 2012-07-28
forum: General Help
---

### Post by rocky289 on 2012-07-28
Hi
New user here.
 
Hope I am posting in the right place.
 
Have installed Lubuntu (Alternate) on a old Pentium III
Couple of questions:
Can I get rid of the logon & password thingy?
Also is it possible to set this up for file sharing with other windows pc's on my home network?

---

### Post by tartalo on 2012-07-28
[https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides#How_to_enable_automatic_logon](https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides#How_to_enable_automatic_logon)

---

### Post by Lars Noodén on 2012-07-28
Welcome to Lubuntu.  

Autologin is an option given in the desktop/live install disc.  If you used the alternate image, then you can add autologin after the fact.  The file to edit is lxdm.conf and it is buried in /etc/xdg/lubuntu/lxdm/ Add to it the following line, modified for your actual user name:

```

autologin=rocky289

```

---

### Post by Lars Noodén on 2012-07-28
For file sharing you have several options.  The two that might be best to consider would be Samba and SSHFS.  You can use either or both.  Samba is better suited to sharing to Windows and Linux machines, but only on the same LAN.  If you are sharing across WAN, then you might want to consider SSHFS, though it also works for LAN sharing, too.

[https://help.ubuntu.com/community/Samba/](https://help.ubuntu.com/community/Samba/)
[https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)

---

### Post by rocky289 on 2012-07-29
Thanks for that information.
I will work my way through that.
I am an old dog, but I like learning new tricks.

---

### Post by Lars Noodén on 2012-07-29
> **Lars Noodén said:**
> Welcome to Lubuntu.  

[s]Autologin is an option given in the desktop/live install disc.  If you used the alternate image, then you can add autologin after the fact.  The file to edit is lxdm.conf and it is buried in /etc/xdg/lubuntu/lxdm/ Add to it the following line, modified for your actual user name:

```

autologin=rocky289

```[/s]

If I recall correctly, that was how I did it with 11.10.  Looking at 12.10-Alpha3, the way to do it has changed.  In the new version, the file /etc/lightdm/lightdm.conf needs the following lines:

```

[SeatDefaults]
autologin-user=rocky289
autologin-user-timeout=0

```

---

### Post by rocky289 on 2012-07-29
I am not having much luck with the login thing.
Do I open that file in the LXTerminal & edit it there or somewhere else & paste it in there.
I havent even managed to open the file yet.

---

### Post by kalehrl on 2012-07-30
Type in terminal:

```
 sudo nano /etc/lightdm/lightdm.conf
```

Put your user in place of <YOUR USER>

```
autologin-user=<YOUR USER>
```

---

### Post by rocky289 on 2012-07-30
Thank you.
I can now log in with out a password.
Can I also get rid of the login prompt & having to use the password to make changes.
Havent attempted the networking yet, thought I'd get this sorted first.

---

### Post by rocky289 on 2012-07-31
Ok now trying to set up file sharing.
Keep getting this prompt for password to Authenticate.
I am an old fart with fat fumbling fingers.
How can I get rid of that.

---

### Post by Lars Noodén on 2012-08-01
Which method are you trying for file sharing?  It is probably better to start a new thread about it.

---

### Post by m3n3chm0 on 2012-08-10
> **kalehrl said:**
> Type in terminal:

```
 sudo nano /etc/lightdm/lightdm.conf
```Put your user in place of <YOUR USER>

```
autologin-user=<YOUR USER>
```


Dear all.. does it work for ubuntu 12.04 and Gnome-shell ¿?¿?

---

### Post by rocky289 on 2012-08-13
Thank you for your help.
 
I am slowly getting more familiar with this os.
Have got the network & file share sorted.
 
I have 2 more questions:
1/ How can I get a shortcut to the Network Drives, onto the desktop.
2/ How can I bipass the logon screen.

---

