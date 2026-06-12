---
title: "&quot;S&quot; key always goes to system menu in VNC since 9-&gt;10 upgrade"
date: 2010-05-09
forum: General Help
---

### Post by greggman on 2010-05-09
I just upgraded to 10.04 and almost everything worked but ...

I can't type the "S" key anymore. It doesn't matter where I am, in a terminal, in Firefox, anywhere I type "S" the system menu in the top right corner of the screen drops down and I'm no longer in the window I was originally typing in.

Note, I'm VNCed to the machine. If I use the machine directly or through a remote shell, no problem but if I'm VNCed, which is how I normally access the machine, then I get this "S" problem.

Also, I'm VNCed to it's own desktop. Meaning I'm not sharing the main desktop.

Any ideas how to fix this? I'm not sure even where to start looking.

---

### Post by narnia on 2010-05-10
I got the same problem here since I upgraded from Ubuntu 9.10 to 10.04TLS. 

"s" key always goes to system menu, and "d" key always goes to email/chat. All the other keys are fine.

I am using "vnc4server" in the server side, and "vnc viwer 4" as the client.

---

### Post by oyeaussie on 2010-05-10
I have the same issue. my D letter works fine, but my S always points to the system menu on the top right.
Anyone knows whats going on?

---

### Post by snash on 2010-05-11
I can't type lowercase s. Uppercase S is fine.
s brings up the menu of "Lock Screen, Logout....etc

Ubuntu 10.04LTS
vnc4server
tried two different vncviewers from two different platforms, with identical result.

Xvnc4 4.1.1
UK keyboard layouts.

---

### Post by houldsworth1 on 2010-05-11
Same issue here.  I can get around it by using SSH for terminal server stuff from my main PC but this is a PIA.  
 
Anyone have a solution?

---

### Post by snash on 2010-05-13
Here is another thread discussing a similar issue:
[http://ubuntuforums.org/showthread.php?t=1464342](http://ubuntuforums.org/showthread.php?t=1464342)

---

### Post by houldsworth1 on 2010-05-13
Not that this is a good solution but... I ended up doing a clean install of 10.04 (long story) and have not had the same issue. I know that isn't really an option for most people, but it does mean that it isn't a problem with 10.x.

---

### Post by snash on 2010-05-13
If you right-click on the 'shutdown' button, top right, you get the option to remove it from the panel.
Once removed, my s key is now doing what I want.
I think I can live without it, we'll see.

---

### Post by axtimwalde on 2010-05-14
I had the same problem today, but now, it's gone.  I have no idea what in the line of things that I did was the reason but that's what I did:

The problematic run of vnc4server was through an ssh-tunnel via a very old firewall with crazy language settings, that is, I ssh-ed on the terminal of this firewall to the computer with vnc4server and started vnc4server there.  That always gives me a bunch of complaints about weird locales

vnc4server :2 -localhost
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LC_MONETARY = "en_US.ISO8859-1",
    LC_NUMERIC = "en_US.ISO8859-1",
    LC_MESSAGES = "C",
    LC_COLLATE = "en_US.ISO8859-1",
    LC_CTYPE = "en_US.ISO8859-1",
    LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").

To this server, I could connect through the tunnel but it had the above mentioned  `s` problem.  Then I did a bunch of things:

1. Killed vnc4server
2. ssh-ed to the server through the tunnel which leaves appropriate locales
3. sudo apt-get update & sudo apt-get upgrade & sudo reboot
4. ssh-ed again through the tunnel and started vnc4server again (no complaints about locales)
5. connected via xtightvncviewer -via "-p<tunnel> localhost" :2 (no `s' problem!)
6. restarted vnc4server through the firewall terminal (complains about the locales but also no `s' problem

Despite that I am happy that it's gone, I have no idea what on the way made it work.  Either the upgrades fixed the problem or somehow vnc4server healed itself fixing some broken options.

---

### Post by ZYV on 2010-05-17
Thanks, this hint worked for me. But I'd like to keep the shutdown button. Did anyone narrow down the issue to which configuration options are causing this on upgrade? Might be a good idea to test on a newly created user, by the way.

---

