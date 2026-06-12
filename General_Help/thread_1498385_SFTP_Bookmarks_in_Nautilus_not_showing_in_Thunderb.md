---
title: "SFTP Bookmarks in Nautilus not showing in Thunderbird"
date: 2010-05-31
forum: General Help
---

### Post by paulsp on 2010-05-31
Hi all,

I have some SFTP bookmarks in Nautilus. They work really well. However, these same bookmarks do not show up everywhere. For instance, when I am using Thunderbird and try to save an attachment, only my local bookmarks show up and not the external ones. On the other side, when I am using OpenOffice and select SAVE FILE, I DO see all bookmarks. 

Any idea what causes this?? 

Regards,
Paul

---

### Post by DavePlummer on 2010-05-31
To use those bookmarks, I believe that an application needs to be aware of the GNOME Virtual File System (gvfs). It appears that Thunderbird is not.

---

### Post by paulsp on 2010-05-31
Copy that. And any way to make it work, or will it be just impossible?

Regards,
Paul

---

### Post by DavePlummer on 2010-06-01
You could install sshfs, and mount the remote location on your local filesystem. Then applications will see it as a local resource. There are many good HowTo's on the subject.

---

### Post by Lucky. on 2010-06-01
Yeah, I got fed up with the same issues with some of my programs and went the SSHFS route.  Sorry I'm a bit pegged for time right now, but I will try to post my instructions later tonight!

---

### Post by Lucky. on 2010-06-02
Here's my personal notes compiled from various how-tos and mixed with my own stuff.  I've only done this twice, so I hope the notes are correct enough to follow (usually my notes suffer from "oh yeah I forgot that" syndrome, but about the 3rd time around they're solid).

The passwordless SSH info was lifted straight from Matthias Kettner, so I need to give him credit here:  [Passwordless SSH login](http://linuxproblem.org/art_9.html) by [Matthias Kettner](http://mathias-kettner.de/).

In a nutshell:

1.  Get SSHFS on the client.
2.  Set up mount point on the client, and set permissions correctly.
3.  Create a key pair for your user accounts on the client & server to allow for passwordless/non-interactive login.
4.  Add mount command to &#8220;Startup Applications&#8221; in Gnome.

If you're using SFTP to get to your server also, I'm guessing you already have SSH on your server, and have your &#8220;share(s)&#8221; & permissions set up correctly on the server.

For the sake of examples, here's my information:

[b]
Server Hostname:  boss
Intended SSHFS folder &#8220;shared&#8221; on Server:  /srv/stuff
My username on both the server and client:  lucky
[/b]
(*Different usernames on the client/server would probably work, but mine are the same on both.)


On the client side, install SSHFS

```

Client:
sudo apt-get install sshfs

```

I want my local mount point to be /mnt/stuff, so I'll create that directory on the client & give myself permissions to the share via the group:

```

Client:
sudo mkdir /mnt/stuff
sudo chown lucky /mnt/stuff

```
(I recommend better permissions, but this is quick and dirty, not a security discussion...)

From the client side, test out mounting the share:

sudo sshfs <YourNameOnServer>@<ServerName>:<ServerFileShare> <LocalMountPoint>

So in my case:

```

Client:
sudo sshfs lucky@boss:/srv/stuff /mnt/stuff

```

Check the /mnt/stuff folder to see if things mounted correctly and it looks good.

Then unmount:

```

Client:
sudo fusermount -u /mnt/stuff

```

Now that we know our share/mounting works, we have another problem:  SSH/SSHFS requires an interactive login - it forces us to type in our name and password each time.  That's no good, we want our shares to be available at login!

In order to avoid the interactive login, we can create a trust between your server and client login accounts by using a public/private key pair.

Create an ssh key pair on the client **(do this with your user account, not root)**:

```

Client:
ssh-keygen -t rsa

```

(When prompted for stuff, simply keep pressing enter...leave the password blank.)

If it already doesn't exist, create an .ssh folder in your user home folder on the server.
We can use ssh from the client to do this!

```

Client:
ssh lucky@boss mkdir -p .ssh

```

Append my client's new public key to my server account's ssh authorized keys:
Again, you can use ssh from the client to do this!

```

Client:
cat .ssh/id_rsa.pub | ssh lucky@boss 'cat >> .ssh/authorized_keys'

```

Now we should have a passwordless login!  Test it out by trying a simple login from the client to the server:

```

Client:
ssh boss

```

Did you log in without being asked for a password?  Great!  Now log out!

At this point we have SSHFS on the client, and SSH on the server.  Our shares are ready, and we have a passwordless login.  Great!  The last thing to do is set up an auto-mount on login.

Some people suggest toying with fuse & fstab (add users to the fuse group, edit /etc/fuse.conf, change permissions for /etc/fuse.conf, put an entry in the fstab, etc.).  That's a fine method, but I found something much easier:

Simply add the mount command to our startup applications:

Click System->Preferences->Startup Applications
Click &#8220;Add&#8221;
For a name, type anything you like - maybe &#8220;Auto-Mount my folder&#8221;
For command, type our mount statement we used earlier

sshfs <YourNameOnServer>@<ServerName>:<ServerFileShare> <LocalMountPoint>

```

sshfs lucky@boss:/srv/stuff /mnt/stuff

```

Log out/log in, check to see that the mount automatically works, and make a bookmark to it since you probably don't want to keep manually navigating to your mounted folder!

This method works good for me, but a few drawbacks.

1.  There's no unmount when I log out.  This hasn't hurt me yet, but it's untidy.  Anybody know where I would place an unmount statement?

2.  If you lose connection with the server, you lose the share unless you remount.  Not a problem for desktop PC use, but laptops & wireless can get ugly.

3.  A bug causes certain files to appear as executable.  I mentioned this [here](http://ubuntuforums.org/showthread.php?t=1485059), and filed a bug report with Gnome - but it's a fuse problem according to them.  I never followed up and filed a bug with fuse like I should have).

4.  Seems like every once in a while I'm asked to type my password when I log in - this has something to do with the SSHFS startup app, but I'm not sure why since the passwordless login works.  Still haven't investigated this fully.

I hope this helps - any feedback from others & fixes to the problems would be happily accepted!

---

### Post by paulsp on 2010-06-02
Thanks a lot!! I was able to install SSHFS and it works like a charm, great solution!

---

### Post by Lucky. on 2010-06-02
Thanks!  I'm glad it worked out for you!

---

