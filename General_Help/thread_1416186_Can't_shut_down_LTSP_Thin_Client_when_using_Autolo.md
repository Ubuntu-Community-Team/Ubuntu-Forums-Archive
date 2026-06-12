---
title: "Can't shut down LTSP Thin Client when using Autologin"
date: 2010-02-25
forum: General Help
---

### Post by stpgod on 2010-02-25
I just finished setting up a new computer lab at my kids school, using LTSP and 22 think clients connecting to Ubuntu.

Everything is going beautifully, and I'm using static IPs and autologin so that when each computer is turned on it logs itself in with no user intervention. 

The problem is, when users go to the top right system menu and select "Shut Down", they are brought out to the login screen for a second and then immediately logged back in automatically to the Desktop. How should I be shutting down the thin clients?

The only way to do it at the moment is to have everyone hold the power button down until the CPU shuts off, but it feels sloppy and unhealthy. Am I missing something? How should the students me shutting down their sessions?

---

### Post by felixvah on 2010-04-05
> **stpgod said:**
> I just finished setting up a new computer lab at my kids school, using LTSP and 22 think clients connecting to Ubuntu.

Everything is going beautifully, and I'm using static IPs and autologin so that when each computer is turned on it logs itself in with no user intervention. 

The problem is, when users go to the top right system menu and select "Shut Down", they are brought out to the login screen for a second and then immediately logged back in automatically to the Desktop. How should I be shutting down the thin clients?

The only way to do it at the moment is to have everyone hold the power button down until the CPU shuts off, but it feels sloppy and unhealthy. Am I missing something? How should the students me shutting down their sessions?
I have the same problem.  If you figure a way on how to shut them down, please share it with me.  Thank you,

---

### Post by conradin on 2010-04-05
I know there is a difference between the shutdown command and the shut-down program. Im curious if the shutdown command works properly for you.
I would try reinstalling gnome-power-manager or checking the settings there in.

---

### Post by Fionnziegler on 2010-05-06
its because the reboot and shutdown option does the same like logging out and if autologin is true its like a infinitive loop ;). 
What a shame, that there isn't a solution for lucid:
[https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/491940](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/491940)

---

### Post by bpranoto on 2012-09-16
My solution is by creating a script which simply sends halt command to the underlying client's o/s. Here is how I do it:

1. Chroot to the client environment:

```
$sudo chroot /opt/ltsp/i386
```
2. Define root password:

```
#passwd
```

3. Install openssh server and exit from chroot:

```
#apt-get install openssh-server
#exit

```

4. Update the client image:

```
$sudo ltsp-update-image
```

5. Create the down script:

```

#!/bin/bash
my_ip=`printenv|grep SSH_CONNECTION|sed 's/\(SSH_CONNECTION=\)\([0-9]*\.[0-9]*\.[0-9]*\.[0-9]*\)\(.*\)/\2/'`
ssh root@$my_ip halt

```

6. Place a launcher on client's desktop referring to the above script.

---

