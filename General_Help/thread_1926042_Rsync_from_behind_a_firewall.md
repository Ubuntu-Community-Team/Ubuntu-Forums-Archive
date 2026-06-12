---
title: "Rsync from behind a firewall"
date: 2012-02-15
forum: General Help
---

### Post by hwttdz on 2012-02-15
I am behind a firewall which prevents me from using rsync to update a database.  I have ssh access to another machine on which a) I am root, b) rsync to this database works.  I am looking for a way that I can use an ssh tunnel to the second machine to get rsync traffic through the firewall.  Have no qualms about security, as sysadmin says he will open it in a few days, but the data would be very helpful now, and he's always busy with the filesystem/backups/queue issues, so a few days might be a month.

---

### Post by papibe on 2012-02-15
Both, the database server and the second machine are behind the firewall, but you only have ssh/rsync access to the second machine?

Did I get it right?

Once you are connected to the second machine, do you have ssh/rsync access to the database server?

Regards.

---

### Post by hwttdz on 2012-02-15
```

             firewall
                |
caerphilly <---ssh---> odysseus <---rsync---> pdb
                |

```

So I have rsync access from odysseus to the pdb.
I have ssh from caerphilly to odysseus.
I want rsync access from caerphilly to pdb.

In probably the worst move ever I started an rsync from the pdb to odysseus.  And since I have a drive on odysseus mounted on sshfs, I'm doing a "local" rsync from the sshfs drive to a drive which is really on caerphilly.  I'm still interested in knowing how to do this properly, because right now I'm relying on sshfs and two crontabs to keep everything in sync.  That and I imagine I'm slowing things down a great deal (which granted only matters this first time, but at the current rate it's going to take quite a long time).

---

### Post by papibe on 2012-02-15
You can create a tunnel by mapping ports on your ssh connection.

Open a terminal on caerphilly and run:
```
ssh -L 2222:pdb:22 odysseus
```
Wait until you get a prompt, and leave it running all the time. You are mapping the caerphilly's port 2222 to pdb's port 22.

Open a another terminal on caerphilly and run:
```
ssh -p2222 localhost
```
And you'll end up connected to pdb.

The same way you can rsync directly to pdb from caerphilly (the previous connection is not necessary):
```
 rsync -av -e "ssh -p2222"  local_dir_on_caerphilly/   localhost:remote_dir_on_pdb/
```
To terminate the port mapping just logout from the firt ssh connection.

Hope it helps, and tell us how it goes.
Regards.

---

### Post by hwttdz on 2012-02-20
Sorry to be slow in responding.

I'm not sure if it's an issue, but I don't have ssh access to the pdb, they actually have a page explaining how to download ([http://www.wwpdb.org/remediation-downloads.html](http://www.wwpdb.org/remediation-downloads.html)), which works outside this firewall.

It amounts to:
rsync -a --port=33444 ftp.wwpdb.org::ftp_data/structures/divided/pdb/ ./pdb

I did "ssh -L 33444:ftp.wwpdb.org:22 odysseus" on caerphilly to open the tunnel.

When I then did: "rsync -av -e "ssh -p33444" localhost:ftp_data/structures/divided/pdb/ pdb"
and "rsync -av -e "ssh -p33444" pdb localhost:ftp_data/structures/divided/pdb/" on caerphilly to try to grab the data (I wasn't sure of the order).  And I get a "channel 4: open failed: connect failed: Connection timed out" on the terminal that has the tunnel open. And I did once get a:

ssh_exchange_identification: Connection closed by remote host
rsync: connection unexpectedly closed (0 bytes received so far) [sender]
rsync error: unexplained error (code 255) at io.c(601) [sender=3.0.7]

On the terminal attempting to do the rsync, but really it just hangs, no output, no error message.

---

### Post by papibe on 2012-02-20
I see.

pdb doesn't provide ssh services, but a rsync daemon (note the :: syntax on the page you linked).

Unfortunately, I don't have very much experience with rsync daemons, but I think this should work:

First for the tunnel:
```
ssh -L 2222:ftp.wwpdb.org:33444 odysseus
```
You are mapping pdb's 33444 to your local por 2222.

For the final rsync connection you should use the dameon syntax ('::') instead of the typical shh connection:
```
rsync -av **[COLOR="Red"]--port=2222[/COLOR]** ./pdb   localhost**[COLOR="Red"]::[/COLOR]**ftp_data/structures/divided/pdb/
```
I haven't tried this myself, so let us know how it goes.
Regards.

---

### Post by hwttdz on 2012-02-20
To forward localhost's port 2222 to the pdb's port 33444 through odysseus:
```
ssh -L 2222:ftp.wwpdb.org:33444 odysseus
```
I should probably feed ssh the -f flag here, but I can figure that out later.

To rsync, over port 2222 (which is actually pdb's 33444) the given directory to my local ~/pdb directory:
```
rsync -av --port=2222 localhost::ftp_data/structures/divided/pdb/ ~/pdb
```

Stellar, thanks a bunch.  I also learned a bunch of other valuable tools in learning how to set this up, including autossh and reverse ssh tunnels.

---

