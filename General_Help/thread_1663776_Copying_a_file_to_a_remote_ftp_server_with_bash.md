---
title: "Copying a file to a remote ftp server with bash"
date: 2011-01-10
forum: General Help
---

### Post by themusicalduck on 2011-01-10
I'm hoping to set up a cron job that takes a file and copies it to a remote password protected FTP server. I've got a command that formats the file with the correct name and I've put it in the anacron file in /etc/cron.d (which I think is right, haven't tested it yet).

I'm not sure how to copy the file to a remote server though. I do actually have the ftp server bookmarked in my places menu. So is there a simple way of suppling a file path that will put it straight into that folder? The only problem I can see with this is that the connection won't be open continuously, so would need to be re-opened when needed (I could presumably save the password in the keyring so that I don't need to be there to type it in).

Or maybe set up a cron job that connects to and mounts the ftp server a minute before it has to copy the file over?

---

### Post by tredegar on 2011-01-10
My suggestion:

Setup **ssh** for public / private key based logins (no password needed, more secure than a password). A HOWTO is [here]("http://www.linux.com/archive/feed/34958")

Then just use **scp** to copy the file
**/usr/bin/scp sourcefile user@server:/path/to/destination/**

---

### Post by themusicalduck on 2011-01-10
That sounds brilliant, but I don't have ssh access to this server, unfortunately FTP only :(

---

### Post by tredegar on 2011-01-10
No **ssh** ?
For a _server_ ???
How can you securely manage a server without **ssh** ?
Please don't tell be you are using **telnet** !
Can't you install **ssh** or ask for it to be installed ?

---

### Post by themusicalduck on 2011-01-10
I'll clarify my post a little!

I'm not actually managing a server myself. I have just bought some space on a shared server from web hosting company. If I want SSH access then I'd have to pay a lot more and get a VPS or dedicated.

Most of the management is done through cpanel and FTP software. I've created an extra folder on my space and associated an FTP account with it. I'm just hoping that there is a way of automating the copying of a file to that FTP account so I don't have to do it manually each day.

---

### Post by mickwombat on 2011-01-10
Save the script below and change to your needs.  Make it executable and run as a cron job.

```
#!/bin/sh
USERNAME="username"
PASSWORD="password"
SERVER="hostname or ip here"
# Directory where file is located
DIR="/some/directory"
#  Filename of backup file to be transfered
FILE="filename"
# login to ftp server and transfer file
cd $DIR
ftp -n -i $SERVER <<EOF
user $USERNAME $PASSWORD
binary
mput $FILE
quit
EOF
# End of script
```

---

### Post by Cheesehead on 2011-01-10
If you have curl installed, it also uploads by FTP.
I use it to upload regularly to my rented host.
(I really like mickwombat's script, though)
If you need something that fits onto one line (for example, for use as a .bashrc alias or a cron job), this can be a convenient way to do it.

```
# The next 9 lines are lifted from mickwombat's script 
#!/bin/sh
USERNAME="username"
PASSWORD="password"
SERVER="hostname or ip here"
# Directory where file is located
DIR="/some/directory"
#  Filename of backup file to be transfered
FILE="filename"
# login to ftp server and transfer file

curl -T $FILE -u $USERNAME:$PASSWORD $SERVER/$DIR

```

-T is the Upload flag.
-u is the user authentication flag.

---

### Post by themusicalduck on 2011-01-11
Thanks for your efforts both. That curl line looks perfect, but every time I run it it tells me I don't have permission to upload to the server and gives me a 403 forbidden message.

Now I would've thought I must be putting something wrong in to get this kind of error, but I've tried connecting using a few different accounts and I've been double checking all of my details and tried every combination possible with no luck.

Is there any other reason why this would happen?

---

### Post by HermanAB on 2011-01-11
Howdy,

Here is another guide that explains how to script an FTP session:
[http://www.aeronetworks.ca/howtos/windows-backup.html](http://www.aeronetworks.ca/howtos/windows-backup.html)

---

### Post by themusicalduck on 2011-01-11
Thanks again all. After a bit more fiddling with scripts I have managed to put something together that so far is working nicely. :D

---

