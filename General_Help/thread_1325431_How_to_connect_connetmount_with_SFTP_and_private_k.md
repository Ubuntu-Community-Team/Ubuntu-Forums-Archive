---
title: "How to connect connet/mount with SFTP and private key"
date: 2009-11-13
forum: General Help
---

### Post by acroporas on 2009-11-13
How can I connect&mount to a remote server using SFTP when the servers SSH is configured to use a private key for authentication?

---

### Post by FuturePilot on 2009-11-13
You can use Nautilus. Just do Places > Connect to server and select SSH from the drop down. If you already have your key setup on the server there's nothing more to do. It will automatically use the appropriate key.

---

### Post by upbeat.linux on 2009-11-13
Slicehost has a great article here.  It's pretty straight forward:

[http://articles.slicehost.com/2008/11/28/ubuntu-intrepid-setup-page-1](http://articles.slicehost.com/2008/11/28/ubuntu-intrepid-setup-page-1)

---

### Post by acroporas on 2009-11-13
> **FuturePilot said:**
> You can use Nautilus. Just do Places > Connect to server and select SSH from the drop down. If you already have your key setup on the server there's nothing more to do. It will automatically use the appropriate key.

Ok, good to know that "Connect to Server" can handle this - that is what i was hoping.

I suppose then my next question is how do I set up the key.  I was provided the private key.  Where do I put it and what do I do with it so that nautilus will be able to find/use it.

---

### Post by FuturePilot on 2009-11-13
> **acroporas said:**
> Ok, good to know that "Connect to Server" can handle this - that is what i was hoping.

I suppose then my next question is how do I set up the key.  I was provided the private key.  Where do I put it and what do I do with it so that nautilus will be able to find/use it.

Put the private key in ~/.ssh/. That's a hidden directory in your home directory so press Ctrl+H in the file manager to show the hidden files.

---

### Post by delcypher on 2009-11-13
I expect Nautilus will probably use ssh-agent to manage keys so it will probably expect your private key to be in on of these:

~/.ssh/id_rsa
~/.ssh/id_dsa
~/.ssh/identity

You should put the key in the appropriate file.
>  The default is ~/.ssh/identity for protocol version 1, and ~/.ssh/id_rsa and ~/.ssh/id_dsa for protocol version 2.
From ssh manual

I'd advise you check your key actually works first by manually loading it then seeing if you ssh into the remote host.

You can do that using the command line.
```
ssh -i /path/to/your/private_key -v username@remotehost.com 
```

You can also try loading your key into ssh-agent. In ubuntu it seems ssh-agent is always running so you don't need to load it first, it will ask for your password if it's not a passwordless key.
```
ssh-add /path/to/your/private_key
```

If you can log-in then your key works. If it doesn't then the verbose output of ssh will tell you why.

Personally I wouldn't use Nautilus to log-in at all. I would use sshfs to mount a directory on your remote host instead and then happily browse it with nautilus.

---

### Post by acroporas on 2009-11-13
> **FuturePilot said:**
> Put the private key in ~/.ssh/. That's a hidden directory in your home directory so press Ctrl+H in the file manager to show the hidden files.



Ok, I must not be explaining things properly, but It still is not working, thanks for being patient with me.

The server I am trying to connect to is an amazon ec2 server running ubuntu.

Amazon's instructions for connecting via ssh are:

```
 ssh -i {filename goes here}.pem root@{address goes here}.com
```

I paste this code into the terminal and it does connect.

So based on the instructions I just received from you guys, I: 

 - copied the {filename goes here}.pem  file to the .ssh directory.
 - Clicked "Connect To Server"
 - selected ssh as type
 - entered {address goes here}.com into the server field
 - entered root into the username field
 - clicked connect

I then get a popup that says Permission denied

---

### Post by acroporas on 2009-11-13
> **delcypher said:**
> Personally I wouldn't use Nautilus to log-in at all. I would use sshfs to mount a directory on your remote host instead and then happily browse it with nautilus.

Well if sshfs is an easier way to mount a directory, I would love to learn more.  Would you be so kind as to post some example code for how I might mount the directory with sshfs?

In the mean time, I will be trying to figure out the rest of your post.

Thanks

---

### Post by acroporas on 2009-11-13
> **delcypher said:**
> 
You can also try loading your key into ssh-agent. In ubuntu it seems ssh-agent is always running so you don't need to load it first, it will ask for your password if it's not a passwordless key.
```
ssh-add /path/to/your/private_key
```

If you can log-in then your key works. If it doesn't then the verbose output of ssh will tell you why.

That right there was the trick.  After doing that it works.  Thank you so much.

:)

---

### Post by FuturePilot on 2009-11-13
> **acroporas said:**
> Ok, I must not be explaining things properly, but It still is not working, thanks for being patient with me.

The server I am trying to connect to is an amazon ec2 server running ubuntu.

Amazon's instructions for connecting via ssh are:

```
 ssh -i {filename goes here}.pem root@{address goes here}.com
```

I paste this code into the terminal and it does connect.

So based on the instructions I just received from you guys, I: 

 - copied the {filename goes here}.pem  file to the .ssh directory.
 - Clicked "Connect To Server"
 - selected ssh as type
 - entered {address goes here}.com into the server field
 - entered root into the username field
 - clicked connect

I then get a popup that says Permission denied

Oh, now I see. I'm guessing .pem is different from the usual id_rsa type keys? I don't really know. If using it from the command line works there should be a way to make it work but I'm not exactly sure how.

Edit: never mind I see you have solved it :)

---

### Post by delcypher on 2009-11-13
That command should read
```
 ssh -i /path/to/your/privatekey your_username@yourdomain.com
``` 

To use sshfs you need to install the package, the command to install it is
```
sudo apt-get install sshfs
```

then to mount a remote host as the directory /mnt (your mount point) (you can use any directory you like even ones with stuff in - it will not write over the top of them the contents will just be invisible until you umount). Note the -o ssh_command... option should not be necessary if you have loaded your key using ssh-add /path/to/your/privatekey .
```
sshfs username@remotehost.com:/folder/in/remotehost /mnt -o ssh_command='ssh -i /path/to/your/privatekey'
```

to unmount where /mnt is your mount point:
```
fusermount -u /mnt
```

I prefer to use a mount point in my home directory. e.g. /home/username/mnt/ and use that as my mountpoint instead

---

### Post by acroporas on 2009-11-13
> **delcypher said:**
> 
```
sshfs username@remotehost.com:/folder/in/remotehost /mnt -o ssh_command='ssh -i /path/to/your/privatekey'
```
Again, thank you

---

