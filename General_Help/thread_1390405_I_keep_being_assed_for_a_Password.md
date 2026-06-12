---
title: "I keep being assed for a Password"
date: 2010-01-25
forum: General Help
---

### Post by the lemming on 2010-01-25
I have two computers that are connected to a router so that I can go onto the internet.  Nothing unusual there as I'm guessing that many on here have the same sort of setup, or there abouts.

One is a desktop computer which runs Windows 7 while the other is a laptop that dual boots Vista and Ubuntu.  When I boot the computers into Vista and Windows 7, both computers can see eachother and I can freely listen to music, movies and generally swap files from each computer.

Unfortunately I can not do the same when I boot the laptop into Ubuntu.  When the laptop is booted into Ubuntu I can see the Windows 7 desktop on my Ubuntu laptop as an icon, but that's it.

Once I try to click on the icon of my Windows computer I keep being asked for a password.  The problem is that there is no password to use.  In Windows, I disable that feature.

Anybody know what I must do so that my Ubuntu laptop can see my Windows computer and let me watch movies and music from that computer?

Any help or advice would be very much appreciated.

---

### Post by doas777 on 2010-01-25
if the password is in fact blank on windows, then you should be able to put in a username (the one of a windows user) and hit enter (with a blank password).

---

### Post by Monotoko on 2010-01-25
if that doesnt work, set a password :P

---

### Post by the lemming on 2010-01-26
Any other suggestions would be a great help.

Cheers

---

### Post by killiekosmos on 2010-01-26
I'm having a similar problem [http://ubuntuforums.org/showthread.php?t=1390491](http://ubuntuforums.org/showthread.php?t=1390491)
 
Unfortunately I'm no where near a solution.

---

### Post by Ryan Dwyer on 2010-01-26
Check the event log in Windows. I think Windows might be trying to use the Guest account, but it's disabled. Sometimes even enabling the account isn't enough - there's a setting in the local security policy or somewhere that denies Guest the ability to logon from the network.

---

### Post by doas777 on 2010-01-26
> **Ryan Dwyer said:**
> Check the event log in Windows. I think Windows might be trying to use the Guest account, but it's disabled. Sometimes even enabling the account isn't enough - there's a setting in the local security policy or somewhere that denies Guest the ability to logon from the network.

it's in secpol.msc under user rights assignments.

Op, you probably are better off setting a password, and then telling ubuntu to remember it.

---

### Post by 3rdalbum on 2010-01-26
I think I've encountered this before, but I assumed I must have set things up wrong. It's not limited to Ubuntu as client, BTW.

You may need to type in the server's name and the share name into Nautilus. Hit Control-L in your file manager and type it in, in this format:

```
smb://computername/sharename/
```

For instance, my server is called "chris-server" and the share is called "new":

```
smb://chris-server/new/
```

---

### Post by the lemming on 2010-01-26
Just as a side note, which may or may not be relevant, I tried to look at my own ubuntu laptop on the network and could not even do that.

Is it possible not to even see my own computer, which I am using at the time to access it via the network?

I'm guessing that I do NOT have things set up correctly.

Funny thing is that when I was using Vista and Linux, the whole process took minutes to set up.

What's gone wrong?

Me or Windows7?

---

### Post by the lemming on 2010-01-28
Still working on getting my Linux box to work with the Windows 7 box and was chatting to a chap down at the local climbing wall, who really does know his stuff. The problem is I could not remember everything that he said.

The gist of the problem is that there is an issue with windows 7 playing nicely with Linux. There's a surprise however there is a work around.

I know that I need to use Samba but I also need to do something that involves, and this is the bit where my brain went fuzzy, a SMB.confg file. And that is all I know.

I'd appreciate any help or advice on what a SMB.confg is and how I get it working.

Cheers

---

### Post by killiekosmos on 2010-02-08
I found a solution!  On Win 7 delete the Windos Live ID login assistant.

---

### Post by poohter on 2010-02-08
> **killiekosmos said:**
> I found a solution!  On Win 7 delete the Windos Live ID login assistant.

Good to see you got it worked out and it quit assing you.:D

---

### Post by the lemming on 2010-02-08
> **killiekosmos said:**
> I found a solution!  On Win 7 delete the Windos Live ID login assistant.



Once I work out what Windows Live ID log-in is I will delete it.

Cheers

---

