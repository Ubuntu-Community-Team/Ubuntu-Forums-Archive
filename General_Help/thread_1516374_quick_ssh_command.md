---
title: "quick ssh command"
date: 2010-06-23
forum: General Help
---

### Post by spiky001 on 2010-06-23
Hi I want to ssh into my media folder on server I,m missing something

```
ssh username@server:????????
```

thks

---

### Post by s.fox on 2010-06-23
Hello,

```
ssh user@server
```

You will then be prompted for the password.

-Silver Fox

---

### Post by spiky001 on 2010-06-23
I can get that far ok but is it possible to do it in 1 go

---

### Post by bodhi.zazen on 2010-06-23
> **spiky001 said:**
> I can get that far ok but is it possible to do it in 1 go

One go ?

You can add "cd /media" to ~/.bashrc (on the server)

---

### Post by CharlesA on 2010-06-23
> **spiky001 said:**
> I can get that far ok but is it possible to do it in 1 go

You cannot do it in one shot with a password.

I suppose you could use a key with no passphrase, but that's not as secure as a key with a passphrase.

EDIT: I am unsure what you mean by in "one go" but I gave it a shot. :)

---

### Post by s.fox on 2010-06-23
Hello again,

Please clarify.  Do you mean have the password submitted also from a single command?  I believe you can not do that.  Can someone confirm my belief please :)

-Silver Fox

---

### Post by spiky001 on 2010-06-23
No you did answer it Charles I wanted to go ssh name server then get into media that way, I did think security wld stop me thats fine tho thks for reply

---

### Post by Penguin Guy on 2010-06-23
I believe the OP wants something like:
```
ssh user@server:/media
```
(that's just an example - I don't think it's actually possible to do anything like that)

---

### Post by spiky001 on 2010-06-23
it is, but it was to transfer a file I could use the (scp get) will do the job if I can figure it out

---

### Post by CharlesA on 2010-06-23
> **spiky001 said:**
> it is, but it was to transfer a file I could use the (scp get) will do the job if I can figure it out

If you want to, you can use sftp (ftp over SSH) to transfer files.
Check out Filezilla, it's pretty nice. :)

---

### Post by spiky001 on 2010-06-23
I do have filezilla but I was trying to use terminal just for experiance

---

### Post by Penguin Guy on 2010-06-23
> **spiky001 said:**
> it is, but it was to transfer a file I could use the (scp get) will do the job if I can figure it out
```
$ man scp
scp [[user@]host1:]file1 ... [[user@]host2:]file2
```
In simple terms:
```
scp user@server:/path/to/remote/target /path/to/local/destination
*(or the other way round)*
```

---

### Post by spiky001 on 2010-06-23
thks for that I know it,s alot of messing about but still learning

---

### Post by CharlesA on 2010-06-23
Just IMHO, but I think that sftp is a hell of a lot easier than scp if you are doing it from the command line.

---

### Post by bodhi.zazen on 2010-06-23
You might want to look at sshfs

[http://embraceubuntu.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/](http://embraceubuntu.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/)

You may also want to use nfs, although nfs is not secure over the internet. You can harden nfs with kerberos.

If you are sharing with Windows clients , consider samba.

---

### Post by apmcd47 on 2010-06-23
*SCP *is probably the way to go for a single file in either direction. For transferring multiple files use an *SFTP *session. I admit to being a proponent of *LFTP*, a scriptable multi-protocol *FTP *client which can do automated cd into a directory, e.g.:
```
lftp sftp://apm@computer.dot.com/home/apm/some/sub/directory
```
will take me into ~/some/sub/directory on computer.dot.com using *sftp *as the protocol.

The included script *lftpfetch *not only allows you to fetch a file using the protocol of your choice but also serves as an example of how to script with *lftp*.

Andrew

---

### Post by Penguin Guy on 2011-02-28
If you think the question has been answered satisfactorily would you mind reducing clutter by marking it as solved through [COLOR="Green"]Thread Tools -> Mark as Solved[/COLOR]? Thanks :).

---

