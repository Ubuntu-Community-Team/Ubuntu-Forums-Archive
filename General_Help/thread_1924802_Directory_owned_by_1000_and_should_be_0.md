---
title: "Directory owned by 1000 and should be 0"
date: 2012-02-13
forum: General Help
---

### Post by Jonners59 on 2012-02-13
I did some silly messing about to get Stunnel working in etc, and now have a situation where the ownership is wrong, not being root.

I have tried all the fixes logging in via restoration from Grub, but that does not work.  I have noticed that in Settings when I select Users and Groups it does not start.  I have tried adding users and checking that the accounts root and myusername exist and they do.

Any help please?

I am using 11.10 64-bit

---

### Post by jayshomebrew on 2012-02-13
check out the command [chown]("http://manpages.ubuntu.com/manpages/lucid/man1/chown.1.html").  see [file permissions]("https://help.ubuntu.com/community/FilePermissions")

example:
```
jay@weissbier:/tmp$ ls -l
total 44
drwxr-xr-x 2 [COLOR="Blue"]jay jay[/COLOR] 4096 2012-02-13 08:50 1-jay
jay@weissbier:/tmp$ **sudo chown -R root:root /tmp/1-jay**
jay@weissbier:/tmp$ ls -l
total 44
drwxr-xr-x 2 [COLOR="Blue"]root root[/COLOR] 4096 2012-02-13 08:50 1-jay

```

---

### Post by Jonners59 on 2012-02-13
> **jayshomebrew said:**
> check out the command [chown]("http://manpages.ubuntu.com/manpages/lucid/man1/chown.1.html").  see [file permissions]("https://help.ubuntu.com/community/FilePermissions")

example:
```
jay@weissbier:/tmp$ ls -l
total 44
drwxr-xr-x 2 [COLOR="Blue"]jay jay[/COLOR] 4096 2012-02-13 08:50 1-jay
jay@weissbier:/tmp$ **sudo chown -R root:root /tmp/1-jay**
jay@weissbier:/tmp$ ls -l
total 44
drwxr-xr-x 2 [COLOR="Blue"]root root[/COLOR] 4096 2012-02-13 08:50 1-jay

```

Thanks Jay and other cmds, not sure of the one you have just shown.  I shall try later or tomorrow and get back.
I have tried a lot of chmod

---

### Post by SeijiSensei on 2012-02-13
> **Jonners59 said:**
> I have tried a lot of chmod

You won't get very far unless you use sudo.

---

### Post by Jonners59 on 2012-02-13
Did do sudo

Tried again...  This is what I got

```

sudo chown root /etc/sudoers
sudo: /etc/sudoers is mode 05440, should be 0440
sudo: no valid sudoers sources found, quitting

sudo chmod 777 -R /etc
sudo: /etc/sudoers is mode 05440, should be 0440
sudo: no valid sudoers sources found, quitting

 ls -l /etc/sudoers
-r-Sr----T 1 baronipc root 574 2011-09-11 20:09 /etc/sudoers

```

---

### Post by jayshomebrew on 2012-02-14
jonners,
I think you broke the sudoers file.

