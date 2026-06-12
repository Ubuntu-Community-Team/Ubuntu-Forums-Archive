---
title: "Accessing a samba share via command line?"
date: 2010-07-03
forum: General Help
---

### Post by sr_guy on 2010-07-03
I have a 500GB external usb drive connected to my USB router (running dd-wrt). I have the router setup with samba and can read/write to it from any PC on the network. I have it setup to automount in Ubuntu. How can I access that mounted samba share when I SSH into the box? I want to cp or mv files from the PC to the Networked samba share via ssh CLI.

---

### Post by capscrew on 2010-07-03
> **sr_guy said:**
> I have a 500GB external usb drive connected to my USB router (running dd-wrt). I have the router setup with samba and can read/write to it from any PC on the network. I have it setup to automount in Ubuntu. How can I access that mounted samba share when I SSH into the box? I want to cp or mv files from the PC to the Networked samba share via ssh CLI.

When you mount the share to the Linux file system you should be able to change to that mount point (not share) and the files and directories will be available to you.

As an example, if you mount the share at [FONT="Courier New"]**/mnt/mountpoint**[/FONT] then from the CLI you should be able to do this```
cd /mnt/mountpoint
``` and see the data.

---

### Post by robsoles on 2010-07-03
hey sr_guy, if capscrew has nailed it for you then please mark your thread as solved, otherwise...

What are you doing to auto-mount this networked share? If it is inside a 'standard' user's session of some kind then ~/.gvfs/ may be the way you can reach it using SSH - I know this is a case when the share has been mounted by a logged in user using gnome for instance.

---

### Post by sr_guy on 2010-07-08
To revisit this,

I'm getting closer:

mount -t smbfs -o username=root //192.168.1.1/seagate /media/seagate

I am able to access that samba drive as a mount point, but I want to make a script to auto mount it, but with the above command it requires a password. What piece am I missing to add the password to that command?

I've tried -p password and no go.

---

### Post by capscrew on 2010-07-08
> **sr_guy said:**
> To revisit this,

I'm getting closer:

mount -t [COLOR="Red"]**smbfs **[/COLOR]-o username=root //192.168.1.1/seagate /media/seagate

I am able to access that samba drive as a mount point, but I want to make a script to auto mount it, but with the above command it requires a password. What piece am I missing to add the password to that command?

I've tried -p password and no go.

Two things to note: 

The mount type (noted in red above will cause problems with some later MS Windows systems.  You should use **[COLOR="Green"]cifs [/COLOR]** instead.  CIFS is an update to smbfs to accommodate MS extensions of the CIFS/SMB protocol. 

You can auto mount this using fstab.  That's what it is for.  See [**_here _**]("https://help.ubuntu.com/community/Fstab").  Use fstab assumes (always a dangerous thing) that you are not removing the external drive (i.e.  the connection is for convenience not portability).  I have a eSATA drive in just that configuration.

---

### Post by sr_guy on 2010-07-09
This worked in fstab:

//192.168.1.1/seagate /media/seagate cifs username=root,password=pw 0 0

Mounted after reboot as well =)

---

### Post by capscrew on 2010-07-09
> **sr_guy said:**
> This worked in fstab:

//192.168.1.1/seagate /media/seagate cifs username=root,password=pw 0 0

Mounted after reboot as well =)

Sweet!

---

### Post by Telengard C64 on 2010-07-09
> **sr_guy said:**
> This worked in fstab:

//192.168.1.1/seagate /media/seagate cifs username=root,password=pw 0 0

Mounted after reboot as well =)

Nothing necessarily wrong with that. The only concern I would have is that the login credentials for the Samba server are stored in a plain text file which is readable by anyone with access to the system. This may not be a concern in a home environment, but it should be a consideration.

---

### Post by capscrew on 2010-07-09
> **delhiteen said:**
> Will it work properly.......


Is this a question?  If it is a question then answer is, yes, it will work.  But you have created a security risk because anyone with access to this host (computer) can view the /etc/fstab file.  This means the root password can be seen.  I would look [**_here _**]("http://ubuntuforums.org/showthread.php?t=283131")for some ideas.

Generally it is not a good idea to expose the root account to potential misuse.  Are you the only user on the system?  Where and how do I securely store the password?

---

### Post by bodhi.zazen on 2010-07-09
> **capscrew said:**
> Is this a question?  If it is a question then answer is, yes, it will work.  But you have created a security risk because anyone with access to this host (computer) can view the /etc/fstab file.  This means the root password can be seen.  I would look [**_here _**]("http://ubuntuforums.org/showthread.php?t=283131")for some ideas.

Generally it is not a good idea to expose the root account to potential misuse.  Are you the only user on the system?  Where and how do I securely store the password?

What you say is true, but ...

1. Samba does not use the root login password. root would (should) be a samba user not the same as root the administrative account. samba users are not the same as a login user (or at least I separate the two on my samba servers, lol).

2. As you indicated on your previous post, this is a reasonable strategy (putting a user name and password) in fstab on a LAN. Samba should NOT be used over the internet.

3. If you really wish you can make a credentials file. Not sure if that is much better, that would be an opinion.

4. Large business should use kerberos.

---

### Post by Elfy on 2010-07-09
> **capscrew said:**
> Is this a question?  If it is a question then answer is, yes, it will work.  But you have created a security risk because anyone with access to this host (computer) can view the /etc/fstab file.  This means the root password can be seen.  I would look [**_here _**]("http://ubuntuforums.org/showthread.php?t=283131")for some ideas.

Generally it is not a good idea to expose the root account to potential misuse.  Are you the only user on the system?  Where and how do I securely store the password?

It was a spam account.

---

