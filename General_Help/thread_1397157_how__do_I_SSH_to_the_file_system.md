---
title: "how  do I SSH to the file system"
date: 2010-02-02
forum: General Help
---

### Post by ranch hand on 2010-02-02
I know  I can do this somehow but can't figure it out.  Getting full access to /home is a piece of cake.

I want to be able to look in on all the files.

I would also like to know how to chroot through ssh.

I really hope someone know how to do this and can take the time to pamper a noob.

---

### Post by caryb on 2010-02-03
This is me so don't bash me folks if you differ in your approach!

1st of all RH I give the root user on the system a password```
sudo passwd root
``` so when you ssh to the box you type ```
ssh root@xxx.xxx.xxx.xxx
``` 
xxx is the ip address but could be the fqdn if setup in the dns or host file.

Then you have root access to the system as root user

Cary

---

### Post by ranch hand on 2010-02-03
> **caryb said:**
> This is me so don't bash me folks if you differ in your approach!

1st of all RH I give the root user on the system a password```
sudo passwd root
``` so when you ssh to the box you type ```
ssh root@xxx.xxx.xxx.xxx
```xxx is the ip address but could be the fqdn if setup in the dns or host file.

Then you have root access to the system as root user

Cary
I actually thought about trying something like that and might.  Just not on the box I am wanting to be able to get into.

I just got a Service76 laptop for my wife and I have to maintain it.  There are things that I like to try out on my test platform before dumping on the new toy.

I do not want a root password on that box either.  Seems too risky in this case.  If nothing else works, however, I will go that route.

Thanks a bunch.  I have an old box that we use for email and a couple other things that I will be trying that out on.

---

### Post by caryb on 2010-02-03
I disable root ssh logons so you have to be on the console to logon as root then all you do is ssh as a user then once you are in you su - then you are root.


Cary

---

### Post by ranch hand on 2010-02-03
I am not worried about the root login in ssh.  I am worried about having a root password on the wifes laptop.  Probably paranoid.

---

### Post by anders_c_ on 2010-02-03
Why don't you just ssh as your normal user and then use sudo to change files you don't have permission to?

ssh user@host
sudo rm /file/user/doesnt/have/permission/to

Or have i misunderstood you? Is the problem that you don't know how to work the terminal, and want a graphical way to get root access to the entire file system?

And why is this in the Lucid forum?

---

### Post by VMC on 2010-02-03
> **anders_c_ said:**
> Why don't you just ssh as your normal user and then use sudo to change files you don't have permission to?

ssh user@host
sudo rm /file/user/doesnt/have/permission/to

Or have i misunderstood you? Is the problem that you don't know how to work the terminal, and want a graphical way to get root access to the entire file system?

I was wondering this myself. But since I have never used ssh, I had no comment until now. I think I will have to try ssh just to be informed. The topic keeps coming up. Your approach of using a user and sudoing to root is the safest method.

---

### Post by Reiger on 2010-02-03
> **ranch hand said:**
> I know  I can do this somehow but can't figure it out.  Getting full access to /home is a piece of cake.

I want to be able to look in on all the files.

I would also like to know how to chroot through ssh.

I really hope someone know how to do this and can take the time to pamper a noob.

Okay, I may be missing something here but you want:
(a) be able to traverse the fs? That is generally speaking (excepting some very restrictive settings on certain /etc files) possible through SSH. Use the cd command.
(b) be able to take control over the files through chmod and chown no matter their ownership/permission status? Then you must set up sudo properly (or a root account/passwd). To do that look into **visudo**. If you install Ubuntu for your wife, and ask here to lend you here account for 5 seconds? (sudo visudo is required.)

(c) I am not sure what you mean with chroot, but ssh does not mount anything locally. You are litterally working _on_ that box, so if that box goes down you will be logged out of your SSH session. Of course once you have unrestricted sudo access on that machine via SSH you can probably chroot on _that_ machine like you would do on a local tty.

