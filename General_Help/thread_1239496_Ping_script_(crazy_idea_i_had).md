---
title: "Ping script (crazy idea i had)"
date: 2009-08-13
forum: General Help
---

### Post by juicyoner on 2009-08-13
I'd like to write a ping script that pings a hosts until it comes online and the call a system beep.

Any ideas on how to do this w/ a bash script?

---

### Post by juicyoner on 2009-08-13
Just so ppl understand this is because I am constantly shutting down and restarting apache/tomcat while developing and would like to know immediately when it comes back up.

This is NOT for any kind of malicious hacking

---

### Post by doas777 on 2009-08-13
I'd do it in python, but is a pretty trivial task. 
[http://www.daniweb.com/forums/thread118801.html](http://www.daniweb.com/forums/thread118801.html)

---

### Post by Martje_001 on 2009-08-13
I wonder how ping could be used for hacking.. anywayzz:
```
#!/bin/bash

# Configuration
HOST= 'www.google.nl'
INTERVAL='1' # Seconds
# /Configuration

# Is the server online?
while true; do
 ping "$HOST" -c 1 > /dev/null 2>&1
 if [ "$?" = "0" ]; then
  # Yes it is!
  break
 fi
 sleep "$INTERVAL"
done

# Let's beep
beep # Sidenote: I don't have a pc-speaker, so I don't know wheter it works or not.

```

---

### Post by doas777 on 2009-08-13
> **Martje_001 said:**
> I wonder how ping could be used for hacking.. anywayzz:



scanning a subnet to id the hosts online. lots of good reasons to do it, but lots of bad ones too.

---

### Post by juicyoner on 2009-08-13
[SIZE="3"]Thanks so much![/SIZE]

I just remembered that when tomcat goes down, apache is still running. So this doesnt really work anymore. I dont think there is a way to run a command and see if tomcat is up.

Maybe w/ 'ps aux | grep -i tomcat'?

And idea how I could incorporate this? Perhaps if the ps returns a process (besides the 'grep -i tomcat' process), it could run the beep.

Hmm.

---

### Post by Martje_001 on 2009-08-13
Well, you could:
[LIST=1]
[*]Ping the machine to see if it's online
[*]Then scan if ssh is available and login
[*]Run 'ps x' and see if tomcat is up
[*]Beep!
[/LIST]
I'm not motivated enough to program all that, sorry :P. 

I'm sure you can do it with Python, without too much trouble.

---

### Post by Tibuda on 2009-08-13
> **juicyoner said:**
> [SIZE="3"]Thanks so much![/SIZE]

I just remembered that when tomcat goes down, apache is still running. So this doesnt really work anymore. I dont think there is a way to run a command and see if tomcat is up.

Maybe w/ 'ps aux | grep -i tomcat'?

And idea how I could incorporate this? Perhaps if the ps returns a process (besides the 'grep -i tomcat' process), it could run the beep.

Hmm.

What about
```
if [ `pidof tomcat` ]; then
  # something here
fi
```

---

