---
title: "Script to run at resume needs network"
date: 2012-10-08
forum: General Help
---

### Post by Kalliban on 2012-10-08
Hi!
This is my first post here, but I have been reading tips here for a long time. I have a problem that I hope you can help me with. 

I have a script that I wish to run after the computer wakes up from sleep and I have put it in /etc/pm/sleep.d/0000000000_SpinDisksOnServer (the zeros are there because I wished to make sure it was the last thing to run on resume). The script looks like this:

```
#!/bin/bash

case "$1" in
        hibernate|suspend)
                ;;
        thaw|resume)
                WakeUpServer.sh &
                ;;
        *)
                ;;
esac

exit $?

```

And WakeUpServer.sh (which is in /usr/bin looks like this:

```
#!/bin/bash
sleep 5
ssh <username>@<ip-address> sudo spindisks.sh spin

```

The script wants to ssh to my server and run a script there, and it works fine if I run WakeUpServer.sh from the terminal. The problem is that when pm-utils runs the script, the network does not seem to be initialized and hence it fails with "ssh: connect to host <ip-address> port 22: Network is unreachable". 

Is there a way for me to:
[LIST=1]
[*]run the script after the network has been initialized?
[*]initialize the network myself and then run it?
[*]run the script as the user AFTER the computer has woken up completely?
[/LIST]

I am running ubuntu 12.04.

Thank you for your help!

---

### Post by HiImTye on 2012-10-08
I'd increase the time for *sleep* and see if that helps

---

### Post by Rebelli0us on 2012-10-08
Wouldn't it be simpler to send a read or write request to the server?

---

### Post by Kalliban on 2012-10-10
Thank you for your replies! :KS

Rebelli0us: It might be simpler, but I have a whole script thingy going on on the server and the script works fine, just not from the sleep.d. :)

HiImTye: I tried with sleep 8 yesterday, but it still did not work. I will try tonight to increase it a whole lot (like 20 or 30) and see, but I think that the problem is that the network is initialized after the pm-utils sleep.d-scripts has been run.

I will get back to you after I have performed the tests :)

---

### Post by Kalliban on 2012-10-10
You were right HiImTye! I increased the sleep to 15 and then it worked, I really thought that it was enough :)

Thank you for your help!

---

