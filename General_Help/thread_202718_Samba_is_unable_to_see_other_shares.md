---
title: "Samba is unable to see other shares"
date: 2006-06-23
forum: General Help
---

### Post by Skye on 2006-06-23
Hi everyone!

I'm helping a friend to install linux for the first time, (quite a change from windows ME, isn't it?) and we've run into a bit of a problem.  Samba on her computer (called vega) is unable to see one of the computers on her network, and the other computer on her network won't allow her to connect, even though it's visible.  It works the same way in reverse- the computer that vega can see can see vega in return, but not connect, and the computer that can't be seen by vega can't connect.

The smb.conf is as follows:
```

[global]
        use spnego = no
        log file = /var/log/samba/log.%m
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spa$        
	obey pam restrictions = yes
        socket options = TCP_NODELAY
        encrypt passwords = yes
        passdb backend = tdbsam guest
        passwd program = /usr/bin/passwd %u
        dns proxy = no
        netbios name = Vega
        server string = Vega
        invalid users = root
        workgroup = MSHOME
        os level = 20
        syslog = 0
        panic action = /usr/share/samba/panic-action %d
        max log size = 1000

[Shared]
        root postexec = chmod -R 777
        writeable = yes
        path = /home/lexi/Shared
        write list = lexi
        force directory mode = 777
        force create mode = 777
        hide dot files = no
        comment = Shared Files on Lexi's Computer
        valid users = lexi
        create mode = 777
        directory mode = 777
        case sensitive = yes

```

It's not a real secure setup, but this is a home machine connecting only to her family's computers with a hardware firewall, so I think it's ok.

The computer that can be seen from the Places -> Network Servers menu but cannot be accessed gives the error *'Sorry, couldn't display all the contents of "Windows Network: sagittarius"'*.

At first, this screamed "firewall problem" to be, but we tried disabling the windows firewall and Norton on the invisble computer, and it did nothing in either direction.  I haven't tried messing with the firewall on the other computer

So, our questions are as follows:
1- Why can one computer be seen/see vega?
2- Why can't we access the one visible computer/access vega?
3- Why does the login to the linux machine fail from the other computer?

We appreciate the help!

---

### Post by bforbes on 2006-06-24
Try adding:
```

    guest ok = yes

```
to the smb.conf entries.

Are you sure you've added all the appropriate usernames?

---

### Post by Skye on 2006-06-24
No, I'm not sure that I've added any usernames at all- it's been quite awhile since I set up samba.  How would I go about adding those usernames?

---

### Post by Stormbringer on 2006-06-24
> 1- Why can one computer be seen/see vega?

Make sure the computer is in the right workgroup (you called it "MSHOME" in your sample above).

> 2- Why can't we access the one visible computer/access vega?
> 3- Why does the login to the linux machine fail from the other computer?

Both questions have one answer: You need to give users explicit access to samba by following these steps (alternatively take a look at the HOWTO I linked in my signature):

First you need to add the username to the system --- open a terminal ...

Example - adjust it to your needs

# sudo useradd -s /bin/true skye
password: <enter your passward>

Now add the user to samba

# sudo smbpasswd -L -a skye
# sudo smbpasswd -L -e skye

That's it.

If possible disable firewall services on both computers (if you're inside a LAN behind a hardware router or firewalling server) or configure a pass-through rule in your firewall for ports 137,138,139,420 TCP/UDP.

---

### Post by Skye on 2006-06-24
Thanks for the help, and the link.  As soon as I have access to that other PC, I'll try implementing that stuff.

One quick question, though.  When you say add users, should the usernames being added be users on the remote windows machines, or the local Linux box?

And also, will this fix the problem of some of the other computers not being able to see the linux computer at all?

---

### Post by Stormbringer on 2006-06-24
[QUOTE="Syke"]One quick question, though. When you say add users, should the usernames being added be users on the remote windows machines, or the local Linux box?[/QUOTE]

I'm refering to the user that's configured on Windows ... you need to add the very same useraccount (the Name you use for login) with the very same password to your linux box.

If you need to access a share on the Windows box from Linux the same is true - you need to add the useraccount of your Linux box to Windows.

[QUOTE="Syke"]also, will this fix the problem of some of the other computers not being able to see the linux computer at all?[/QUOTE]

As I wrote - both computers need to be in the same workgroup and the user accounts have to be setup. In the moment everything is configured correctly your Windows box should be able to see the Linux box in "Network Places".

---

### Post by bforbes on 2006-06-24
[QUOTE=Stormbringer]If you need to access a share on the Windows box from Linux the same is true - you need to add the useraccount of your Linux box to Windows.
[/QUOTE]

Not true, I haven't had to do that. But I did have to make sure there was a Linux account so that the Windows box could access the Linux box.

---

