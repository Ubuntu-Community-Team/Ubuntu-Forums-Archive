---
title: "Need help creating a script"
date: 2009-09-11
forum: General Help
---

### Post by sr_guy on 2009-09-11
I have a ubuntu box that both runs mythtv, asterisk, and freepbx on it. From time to time if I need to reboot the box, I am having an issue with asterisk loading my configured trunks for some reason. I usually end up logging into asterisk CLI and run "reload" to reload the config, which starts the trunks. 

How can a script be configured to accomplish:

1. start asterisk -r
2. within asterisk CLI run "reload"

So at bootup I can reload the trunk setup automatically

---

### Post by lykeion on 2009-09-11
Hi
I've no experience with mythtv or asterisk but a quick search for the man page for asterisk gave me:
```
-r   Connect to Asterisk running in the background and present a command line interface
-x  In combination with -r, execute an Asterisk CLI command 
```

So I guess the asterisk command you want is:

```
asterisk -r -x reload
```

To create a script doing this is easy:

1. Startup a text editor (gedit vim or whatever) and add this text:
```
#!/bin/bash
asterisk -r -x reload

```
2. Save
3. To make it run you have to make it executable:
Right-click script file > Properties > Permissions > Check "Allow executing file as program" (or use chmod +x from command-line)

I'm not sure whether you want this to be done at every bootup, but to make a script run at bootup see:
[http://ubuntuforums.org/showthread.php?t=208954]("http://ubuntuforums.org/showthread.php?t=208954")

Hope this helps...

---

### Post by NoaHall on 2009-09-11
I think it would be 
```
#!/bin/bash
asterisk -r
asterisk -x reload

``` If the one above doesn't work, that is.

---

### Post by sr_guy on 2009-09-11
Will any script run automatically upon bootup if it has read/write access and is in /etc/init.d directory?

---

### Post by Codix121 on 2009-09-11
To run a script automatically, just go to your SYSTEM > PREFERENCES > STARTUP APPLICATIONS


and you set the "Command" to the location of your .sh (script file)
and it'll load on boat, that's how my conky loads xD!

---

### Post by Liolikas on 2009-09-11
>Will any script run automatically upon bootup if it has read/write access and is in /etc/init.d directory?
No.

OR customize /etc/rc.local script with your lines or just dump link to your script.

---

### Post by lykwydchykyn on 2009-09-11
> **sr_guy said:**
> Will any script run automatically upon bootup if it has read/write access and is in /etc/init.d directory?

No.

scripts in /etc/init.d are a special format, and need to be written to take start/stop/restart commands.  Then it'd need to be symlinked to /etc/rcX.d where X is the run level, etc.

Just call the script (or put the commands) into /etc/rc.local.

---

