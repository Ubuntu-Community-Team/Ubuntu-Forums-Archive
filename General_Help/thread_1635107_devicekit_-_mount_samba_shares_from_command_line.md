---
title: "devicekit - mount samba shares from command line"
date: 2010-12-01
forum: General Help
---

### Post by lytithwyn on 2010-12-01
Is there a way for a normal user to mount samba shares from the command line using devicekit?  It seems like I remember there was a way to do it using hal, but that's been replaced by devicekit in Lucid if I've read correctly.

I can click on the shares I want in nautilus under "Network", but I'm using fluxbox and I'd like to mount a few shares at startup.  I read the documentation for the udisks command, but I can't figure out how to get it to work with samba shares.

**NOTE: As you will notice in post #3, I figured out that this has nothing to do with hal or devicekit, but deals with fuse instead.  Please read on.**

---

### Post by papibe on 2010-12-01
Besides samba you need to install an additional package:
```
$ sudo apt-get install smbfs
```
When it has been installed you can mount samba shares like this:
```
$ sudo mount -t smbfs //sambaserver/theshare /local/dir  -o rw,otheroptions
```
Some new versions use cifs as a file system type instead of smbfs (-t cifs).

Good Luck!

---

### Post by lytithwyn on 2010-12-02
Well, papibe, I'm looking for a way to do it as a normal user.

Anyway, I totally asked a semi-dumb question.  I had forgotten...it wasn't hal that allowed user-mounting of smb shares before; it was fuse.

After doing some research, I found that there is a nice tool called smbnetfs that makes this easier.  What it will do is create a special filesystem under the specified folder that looks like the "network" location in Nautilus.  Here's how I got it working:

```

# add yourself to the fuse group
usermod -a -G fuse [username]

#log out and log back in

#install smbnetfs
sudo apt-get install smbnetfs

# make the proper configuration directory and copy the files
mkdir ~/.smb
cp /etc/samba/smb.conf ~/.smb/
cp /etc/smbnetfs.conf ~/.smb/
chmod 600 ~/.smb/smbnetfs.conf # else it refuses to run

# I uncommented the line in smbnetfs.conf that says:
# auth    "guest" ""
# but I don't know if this is needed or not

# make a directory where we'll mount smbnetfs
# you should be able to put this pretty much anywhere you want
mkdir ~/network

# mount smbnetfs
smbnetfs ~/network

```

Now I can access samba shares the same way they work in nautilus.  The only catch I found is that `ls` hangs if you try to run it right under your smbnetfs directory (in my case, ~/network) but it works just fine if you do `ls ~/network/WORKGROUP`.

NOTE: I had to experiment to get this sequence of commands right.  Instead of spending 20 minutes finding all the right ones in my .bash_history, I just typed them into the post here so DOUBLE CHECK the commands for errors before you run them.

---

