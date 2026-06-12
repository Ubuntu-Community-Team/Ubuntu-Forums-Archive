---
title: "LTSP problems with Natty (Unity problems)"
date: 2011-08-29
forum: General Help
---

### Post by stpgod on 2011-08-29
I'm trying to upgrade my LTSP computer lab to Natty, and a couple of computers are showing a black screen after the PXE dialog. I found the following in Syslog, and I think the issue is due to the new Unity:

ubuntu kernel: [73435.535518] unity_support_t[21142] general protection ip:70f85a sp:bf901a50 error:0 in libGL.so.1.2[6f9000+49000


Any thoughts on how to disable Unity for the LTSP thin clients, or a workaround for the machines that boot to black screen? I've spent days searching and found nothing to fix the issue.

---

### Post by Hakunka-Matata on 2011-08-29
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

There are a massive amount of issues with 11.04 causing black screen on first boot after install.  The thread above has over 500 posts and it's one of the most complete dealing with the problem.  If stability is important, I'd go back to 10.10 for stability.  I use 11.04 in Ubuntu Classic mode, not Unity, I don't even like Unity.  Hope this helps, and I should think you can change the server copy to PXE with the correct fixes, hope so anyway.

**EDIT:  Apologies, I misunderstood, or better said did not understand what "LTSP" was.  I now know, thanks, I like it.**

---

### Post by Ubutuxer on 2011-11-23
Found a solution to this. LDM_SESSION and LDM_XSESSION parameters in /opt/ltsp/i386/etc/lts.conf do NOT work, but try this:

**Create a file called .xsession in the users' home folders with content:**

```

if [ -n "$SSH_CLIENT" ]
then
    setxkbmap fi &
    exec /usr/bin/startxfce4
fi

```

Obviously, change the keymap "fi" to the one you are using. I am from Finland, hence the Finnish keyboard layout. Without this line, the keyboard seems to be stuck at "us" (some bug in LTSP).

Also, if you're not using XFCE for the clients, change the latter line to the relevant one as well. The if-clause makes sure these commands only get executed for LTSP clients, not for the local users.

---

