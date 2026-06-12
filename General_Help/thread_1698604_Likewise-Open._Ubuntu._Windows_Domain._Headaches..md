---
title: "Likewise-Open. Ubuntu. Windows Domain. Headaches."
date: 2011-03-02
forum: General Help
---

### Post by Roasted on 2011-03-02
I thought this was easy? Anyway, I'm trying to add an Ubuntu system to our Windows domain at work. A few things came about.

First, I found a bug report that told me why I was not able to join the Windows domain. I had to edit /etc/nsswitch.conf and edit out the line regarding "hosts: files mdns4_minimal...." and reboot. Once done, I was able to join.

Okay, fine. But now I'm trying to LEAVE the domain, and it's giving me an error. So I shut off the lsassd service and bam, I could leave.

Okay, so now I want to rejoin. See what I'm doing here? I'm trying to repeatedly test this to see how it fairs. Well I go to rejoin and I get DNS_ERROR_BAD_PACKET.

Be blunt with me. Am I wasting my time using Ubuntu in an enterprise environment with a Windows domain?

---

### Post by Roasted on 2011-03-03
Uppp. Need this to work.

---

### Post by Roasted on 2011-03-03
So I ended up purging the 5.4 install in the repos and installed 6.0 with a .sh file I found on their site. It seems as if the issue is gone. The only thing is I DO have to edit the /etc/nsswitch.conf file. But once done I can seem to join and leave the domain as much as I want without headache.

That being said, I can't help but to wonder why. Did everybody have this much trouble on 5.4? What about 6.0 magically changed to (what seems to be) much easier?

---

### Post by asmoore82 on 2011-03-03
Yes, this software does work and I have seen it work firsthand.
Yes, it is largely also a waste of time :D.

You are always allowed to leave a domain when the services aren't actually
talking to the domain. But it cannot contact the domain to tell it is gone.
So, subsequent re-joining to the domain the machine is seen as a duplicate
anomaly or worse a trojan impostor! You need to manually delete the machine
account from AD before attempting a re-join.

Obviously, a centralized Linux authentication system plus true NFS mounts is much
preferred. I anxiously await the day when I get to try this setup for myself.

---

### Post by Roasted on 2011-03-03
> **asmoore82 said:**
> Yes, this software does work and I have seen it work firsthand.
Yes, it is largely also a waste of time :D.


These seem like contradictory ideas. Can you elaborate on what you mean?

> **asmoore82 said:**
> 
You are always allowed to leave a domain when the services aren't actually
talking to the domain. But it cannot contact the domain to tell it is gone.
So, subsequent re-joining to the domain the machine is seen as a duplicate
anomaly or worse a trojan impostor! You need to manually delete the machine
account from AD before attempting a re-join.

Obviously, a centralized Linux authentication system plus true NFS mounts is much
preferred. I anxiously await the day when I get to try this setup for myself.

I was going to contact the network admin to ask if it got removed. This is good information. I would have assumed it would have just dumped overtop of the existing one. Is it really *that* bad to have duplicates? Don't they expire after a certain amount of time of inactivity?

---

### Post by asmoore82 on 2011-03-04
> **Roasted said:**
> These seem like contradictory ideas. Can you elaborate on what you mean?
Joining Linux to AD is playing microsoft's game by microsoft's rules.
The point being: microsoft always wins. The very existence of such software
partially validates microsoft's ridiculous marketing jargon that AD is end-all
be-all of enterprise system management and is the proof incarnate that Linux is
not suitable for massive scale, cost effective deployment.

The marketing jargon all falls apart someday when microsoft is eventually forced
to admit that AD can't do it all. At that point they say you also need to fork out
even more cash for SMS or SCCM or whatever other expensive acronyms they dream up.

> **Roasted said:**
> I was going to contact the network admin to ask if it got removed. This is good information. I would have assumed it would have just dumped overtop of the existing one. Is it really *that* bad to have duplicates? Don't they expire after a certain amount of time of inactivity?
I've never heard of machines expiring from AD but it's certainly possible that
it's configurable. The big deal about duplicates is that machines in AD must have
permission to do certain things, such as read permissions on all policies
applied to them. The machines have these permissions completely independent
of the permission status of the users of that machine. So, an intruder could be
manipulating a lookalike machine to gather information that he otherwise
should not be allowed to access.

---