Alternatively you mean you want a chroot jail, so you account sees only a restricted subset of the entire file system on that machine? See: [http://www.debian.org/doc/manuals/securing-debian-howto/ap-chroot-ssh-env.en.html](http://www.debian.org/doc/manuals/securing-debian-howto/ap-chroot-ssh-env.en.html)

You can experiment on your _own_ machine with SSH by installing the ssh package. This pulls in a SSH server, so you can then log on to your own machine as: ssh user@localhost, providing a password at the prompt. (You will have to accept a RSA key fingerprint the first time you do this, it adds your own SSH server to the list of trusted servers.)

---

### Post by cariboo on 2010-02-03
I ssh in as a normal user, then run mc as root. ranch hand, you may like mc, it is a lot like the old Norton Commander, from the pre=Windows 3.0 era, it is available in the repositories.

You can do almost everything you would do from the command line. The latest version allows you to use nano as an editor, you can use it to change permissions and ownership of files and directories, it even works as an ftp client.

---

### Post by pressureman on 2010-02-03
You can sudo to a root shell without having to set a password on root's account. Just

```

sudo su -

```

---

### Post by rolnics on 2010-02-03
> **cariboo907 said:**
> I ssh in as a normal user, the run mc as root. ranch hand, you may like mc, it is a lot like the old Norton Commander, from the pre=Windows 3.0 era, it is available in the repositories.


+1

I second mc, its a god send! I'm still trying to get my head around command line commands...and how long have I been using linux?!2yrs+? lol. I use it a lot on my nslu2 debian slug, any linux install I do from now on it will be top of my list of installs!

---

### Post by ranch hand on 2010-02-03
OK.

First, this is in this forum as I am doing this from 10.04.  There may be issues here that I need to know in 10.04.

I am going to a 9.10 box.

When I get there the only menu that I get is for the /home file.  There is no option for "file system".  There is something I am not doing right or there is a problem with the ssh in 10.04.  I think it is me.

I am starting this from the connect to server option in "places".  It is the only way I know to do this.

---

### Post by anders_c_ on 2010-02-03
Well that changes it...i think most people here thought you were connecting with a ssh client in a terminal. In that case i don't know any other way than enabling root on the ssh server.

What you're using is normally called sftp, not ssh, thats what confused people.

Good Luck!

---

### Post by ranch hand on 2010-02-03
Well, I guess the problem is me.

I have the man page for ssh up right now and I can only understand about 1 word in 4.  I have no idea what it is telling me at all.

The options make no sense to me.  I can't even figure out how to set the address.

This may just be a bad idea.

---

### Post by xebian on 2010-02-03
I'm not an expert either but openssh client and server should be installed in both boxes.

ssh <loc address>  <-- usually ip address

Think of it as like logging on the box from a terminal except that the box is remote.  It will ask you for a logon id and then password.  

I haven't used gnome for a while but it used to be as easy as a pie in nautilus->places to connect to other boxes in the network.  All you need is a valid user/id/pass on the box.  For me it's easy because I only use the same userid/pass for all my boxes/installations.

---

### Post by knarf on 2010-02-03
```
sudo -s
```This gives you a root shell with all bells and whistles. It does not matter how you get there, console or ssh or telnet for all I care.

Put the following in *~/.bash_aliases* (or wherever you keep your aliases):

```
alias s='sudo'
alias ss='sudo -s'
```The shorter the better. Or should that be 'th shrtr th bttr'?

---

### Post by ronacc on 2010-02-03
is it absolutely necessary to do it remotely ?

---

### Post by ranch hand on 2010-02-04
It may be if she runs into a problem at a show and it running credit cards over it.

Here, I had a problem with trying to put a password on the boot menu and just plugged in my external and used this OS (yes I am on the daytime OS at this time of night - have a guest and am plying tunes at full blast over the altec lansing 5.1s - best responce of all my variations is 10.04)

---

### Post by jpeddicord on 2010-02-04
Moving this to General Help, since this isn't really specific to Lucid.

---

### Post by ImperialXT on 2010-02-04
Reading this I'm starting to think you're more so looking towards the remote desktop sort of perspective here instead of ssh or sftp aka GUI instead of CLI

---

### Post by kimda on 2010-02-04
If you want to manage that pc remotely via gui instead of terminal (ssh) enable remote desktop. System > Preferences > Remote Desktop. Then use vinagre to connect to this system Apps > Internet remote desktop viewer

---

### Post by nothingspecial on 2010-02-04
```
ssh -X -C -c blowfish user@ipaddress
```

```
nautilus --no-desktop
```

or ```
gksudo nautilus --no-desktop
```

depending on what you want to do.

---

