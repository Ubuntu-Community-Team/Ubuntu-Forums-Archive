---
title: "Problem starting ssh by crontab"
date: 2010-01-12
forum: General Help
---

### Post by ab275 on 2010-01-12
Hello,
I am having some trouble setting up a cron job that creates a tunnel to my remote machine to work correctly on Ubuntu 9.10. The setup looks like the following: 

(1) myscript.sh (executable)
```

#!/bin/bash
ssh -2 -x -i /home/user/.ssh/id_rsa.prv -L 3128:myremotemachine:3128 myaccount@myremotemachine

```(2) crontab -e, added the following lines: 
```

SHELL=/bin/sh
@reboot /home/user/Scripts/myscript.sh 2>&1 | tee /home/user/Logs/myscriptlog

```(my username, myremotemachine, etc are replaced by real values).

When the computer boots up, the connection is not started, although I can see that the job was executed from the log file. This is what I get in the log file: 
```
 ssh: connect to host myremotemachine port 22: Network is unreachable 
```When I simply manually execute the *same* script from the terminal,  the connection is established normally and the tunnelling works just fine!

How to fix this?

---

### Post by bodhi.zazen on 2010-01-12
Your problem is likely one of concurrency. 

When Ubuntu boots, to lessen boot time, boot scripts run concurrently (rather then sequentially)

So your script is probably running too early, before the network is up.

So you can either :

1. Modify your boot scripts (upstart) to make the connection at boot.

2. Add a sleep to give your system time to boot.

```
#!/bin/bash

sleep 10[FONT=monospace]
[/FONT]ssh -2 -x -i /home/user/.ssh/id_rsa.prv -L 3128:myremotemachine:3128 myaccount@myremotemachine
```

You may need a longer sleep, but 10 *usually* works.

---

### Post by ab275 on 2010-01-12
great, thanks for your help [[COLOR=#980101]**bodhi.zazen**[/COLOR]]("http://ubuntuforums.org/member.php?u=89054")! The connection gets established at startup when I add *sleep*, but it also gets immediately terminated...please see the output:
```

...
[[COLOR=#980101]****[/COLOR]]("http://ubuntuforums.org/member.php?u=89054")debug1: Authentication succeeded (publickey).
debug1: Local connections to LOCALHOST:3128 forwarded to remote address 
debug1: Local forwarding listening on ::1 port 3128.
debug1: channel 0: new [port listener]
debug1: Local forwarding listening on 127.0.0.1 port 3128.
debug1: channel 1: new [port listener]
debug1: channel 2: new [client-session]
debug1: Entering interactive session.
debug1: Sending environment.
debug1: client_input_channel_req: channel 2 rtype exit-status reply 0
debug1: channel 2: free: client-session, nchannels 3
debug1: channel 0: free: port listener, nchannels 2
debug1: channel 1: free: port listener, nchannels 1
debug1: fd 0 clearing O_NONBLOCK
debug1: fd 1 clearing O_NONBLOCK
Transferred: sent 1792, received 1864 bytes, in 0.1 seconds
Bytes per second: sent 31267.5, received 32523.7
debug1: Exit status 0

```

---

### Post by bodhi.zazen on 2010-01-12
Try starting the ssh connection in the background, ie use the -N option, and adding a & at the end of the command.

If that fails, you may need to start the ssh session with nohup

---

### Post by ab275 on 2010-01-12
this works in combination with *sleep 20*. thank you so much for the quick help!

btw, back to the concurrency issue - is it possible to specify what are the load dependencies, e.g. that the script requires the network connection? please give me some pointers on how I could do these things.

---

### Post by bodhi.zazen on 2010-01-12
> **ab275 said:**
> this works in combination with *sleep 20*. thank you so much for the quick help!

btw, back to the concurrency issue - is it possible to specify what are the load dependencies, e.g. that the script requires the network connection? please give me some pointers on how I could do these things.

Not sure what you are wanting to do exactly, but it sounds as if you are considering modifying or adding a boot script. Take a look at Upstart and the current scripts, you could probably add your ssh tunnel to the networking scripts, but, if you do, they may become over written when you update the upstart package.

---

