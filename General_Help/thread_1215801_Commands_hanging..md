---
title: "Commands hanging."
date: 2009-07-17
forum: General Help
---

### Post by apoth on 2009-07-17
There's a server at work (RHEL4, I'd replace that in an instant if I could!) which works fine when I SSH over the local network.

However, when I SSH over VPNC from home I'm getting commands hang. If I do an ls ~ it works, but if I do an ls /etc it hangs after printing out the ls. If I do an ifconfig, it hangs. If I run some of my own bash scripts they work, if I echo text > into a file it works. If I do an strace /bin/ls /etc strace displays the initial execve line as expected and then hangs itself!

Any ideas? Thanks. BTW this was fine until recently, I've found a post online where someone saw similar behaviour after a network card was upgraded, which may have happened here for all I know.

---

### Post by blueridgedog on 2009-07-17
I do not have an answer, but If I were troubleshooting such a problem, I would get a tcpdump window open on the local side and watch the packets, then on the remote side and see who stops talking.  That would help me look at either the local, remote or VPN gear.

---

### Post by ronaldprettyman on 2009-07-17
> **apoth said:**
> There's a server at work (RHEL4, I'd replace that in an instant if I could!) which works fine when I SSH over the local network.

However, when I SSH over VPNC from home I'm getting commands hang. If I do an ls ~ it works, but if I do an ls /etc it hangs after printing out the ls. If I do an ifconfig, it hangs. If I run some of my own bash scripts they work, if I echo text > into a file it works. If I do an strace /bin/ls /etc strace displays the initial execve line as expected and then hangs itself!

Any ideas? Thanks. BTW this was fine until recently, I've found a post online where someone saw similar behaviour after a network card was upgraded, which may have happened here for all I know.

What are you using to authenticate, is it caching to the local system(the server not your home machine), or is it a local account?

Is your home folder on the same filesystem? Is it a networked filesystem. Or any of the shares down?

What does dmesg show?

If your performace is fine in one directory and jacked in another I'd look at the logs and see whats mounted. Does "df" cause a stutter vs df -F ext3(2 4)
Is this from a privledged account?

---

