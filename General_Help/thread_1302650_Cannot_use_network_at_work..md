---
title: "Cannot use network at work."
date: 2009-10-27
forum: General Help
---

### Post by Toke on 2009-10-27
I work on a ship and bring my laptop along as it is a lot more convenient than the one in my cabin.
The internet works simply by plugging in the cable and does not appear to have anything to do with the server.
Yesterday I figured out how to connect to one of the network printers. Now I wonder if there is a way to access the files on the shared drives?

Another tread mentioned this smbclient command, it does look like my laptop can see the network, but not any of the drives.


> toke@Toke-laptop:~$ smbclient -L //10.10.29.164
Enter toke's password: 
Anonymous login successful
Domain=[TOR-ANGLIA] OS=[Windows Server 2003 3790 Service Pack 2] Server=[Windows Server 2003 5.2]

    Sharename       Type      Comment
    ---------       ----      -------
Error returning browse list: NT_STATUS_ACCESS_DENIED
session request to 10.10.29.164 failed (Called name not present)
session request to 10 failed (Called name not present)
Anonymous login successful
Domain=[TOR-ANGLIA] OS=[Windows Server 2003 3790 Service Pack 2] Server=[Windows Server 2003 5.2]

    Server               Comment
    ---------            -------

    Workgroup            Master
    ---------            -------
toke@Toke-laptop:~$ 


---

### Post by Giblet5 on 2009-10-27
The remote server doesn't permit open browsing.

[Here's a How-To]("http://tldp.org/HOWTO/SMB-HOWTO-8.html") that helped me.

---

### Post by Toke on 2009-10-27
Thanks, I am not sure what happened it ended up with a blinking >.
Next thing I tried to connect again under places>network and used a list I found with the autorised users and paswords. One of the computers is not in use, so I am currently using it's name.

Cool.

---

