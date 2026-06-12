---
title: "Mirroring a Web Server (Easy for YOU, hard for ME!)"
date: 2010-06-30
forum: General Help
---

### Post by chowanec on 2010-06-30
Hey all,

I realize this will go down in the record books as trivial in the end, but given the importance of what I am working with here, I'd rather not destroy 5 years worth of database by screwing around to learn how to do this on my own.  Hence, I come to you, the far more intelligent masses... :)

I have a website that I SSH into all the time.  I'd like to:
1) Mount the website as a local file system.  I think I can use SSHFS for this?
2) Syncronize (in a Webserver -> local filesystem) nightly

Now on step 2 -- I just want to get what has changed on the server every night.  I'm not interested in two-way syncronicity.  Effectively, I want my local file system to mirror the entire website as a poor-man's backup.

I've read about rsync, but I'm scared to experiment. :)

Now -- can you folks help me? :)

Thanks.

-Chow

---

### Post by bodhi.zazen on 2010-06-30
sshfs and rsync sound perfect for what you are describing.

[http://embraceubuntu.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/](http://embraceubuntu.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/)

[http://sial.org/howto/rsync/](http://sial.org/howto/rsync/)

[http://everythinglinux.org/rsync/](http://everythinglinux.org/rsync/)

---

### Post by chowanec on 2010-07-04
Having trouble just with the SSHFS mount right now.  I am trying to get it to be read only:

Setting up the mountpoint
```

mkdir ~/Website/
chown chow:chow ~/Website/
chmod 755 ~/Website/

```

And the SSHFS mount (website obscured for obvious reasons):
```

sshfs -o idmap=user -o umask=400 user@example.com:public_html/ /home/chow/Website/

```

The mount will work and I can cd into Website/ and see all the files.  However, I am trying to get it to be READ only and when I do this, the files are all -wx-wx-wx (666?).  I can make directories, create/destroy files, etc.  This is what I am trying to avoid. :)

Any ideas?

Thanks.

---

### Post by James78 on 2010-07-04
I would've just used a RAID1 configuration to mirror the drive. Mirroring would be done automatically, and would always be backed up 100%. However, mdadm is a little hard to setup to say the least. So if you would rather not reinstall (I highly doubt you'd want too), you're best off with someone else's suggestions (you can set it up without reinstalling, but it'd be harder without the GUI tools the server installation provides). I just posted this for informational purposes, just so you know that this IS an option.

P.S. Sometimes the only way to learn is to experiment. I've reinstalled my server about 25 times experimenting. While tedious, I have a very good knowledge of how it works based off of nothing but trial and error.

---

### Post by chowanec on 2010-07-04
I must have left out the most important bit -- I don't actually *host* the web server.  It is a managed VPS, I have a shell account into it.

Otherwise, I would most definitely RAID the thing. :)

Thanks.

Chow

---

### Post by chowanec on 2010-07-04
And in my own tinkering, I just realized, I don't need sshfs at all -- I can, in thoery do all of this with just rsync... and, as you can imagine, I have problems there too:

I run this (website obscured):
```
rsync -avz -e ssh admin@example.com:/public_html/images/ /home/chow/Website/
```

And I get this error:
```

receiving file list ... rsync: link_stat "/public_html/images/." failed: No such file or directory (2)
done

sent 8 bytes  received 21 bytes  6.44 bytes/sec
total size is 0  speedup is 0.00
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1526) [Receiver=3.0.7]

```

Thing is -- that folder DOES exist and there ARE files in it.  Any ideas on why I am getting the "No such file or directory (2)" error?

Thanks.

---