follow this:
[http://psychocats.net/ubuntu/fixsudo]("http://psychocats.net/ubuntu/fixsudo")

or you can boot your ubuntu live cd/dvd, mount your local drive, and fix your /etc/sudoers file.

If you still can't fix it, try searching using your favorite search engine "fix sudoers file"

---

### Post by Jonners59 on 2012-02-14
> **jayshomebrew said:**
> jonners,
I think you broke the sudoers file.

follow this:
[http://psychocats.net/ubuntu/fixsudo](http://psychocats.net/ubuntu/fixsudo)

or you can boot your ubuntu live cd/dvd, mount your local drive, and fix your /etc/sudoers file.

If you still can't fix it, try searching using your favorite search engine "fix sudoers file"

I had a bad feeling I had.....  Thanks for this, I'll try what you suggested tonight and feed back.

OK.  Booted in to *Recovery mode* and selected *Drop to root shell prompt*
typed the commands as per the link (user guide) - had done this before, but thought worth yet another go:
Typed
```
chmod 0440 /etc/sudoers
```seemed to accept it, so tried:
```
sudo cp /etc/sudoers /etc/sudoers.backup
```Came back with the same error message....  So it had not worked.  I re entered the code again just to make sure and just in case it affected after boot, so I did:
```
chmod 0440 /etc/sudoers
```and re-booted

I then tried again, this time I booted using the 64-bit 11.10 CD in to "try" Ubuntu.
Opened terminal and tried
```
chmod 0440 /etc/sudoers
```Said it had changed.  Then I tried to change the owner to root as it was down as me so I tried
```
sudo chown -R root /etc/sudoers
```Failed as it said that "[I]sudo is mode 05440 should be 0440" 
[/I]

---

### Post by Dave_L on 2012-02-14
You need to use both these commands to set the correct permissions, while in recovery mode or booted from a Live CD:

chown root:root /etc/sudoers
chmod 440 /etc/sudoers

Of course if you're booted from a Live CD, make sure you're changing the sudoers file on your hard disk, and not the temporary one in RAM that's created from the CD.

(Maybe you've already tried this. The posts above are confusing.)

---

### Post by Jonners59 on 2012-02-14
Thanks Dave_L and all
I have tried all these and more, none worked, but I have just found this and I have now managed to change the owner back to root...

```
pkexec chmod 0440 /etc/sudoers
```

That was not possible before...  Now I need to test the sudo...

No still get:
[HTML]
sudo: /etc/sudoers is owned by uid 1000, should be 0
sudo: no valid sudoers sources found, quitting
[/HTML]

It's a start.

Also note my Users and Groups app does not open when selected.  I am wondering if that may have some relevance too.

---

### Post by Jonners59 on 2012-02-15
So I get this right, what code do I put in terminal to change /etc from owned by "user" and group "root" to owned by "root" and group "user"?

Then also, how do I recreate sudoers?  I have tried the fixes but I am not sure it is working correctly.

I am also missing my Settings - Users & Groups.  When I select it, nothing happens.  How do I fix this?

---

### Post by Leppie on 2012-02-15
the only way to fix this is to mount the partition in another ubuntu system.
you could boot off a livecd and then mount the affected root partition and cd into it.
then you will be able to change the permissions for the /etc folder:
```
sudo chown <USER>:<GROUP> /etc
```using the -R switch will make it recursive, e.g. it will be applied to all elements in the /etc folder as well. however, not all elements should be owned by root!

it is possible to restore all the permissions correctly this way, but it would be far easier and quicker to just re-install the base system.

---

### Post by dcstar on 2012-02-16
> **Leppie said:**
> 
..........
it is possible to restore all the permissions correctly this way, but it would be far easier and quicker to just re-install the base system.

And reinstalling is a good punishment for being stupid enough to wreck your system this way.

---

### Post by Jonners59 on 2012-02-16
Oohh, you are a hard man!!!!  Glad you were not my teacher at school.

ACtually, all that seems to work.  The problem I now have is that I can not start User Accounts from Settings.  Any ideas, please?

---

### Post by Leppie on 2012-02-16
> **Jonners59 said:**
> ACtually, all that seems to work.  The problem I now have is that I can not start User Accounts from Settings.  Any ideas, please?
That is an indication that it did not work properly. Like I said before, not all files in the /etc folder should have root set as the owner.

---

### Post by Jonners59 on 2012-02-17
Maybe, but surely fixing does not have to be done via punishment.

1st how does one get a list of ownership from a directory.  There must be a command I can use on /etc that lists all the contents and ownership for each.  I can then check that against other machines and correct any that are wrong, though I have manually been through and see no differences, so far.

The User Accounts is only a front end (the accounts are working) so surely that just needs reinstalling, no?

---

### Post by Leppie on 2012-02-17
I've never tried that. 
Somehow I suspect that would involve re-installing the Gnome desktop environment. So, re-installing your base system would be easier and quicker.

---

### Post by Jonners59 on 2012-02-17
OK...  but to make it as painless as possible, is there a way of just installing /etc and keeping my config files such as fstab and samba?

---

### Post by Leppie on 2012-02-17
> **Jonners59 said:**
> OK...  but to make it as painless as possible, is there a way of just installing /etc and keeping my config files such as fstab and samba?
Why don't you save the config files you want to keep to a usb stick prior to re-installing? That way can it doesn't really matter how many times you bork your system.

---

### Post by Jonners59 on 2012-03-10
OK did a reinstall....  Was pleased to see a re-install in the options which I used.

Having installed I find that if I open any windows or directories the PC locks up and windows are so high that the menus are outside the screen and so can not be moved, resized or closed.  I.e. I am currently in Firefox, but once I have finished this reply to go to anything else I now need to reboot as the window fills the screen and access to anything else.

---

### Post by Jonners59 on 2012-03-12
With no help I deleted the partition and reinstalled.  Have new issues now, but this is resolved, not fixed, not ideal.

OK: Update.  It happend again after complete reinstall, but I have what should fix the problem:

Ideally in Recovery Mode (selected from the GRUB boot up menu), but as mine does not work I used the install CD and loaded via the Try Ubuntu option:

Fixing broken soduers serveral options to try:
1.```
 usermod -a -G admin (username)
```
2. ```
addusr (user name) admin
```
3. ```
sudo cp /etc/sudoers /etc/sudoers.backup
sudo nano /etc/sudoers
```

Ensure the following are inn there and do not have a # in front of them.  Add where missing.

```
Defaults env_reset
root ALL=(ALL) ALL
%sudo ALL=(ALL) ALL
%admin ALL=(ALL) ALL
```

```
Control-X
``` then ```
Y
```

if you get "sudo is 123 and should be 440, try
```
chmod 0440 /etc/sudoers
```

then```
EXIT
``` to return to login...

Also consider "Group" in /etc
```
sudo gedit /etc/group
```

Check to which your username is assigned or not.

This is what ultimately fixed my machine

Hope this helps someone.

---

