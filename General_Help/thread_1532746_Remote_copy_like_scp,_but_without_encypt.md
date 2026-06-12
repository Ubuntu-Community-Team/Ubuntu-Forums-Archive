---
title: "Remote copy like scp, but without encypt"
date: 2010-07-16
forum: General Help
---

### Post by bakegoodz on 2010-07-16
I'm sure this a stupid question for the *nix veterans. I really like scp for sending a random file here or there, were a permanent share is overkill. Sometimes I send a very large file over a local network that has no reason to encrypted. The encryption maxes out the processor that needs cycles for other stuff and bottlenecks the transfer. Is there a command with similar syntax without encryption?

---

### Post by bodhi.zazen on 2010-07-16
On a LAN you can use NFS, Samba, FTP, or even http.

---

### Post by bakegoodz on 2010-07-22
Is there a command line remote copy program without encryption? I've looked at the man pages on rsync, scp, and rcp and I can't find a way to turn it off either.

---

### Post by endotherm on 2010-07-22
> **bakegoodz said:**
> Is there a command line remote copy program without encryption? I've looked at the man pages on rsync, scp, and rcp and I can't find a way to turn it off either.
yeah, they hardened all the 'r' utils some years ago. one option is to set up ftp or tftp, and access files via wget or the cli ftp client. 

or even better if it fits your usecase; just mount the location, and use regular old cp. here is a python script i had lying around that shows how to mount an smbshare locally for access.

```


#!/usr/bin/env python
import os
import subprocess
import random

#randStartrek.py
#selects a random file from a folder hierarchy,
#and opens it, with a specified app.

#be sure to configure these constants to fit your system.
rootpath= os.path.expandvars("smb://<SERVER>/tv/scifi/star-trek/")
filetypes= ["mkv", "avi"] #, "ogm", "ogg", "mp4"]
videoplayercmd="smplayer"

#these constants pertain to smb paths. you can ignore them if rootpath
is a local path
tmppath= os.path.expandvars("/home/<USER>/tmp/startrek/") #only  used if
a net path is given. will be the mountpoint for the share.
mountcmd= "smbmount %s %s -o username=%s"
umountcmd= "sudo umount %s"


eps= []


def mountPath(path):
        try:
                global rootpath
                if not os.path.exists(tmppath):
                        print "creating temp folder: " + tmppath
                        os.makedirs(tmppath)

                uname= raw_input("Enter Username:")
                cmd= mountcmd %(os.path.expandvars(path.split(":")[1]),  tmppath,
uname)
                subprocess.call(umountcmd %(tmppath,), shell=True)
                stat= subprocess.call(cmd, shell=True)
                if int(stat) != 0:
                        print "failed to mount smb path"

                rootpath= tmppath
        except Exception as ex:
                print(ex)
                pass


def getFileList():
        if(rootpath.startswith("smb://")):
                print "mounting smb path"
                mountPath(rootpath)

        print "scanning directory..."
        for root, dirs, files in os.walk(rootpath, False):
                for f in files:
                        f = os.path.join(root, f)
                        for t in filetypes:
                                if(f.endswith(t)):
                                        eps.append(f)
                                        break
def main():
        getFileList()
        if len(eps) <= 0:
                print "No files. Exiting"
                exit(1)
        else:
                idx = random.randint(0, len(eps) - 1)
                print("Opening file: " + eps[idx])
                os.system("%s \"%s\" &" %(videoplayercmd, eps[idx]))


if __name__ == "__main__":
        main()

```

---

### Post by gmargo on 2010-07-22
**ftp** or **netcat** or **rsync** are possibilities.  The **ncftpget** and **ncftpput** tools from the **ncftp** package will give you a simple command interface for ftp transactions.  If there is an rsync daemon on the remote, you can use the double-colon addressing mode (or rsync://) to force a rsync connection.

---

### Post by bakegoodz on 2010-07-25
Netcat looks very interesting, thanks!

[http://www.g-loaded.eu/2006/11/06/netcat-a-couple-of-useful-examples/](http://www.g-loaded.eu/2006/11/06/netcat-a-couple-of-useful-examples/)

---

### Post by bakegoodz on 2010-08-19
With netcat you have to setup a sever and client, certainly not as easy and you can't use directories or wildcards.

There must be an answers to this. I remember reading an article years ago talking about how you should use scp instead of another tool. What was the other tool? It is really overkill to encrypt everything on a private network

---

### Post by v1ad on 2010-08-19
not sure if sshfs is encrypted. man it and see the options.

---

### Post by bakegoodz on 2010-08-21
sshfs does only encypted

---

### Post by gmargo on 2010-08-21
> **bakegoodz said:**
> I remember reading an article years ago talking about how you should use scp instead of another tool. What was the other tool?
The other tool was **rcp**. See [http://en.wikipedia.org/wiki/Rcp_%28Unix%29](http://en.wikipedia.org/wiki/Rcp_%28Unix%29)

Have you tried **rsync**, **ncftp**, or **lftp**?  While I understand your objection for a local LAN, I wonder what you're copying (or how often?) such that the encryption is a bottleneck.

---

### Post by LightningCrash on 2010-08-21
> **v1ad said:**
> not sure if sshfs is encrypted. man it and see the options.

sshfs is encrypted.


OP you could also look at NFS if it's on the same network...

---

