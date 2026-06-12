---
title: "How do I run one simple command on login?"
date: 2006-02-12
forum: General Help
---

### Post by k00zk0 on 2006-02-12
Hey guys, I've been looking around on how to get my WUSB11 workign with breezy and I eventually found out how.

The problem now is that every time I login it starts up with wlan0 deactivated.

Ive looked and looked for fixes and I tried the "activate wireless on startup" tip that was posted in the thread on "Speeding up boot-up with InitNG.

Well, I boot in about 2x less time now, but wireless still doesnt start when all the rest of my apps start.

I know that i must run ONE command as root, "ifup wlan0"

This activates my wireless and connects me. My question now is.. how do I run this command at login? I would think that running it during OS boot up would be too early, but i may be wrong.

Somethign else I noticed is that when booting into recovery mode, I see that it issues the command "ifdown wlan0" sometime near the end, and gets a response that wireless isnt configured (which is what I get if i type that into a terminal). This could be turning my wireless off when I boot into normal mode. I tried searching a "contains this text" search for "ifdown wlan0" through the whole filesystem, but found nothing. I think if someone could tell me where this string is located, I could replace it in that file with "ifup wlan0".

Yes it does say "auto wlan0" in my interfaces file, it just doesn't start it no matter what.

So.. how do I run this command during login?

Thanks

---

### Post by nanotube on 2006-02-12
well, the easiest would be to go to your system>preferences>sessions, and add that command to be run on login (in the startup programs tab).
seems like that would do what you want.

---

### Post by k00zk0 on 2006-02-12
Genious! Why didn't I think of that :P

The only problem is the command needs to be run as root, and sudo asks for a password.. so.. is there any way to stick the password into the sudo command so it will run without requiring user input?

thx.

---

### Post by codejunkie on 2006-02-12
[QUOTE=k00zk0]Genious! Why didn't I think of that :P

The only problem is the command needs to be run as root, and sudo asks for a password.. so.. is there any way to stick the password into the sudo command so it will run without requiring user input?

thx.[/QUOTE]
follow the guide here and set sudo to not prompt for password
[http://ubuntuguide.org/#usesudowithoutpasswordprompt](http://ubuntuguide.org/#usesudowithoutpasswordprompt)
and to launch the command use ```
sudo nameofcommand
```
just note that doing this is not secure but it will do what your asking for.

---

### Post by k00zk0 on 2006-02-12
Is there a way to make it just run sudo that one time with with no password prompt?

I really dont want to unprotect access to sudo like that...

EDIT: Maybe something with gksudo or gksu?

---

### Post by codejunkie on 2006-02-12
[QUOTE=k00zk0]Is there a way to make it just run sudo that one time with with no password prompt?

I really dont want to unprotect access to sudo like that...

EDIT: Maybe something with gksudo or gksu?[/QUOTE]
you might try looking up some info on writing a shell script for launching your app as  root that doesn't prompt for the password im not sure on how to do it but it should be possible.

---

### Post by nanotube on 2006-02-13
hmm...
well you could just try chmodding the "ifup" command to suid.
(as in, "sudo chmod u+s /sbin/ifup",) and then whenever you run it it will run with root permissions)
of course, note that that will enable any user on your system to run ifup with root privileges... but if you are the only user on your system, it should present no problem.

---

### Post by nanotube on 2006-02-13
oh... or another thing you could do, is just add that command to a startup script and place it toward the end of your initialization stuff. 
so you would create a simple shell script with the following contents:

```
#!/bin/bash
ifup wlan0
```

and place it in /etc/init.d/mycustomifup, eg.
then you would run
```
sudo update-rc.d /etc/init.d/mycustomifup defaults 55
```
from a terminal to place the appropriate symlinks to actually run your script. (the 55 would specify a fairly late-in-the-game execution time for it).

---

### Post by k00zk0 on 2006-02-13
Thanks for all the help guys.

Making a startup script and running that command didn't help at all, like it still starts up with wifi disabled. I think it has somethign to do with the fact that I'm using InitNG instead of the normal startup method, but I tried in both modes (InitNG and normal) to no avail, but I have found a solution. Using nanotube's idea of making ifup run in su by default, I'm now able to simply add a shortcut to the top of my screen.

Hey wait. I can just put ifup wlan0 into the startup programs for this session! w00t! This doesn't work with without nanotube's idea though, as it still prompts me for a password.

Thanks for everything guys. I think this is the fastest responding and most helpful forum I've EVER been on.

kudos.

On a side note, I notice that sometimes when I leave my laptop running idle for a few minutes, it starts having massive hard drive activity. Is it doing something like auto-rearranging files for faster startup? or is this not normal?

---

### Post by nanotube on 2006-02-13
hey
i am glad that you managed to make it work. congrats. :)
sorry, i have no clue about the hard drive activity thing. 
in fact, i would be curious to know if there is a way to see which processes are currently accessing the disk. ... anyone?

---

### Post by RAOF on 2006-02-13
There's always the "lsof" program - that lists what files are open by what processes.

---

