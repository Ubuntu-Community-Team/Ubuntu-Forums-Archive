---
title: "FreeNX Authentication failed for user"
date: 2010-09-24
forum: General Help
---

### Post by Abadon125 on 2010-09-24
Hello,
I just finished following the instructions found [here]("https://help.ubuntu.com/community/FreeNX") to install FreeNX on my ubuntu 10.04 server.  It went smoothly, just used the default keys.

Once I had that all set up I scrolled down and followed the instructions to set up the client and that went fine as well.

My problem is with actually using the program.  When I try to log in I get the error "Authentication failed for user tony" (my username).  Do I need to change anything in the configuration other than setting it to use gnome and putting in the host address?

Does it make a difference that my ssh settings only allow rsa login?  I logged into the server with ssh to see if that helped but it did not.  I even tried using the ssh key with the FreeNX Client but that did not work.

What am I doing wrong?

Also, the section on starting and stopping the server does not work for me either.  When I try to run it I get the error "Rather than invoking init scripts through /etc/init.d, use the service(8) utility, e.g. service freenx-server start

since the script you are attempting to invoke has been converted to an Upstart job, you may also use the start(8) utility, e.g. start freenx-server"  when I try to use the command that it gives (start freenx-server) it simply says Unknown job: freenx-server.

What command should I be using instead?

Thanks for the help on both questions!

---

### Post by Abadon125 on 2010-09-24
bump

---

### Post by CharlesA on 2010-09-25
Have you tried using just passwords?

I've only ever installed FreeNX on the desktop version of Ubuntu and just use regular SSH on server.

---

### Post by Abadon125 on 2010-09-25
Yes, I started a new vm and did a fresh install of ubuntu server 10.04 and followed the instructions [here]("https://help.ubuntu.com/community/FreeNX") to install FreeNX.  I then installed the client on another computer and was successfully able to connect using just the username and password.

I know that the problem has to do with the key based authentication, I just don't know how it has to be set up.

---

### Post by CharlesA on 2010-09-25
Ok.

I've only got the client installed on a Windows Box, but it looks like if you go to configure > General > Key > Import

It looks like you can paste the key in there, but it seems like it only accepts dsa keys with no passphrase.
EDIT:

Check [here]("http://www.nomachine.com/ar/view.php?ar_id=AR01C00126").

Looks like you create the keys like so:
```
charles@lynx:~$ sudo /usr/NX/scripts/setup/nxserver --keygen
[sudo] password for charles:
NX> 704 Starting: server-keygen operation at: Fri Sep 24 21:35:45 2010.
NX> 704 Generating new ssh-keys. Please wait.
NX> 704 Keys generated correctly. Backing up files.
NX> 704 Back up of keys made. Updating files.
NX> 704 Keys updated. NX clients should now use key:
NX> 704 /usr/NX/share/keys/default.id_dsa.key
NX> 704 to get connected to this NX server.
```

Import default.id_dsa.key into the client.

---

### Post by Abadon125 on 2010-09-25
> **CharlesA said:**
> Ok.

I've only got the client installed on a Windows Box, but it looks like if you go to configure > General > Key > Import

It looks like you can paste the key in there.

What key should I be using?  I tried importing the one that I would normally use for SSH but that did not work.

Do you think I need to add a user like [this ]("http://wiki.centos.org/HowTos/FreeNX#head-3a2e4992e1d6b6365aa4205abd4ca269e3b81053")shows? When I look at the man page for nxserver it says that PASSDB is deprecated so that makes me think that I should be doing something else instead.

---

### Post by CharlesA on 2010-09-25
Check the link in my edit. It explains everything. :)

Basically you need to generate a special key, due to how NX does authentication.

---

### Post by Abadon125 on 2010-09-25
Thanks for the help so far!
I don't have that scripts folder though.  I only have bin, lib, and share.  And thats only because I installed the client part.  Before that there wasn't even an NX folder in usr.

Am I missing something? Are using FreeNX or the NoMachine NX Server?

---

### Post by CharlesA on 2010-09-25
I've got NoMachine NX installed (server, client and node).

I'm not quite sure if FreeNX is the same or different.

---

### Post by Abadon125 on 2010-09-25
Is there any down side to using that instead?  I guess I will give that a try and see how it goes.

---

### Post by CharlesA on 2010-09-25
> **Abadon125 said:**
> Is there any down side to using that instead?  I guess I will give that a try and see how it goes.

Not that I know of. I'm using NX Free downloaded from [here]("http://www.nomachine.com/download.php").

---

### Post by Abadon125 on 2010-09-25
I installed the Client. Is it just me or is the node package missing from their downloads page?

Scratch that, I found it

---

### Post by Abadon125 on 2010-09-25
Still not working.  Followed all those instructions and wasn't working so I tried messing around with the sshd_config.  I added 

AuthorizedKeysFile %h/.ssh/authorized_keys2
AllowUsers nx

however still isn't working.  Starting to get quite frustrated.

---

### Post by CharlesA on 2010-09-25
> **Abadon125 said:**
> Still not working.  Followed all those instructions and wasn't working so I tried messing around with the sshd_config.  I added 

AuthorizedKeysFile %h/.ssh/authorized_keys2
AllowUsers nx

however still isn't working.  Starting to get quite frustrated.

I just installed it on a VM, but I needed to install Gnome before it would connect. If I used Openbox, it would fail to connect to the X session. :(

I had to install it in this order:

```
sudo apt-get install xserver-xorg xserver-xorg-core
sudo apt-get install gnome-core
sudo apt-get install gdm
sudo dpkg -i nxclient_3.4.0-7_x86_64.deb nxserver_3.4.0-14_x86_64.deb nxnode_3.4.0-14_x86_64.deb
sudo reboot
```

It looks like it does the initiate authentication via that dsa key and after that is done, it uses the password to connect. That means that it's using keys initially, but still requires the password to connect, but you can tell it to save the password in the session by clicking on "configure" in the client and selecting "remember my password"

If you change the keys it uses by running:

```
sudo /usr/NX/scripts/setup/nxserver --keygen

```

You will need to paste the key located at /usr/NX/share/keys/default.id_dsa.key into the client for it to connect, otherwise you will get an error message.

Also note: After installing gnome-core, I got this error when logging in to the console or via NX.

```
The panel encountered a problem while loading "OAFIID:GNOME_FastUserSwitchApplet"
```

You can fix it by select "delete" when prompted. :)

---

