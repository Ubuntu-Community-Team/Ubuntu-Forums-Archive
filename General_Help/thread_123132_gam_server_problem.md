---
title: "gam server problem"
date: 2006-01-29
forum: General Help
---

### Post by lungdart on 2006-01-29
What is this Gam server? I find myself frequently having to kill it off because it is using over 700megs of RAM. and turns my computer into a slug.

Is it safe to kill? Why does it keep coming back? how much ram should it normally consume and what reasons would it have for using 700megs?

---

### Post by GeneralZod on 2006-01-29
gam_server is used to inform applications of whether or not a file has been altered - it is the successor to famd, the File Alteration Monitor Daemon, which also caused massive headaches when it was used.

I've never had any problems with gam_server under Kubuntu, but have heard of severe memory leaks similar to yours.  Here's the current memory usage on my system; it's pretty miniscule, and should stay at about the same size:

```

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
10939 simon     15   0  3228 1692  788 S  0.0  0.3   3:42.36 gam_server

```

I'm not sure whether or not it is safe to kill; in a sanely written and modular system, it shouldn't be a necessity, but killing it will obviously remove some functionality - for example, I think gam_server is used for automatically updating the GNOME menu when a new app is installed.  I'm not sure what is responsible for re-spawning it when it is killed.

---

### Post by chele on 2006-02-14
I ran into this and found that upgrading the gamin package fixed the problem. [Gamin packages from Dapper]("http://ubuntuforums.org/showpost.php?p=551050&postcount=9")

---

### Post by jonrkc on 2006-05-24
It's safe to kill gamin on Hoary Hedgehog, at least that's my experience; I have to do it almost every time some program requests gam-server.  It seems KDE apps (I don't run KDE, but I use some of the apps) frequently call upon gamin, and a few seemingly can't run without it.  I've never had any problem whatever after killing gamin, but you have to kill the parent process, AND you have to rename the gamin directory (or similar) action BEFORE killing the parent process, because gamin immediately respawns.  It's a real pain.  

I was just lucky and glanced at gkrellm this morning and my CPU was heated to 112 degrees F., the hottest it's ever been.  So I looked at CPU usage and it was steady at 99%, even though I didn't notice any slowdown in operations.  Sure enough, killing gamin solved the problem as it does every time.

Really annoying and apparently very, very common problem.  I upgraded to a package a year ago that was supposed to fix it, and it had no effect.

---

### Post by rutty on 2006-05-25
I killed it today while it was using 750Megs of my RAM, which is nice.

I'll keep an eye on it until I upgrade to Dapper I think - never had this issue with Hoary IIRC though

---

### Post by Lord Illidan on 2006-07-29
I'm sorry about bringing up this thread, but I recently had severe probs with gam_server and Kubuntu, such that it brought my whole machine to a crawl. I went and renamed the executables in /etc and /usr relating to it.

So far everything works...I am just curious, what does gam_server really do? And will my actions have a side effect?

---

### Post by jonrkc on 2006-07-29
> **Lord Illidan said:**
> I'm sorry about bringing up this thread, but I recently had severe probs with gam_server and Kubuntu, such that it brought my whole machine to a crawl. I went and renamed the executables in /etc and /usr relating to it.

So far everything works...I am just curious, what does gam_server really do? And will my actions have a side effect?
I've renamed it (with something conspicuous like .DISABLED as a second suffix) many a time because of it crippling my computer.  So far I have not noticed one single bad effect from that.

Gam-server keeps track of the status of files involved in the programs that call upon it to do that.  It seems to be for the convenience of the programs and certainly not for the convenience of the user.

This problem with gam-server crippling machines has been in existence for a LONG time, has hundreds of threads about it on the Web, and seems to be continually in a state of "about to be fixed" or "finally fixed" (but not really); it's a nuisance among my top, say, five nuisances.

I don't un-disable it unless something refuses to run without it, which is very rare.  And I will try to find an alternate application that doesn't require the *$!* thing if I can.

I think you're quite safe.

---

### Post by kebes on 2006-08-16
Refer to this other thread for a solution to the annoying "gam_server uses 99% CPU" problem:

[http://www.ubuntuforums.org/showthread.php?t=210329&highlight=gam_server](http://www.ubuntuforums.org/showthread.php?t=210329&highlight=gam_server)


The presented solution allows gam_server to keep running, so no functionality is lost, but the CPU usage is brought to a reasonable level. It worked for me.

---

### Post by ffi on 2007-09-03
This solution doesnt work for me Xubuntu Feisty, the problem seems to be specially bad when copying files to my removable disk.

What do the options 'notify' and 'poll' mean in gaminrc?

---