### Post by nanotube on 2006-02-13
hey... by the way, i figured out a more "ubuntu" way of running the "ifup wlan0". it essentially achieves the same thing, but allows only YOU to run it without a password as root, not everyone, like the chmod u+s method.
to do this, you edit your sudoers file (by running "sudo visudo") and add the following line to it:
```

username ALL = (ALL) NOPASSWD: /sbin/ifup
```

where you replace "username" with your actual username on the system. once you do that, you can run "sudo ifup wlan0" without entering your password - but only that command, and only you. well, just for your information, if you feel like playing with it. :) since chmod u+s method works for you, you dont have to try this, but it is more "fine grained control".

---

### Post by nanotube on 2006-02-13
hey raof,
hm, lsof is interesting... but is there a way to list only the files that are /currently/ being read/written to? lsof by itself lists an awful lot of things that are "open" but that doesnt say anything about hd activity. any ideas?

---

### Post by gitfiddler on 2006-02-14
You could try the "top" command. I noticed some unusual hard drive activity myself, but running that command showed me it was just the auto-update routine. Whew!

---

### Post by k00zk0 on 2006-02-14
err. guys. shit.

Like, running the "top" command shows me that 126 out of 128 megs of RAM is being used on my laptop. Here's a screenie of top running.

[klickx0r.]("http://70.24.241.125/top.png")

If you notice firefox using almost 20% of ram there, its because I always have it running on workspace 2, so i can just control+alt+rightarrow right into firefox instead of waiting 5 or 6 seconds for it to start. Even without firefox running it still uses about 98% of my RAM normally.

Dont mind Xorg using all that CPU, it's because the update time is set really low for "top" (0.2)

So what can I do or remove to use less memory? Another question, will switching to KDE help? I see KDE has much more options for visual stuff... so I'm guess it uses much more mem and cpu, but what do I know compared to you guys :P

Another question, I want to make a shared folder (networked) on my laptop so I can read or write files from/to it from a Windows PC. How can I do this?

Thanks for the 41,937st time.

---

### Post by mgmiller on 2006-02-14
Hi, I network from windows to ubuntu all the time.  You need to turn on and configure some services in the Ubuntu machine and when it's done, you would just browse to the local ip address of your Ubuntu computer.  (mine is 192.168.1.4)  give it your user name and password and you should see your home directory.  It's shared by default once you do all this stuff.  Here is a lengthy, but easy to follow set of instructions.  Good Luck:

Install samba and smbfs from synaptic package manager.
Next
sudo gedit edit /etc/samba/smb.conf

you need to change the default work group from MSHOME to HOME
further down in the file you can make the share writable by changing no to yes.
# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
   writable = yes

    Save the edited file 

you need to also add users to samba

sudo smbpasswd -a system_username

this first command is to create a user name and password.
For example:
The command "sudo smbpasswd -a marty"  will create user marty and then prompt several times for a password. just type it in when asked.

issue command to restart samba:
sudo /etc/init.d/samba restart  

At this point it should work.  The following is just for further instructions.

##I did not need the following##
sudo gedit /etc/samba/smbusers

insert the following line into the new file
system_username = "network username"
##I did not need the above##

    To edit network user

sudo smbpasswd -a system_username

    To delete network user

sudo smbpasswd -x system_username

Q: How to share home folders with read only permission (Authentication=Yes)?

   1. Read General Notes
   2. Read How to install Samba Server for files/folders sharing service?
   3.

sudo cp /etc/samba/smb.conf /etc/samba/smb.conf_backup
sudo gedit /etc/samba/smb.conf

   4. Find this line

...
;   security = user
...

   5. Replace with the following lines

   security = user
   username map = /etc/samba/smbusers

   6. Save the edited file (sample)
   7. Read How to add/edit/delete network users?
   8.

sudo testparm
sudo /etc/init.d/samba restart

Q: How to share home folders with read/write permissions (Authentication=Yes)?

   1. Read General Notes
   2. Read How to install Samba Server for files/folders sharing service?
   3.

sudo cp /etc/samba/smb.conf /etc/samba/smb.conf_backup
sudo gedit /etc/samba/smb.conf

   4. Find this line

...
;   security = user
...

   5. Replace with the following lines

   security = user
   username map = /etc/samba/smbusers

   6. Find this section


   7. Replace with the following lines

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
   writable = yes

   8. Save the edited file (sample)
   9. Read How to add/edit/delete network users?



Once started, any changes you make to /etc/samba/smb.conf, need to be put in place by restarting the service - just swap the word "start" with "restart" 

command to start or stop or restart:
/etc/init.d/samba start

---

### Post by k00zk0 on 2006-02-14
Oh my god wow I love you. All of you.

I haven't even tried this yet, and I wanted to say THANK YOU SO MUCH for typing all that out. err, you did right?

hehe.

ubuntuforums.org = t3h_best.

---

### Post by nanotube on 2006-02-15
gitfiddler: where do you see hard drive activity in top? i looked and could not see it...

k00zk0: dont worry about the memory usage, linux is pretty efficient about that. most of it is probably just cache. also, kde generally /is/ more resource hungry than gnome, so you are probably better off with gnome. 

but if gnome is "too slow" for you, you could try xfce, it is supposedly more responsive... (to do that, install package "xubuntu-desktop" then you can choose it as one of the sessions when you log in).

---

