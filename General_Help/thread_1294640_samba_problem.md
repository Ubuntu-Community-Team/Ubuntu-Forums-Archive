---
title: "samba problem"
date: 2009-10-18
forum: General Help
---

### Post by samkarpluk on 2009-10-18
Hello.

I am running ubuntu server v. 8.10 for the simple purpose of sharing out a network drive full of music and running the Squeezebox Server software. I setup a simple samba file server based on the how-to found here: [http://www.howtoforge.com/ubuntu-home-fileserver-p2](http://www.howtoforge.com/ubuntu-home-fileserver-p2) This was working for some time but is no longer. I cannot see the share any longer on the network and even from the server itself. When I enter the following command from the terminal:

>smbclient [hostname]

It yields the following: 

Connection to [hostname] failed (Error NT_STATUS_CONNECTION_REFUSED)

I'm running samba version 3.2.3

I'm looking for some troubleshooting assistance. Thanks in advance for any help you can give me.

samk

---

### Post by P4man on 2009-10-19
does it work using IP address or localhost ?

---

### Post by samkarpluk on 2009-10-19
> **P4man said:**
> does it work using IP address or localhost ?

No, neither works.

---

### Post by samkarpluk on 2009-10-25
Here's what I've found out. For some reason I need to restart the server when I make changes to smb.conf. If I simply do a /etc/init.d/samba restart, then I cannot connect using smbclient. If i reboot the server, then I can connect.

SO that's one issue. 

The bigger issue is that even with the reboot, the windows machines on this network cannot connect to the shared directory, which is the reason I am posting here. I need some assistance getting the samba share working again (as it was for a long time - not sure what's changed).

Here is what I get when I connect to the samba server's ip:

$smbclient -L 192.168.1.5

Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.2.3]

        Sharename       Type      Comment
        ---------       ----      -------
        print$          Disk      Printer Drivers
        public_hard_disk Disk      Public Folder
        IPC$            IPC       IPC Service (martinserver server (Samba, Ubuntu))
Anonymous login successful
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.2.3]

        Server               Comment
        ---------            -------
        MAINFLOOR            
        MARTINSERVER         martinserver server (Samba, Ubuntu)

        Workgroup            Master
        ---------            -------
        WORKGROUP            MARTINSERVER

And here's what i get when I try to access the public_hard_disk on martinserver:

peter@martinserver:~$ smbclient \\\\martinserver\\public_hard_disk
Enter peter's password: 
Anonymous login successful
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.2.3]
Receiving SMB: Server stopped responding
tree connect failed: Call timed out: server did not respond after 20000 milliseconds

Looking in the error log, it shows this at the top of the log:

*** glibc detected *** /usr/sbin/smbd: free(): invalid next size (fast): 0xb862dee0 ***

and then a backtrace...

Any thoughts or advice?

---

