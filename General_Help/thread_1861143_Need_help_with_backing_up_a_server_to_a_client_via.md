---
title: "Need help with backing up a server to a client via rsync/sftp/scp"
date: 2011-10-15
forum: General Help
---

### Post by CharlesA on 2011-10-15
Hi,

I'm trying to figure out the best way to grab some files from a remote server. Basically what I want to do is to backup an sql database (which I have done, mysqldump ftw) and also backup the document roots for the sites hosted there.

I can use scp to grab the sqldump from the client, but I wanted to use rsync for the web sites since I don't want to be copying the files over and over.

I would prefer to keep all the communications on the client but I know that I could probably do this using an public key and forced commands.

Any suggestions?

Thanks,
Charles

EDIT: I think I figured it out, found the solution [here]("http://www.comentum.com/rsync.html").

```
rsync -aiv user@host:/path/to/files /path/to/destination/
```

Woot!

---

### Post by papibe on 2011-10-16
Hey CharlesA, although it seems you've solved your problem already, here's a few other tips.

If you are doing an attended rsync over a LAN, or a corporate network, that is probably all you need. In the case that the data in not that much, and connection got lost, you just run the rsync command again.

However, there a few scenarios that may need the additional considerations:
[LIST]
[*]You want to automate the transfer (unattended script).
[*]The connection to the server is over the Internet.
[*]You are transferring large amount of data, and/or the time required to transfer the data is significant.
[/LIST]

Basically you want to put yourself in the case that the rsync fails, and make the most of it. In order to minimize the time the next rsync command will take, I use the **--partial** option, that keeps partially transfer files, so the next time you run rsync it won't start from zero.

Now, to make your transfer unattended I use a script that has this general design:
```
rsync ...
until [ $? = 0 ]
do
    sleep 90
    rsync ...
done
```
In other words, I'll keep trying to transfer until rsync exits without errors.

The next tip has to do my experience transferring large amounts of data using rsync/ssh over the Internet. When you have any kind of connection problem, the transfers hangs, even by several minutes, until the connection is dropped.

What you want is tighten the standards in which the connections is made, so instead of hanging for a while, it drops quickly. I found that this ssh options works the best for me:
```
rsync -aiv -e "ssh -o TCPKeepAlive=no -o ServerAliveInterval=40" ...
```
A final note. I often transfer files from and to my brother, that is between two regular ISP clients. Long transfers will inevitable fail because of DHCP renovation. Most of the times you try to connect immediately after a dropped connection, you won't be able to connect because DNS is not able to upgrade fast enough. Thus, I wait a bit before initiating the connection again (sleep command).

That's it, I hope you find this tips helpful,
Regards.

---

### Post by CharlesA on 2011-10-16
Thank you, I didn't even think about a dropped connection, since I don't have that much data to sync (yet).

I updated my script with your suggestions. :)

---

### Post by Lars Noodén on 2011-10-16
Alternately you could use a while loop:


while ! rsync ...
do
    sleep 90
done

---

