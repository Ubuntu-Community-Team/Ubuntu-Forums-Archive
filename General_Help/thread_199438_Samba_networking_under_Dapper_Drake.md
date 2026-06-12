---
title: "Samba networking under Dapper Drake"
date: 2006-06-18
forum: General Help
---

### Post by killernurd on 2006-06-18
I've got a few questions that so far I've been unable to find answers to.

I'm running Dapper Drake on my own machine, but the other two machines currently on the network are both running Win98. The only printer currently available is attached locally to one of the Win98 machines.

Onwards.

First, printing.
Printing worked just fine under Breezy. I set my machine on the network, set the Win98 machine to share the printer, told Breezy, 'look on this machine for this printer' and it worked. Printed everything I threw at it time and time again (with a few errors because Win98 overloaded or crashed or somesuch nonsense).

Now, running Dapper, I cannot get my machine to register the presence of the Win98 machine. Period. It's not there at all. I attempt to create a new printer, but the Win98 machine isn't listed in the available computers, and the printer isn't seen at all. I tried filling in the details manually, but that just caused the smbspool to hang and go nowhere.

Second, filesharing on the network.
Under Breezy, it worked perfectly fine, when I had it enabled on the Win98 machines. I'd enable it, reboot, and browse the neighborhood and find my Samba server in there. I could read all the files and it worked perfectly using share-level security.

Now, my machine won't see the Win98 machine (even when the Win98 machine has shares enabled), and the Win98 machine won't see mine (which *always* has shares enabled).

Too - when attempting to diagnose the problem on my end, I discovered that the HOWTOs all mentions a Windows Network setting area in the normal Netoworks admin tool, but I don't see it. When I modify the Samba config manually and then use testparm, it ignores several of the options I have (and yes, I've gone through the file and made sure they were all uncommented, several times).

If anyone can, would they be willing to shed some light on this matter?

---

### Post by nix4me on 2006-06-18
Printing to windows has nothing to do with samba.  It uses ipp.  There are a multitude of posts on the forums about how to get printing to work.

As far as filesharing.  Try going to Places->Connect to Server->Windows share and manually enter the ip of the box with shares.  That should allow you to see them.

nix4me

---

### Post by killernurd on 2006-06-18
Argh.

Well, looking into the solutions you presented, I discovered the problem...

I have Firestarted running, and it was keeping traffic out, even though I had told it to let traffic for Samba through.

I will note for the record that despite printing to a Windows machine being IPP, it's still handled through SMB (which isn't the same thing as Samba, but it is represented by Samba on the Linux side).

---

