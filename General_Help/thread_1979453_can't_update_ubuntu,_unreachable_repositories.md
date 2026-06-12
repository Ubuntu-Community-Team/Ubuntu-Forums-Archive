---
title: "can't update ubuntu, unreachable repositories"
date: 2012-05-13
forum: General Help
---

### Post by Shwick2 on 2012-05-13
My Ubuntu install can't reach the repository urls archive.ubuntu.com and ca.archive.ubuntu.com.

I've tried updating through the command line and the update manager.

Are they laggy lately or down?

When I boot back into Windows 7 I can ping the repositories, but it takes like 30 seconds for the ping to be acknowledged.

I feel like the ping is timing out on Ubuntu when using the ping command or apt.

Ubuntu 10.04 LTS 32-bit



Update: this has turned into an advanced network problem probably involving the bind server on my ubuntu gateway

The Windows partition on the client can ping archive.ubuntu.com but the name resolves after 30 seconds.

The Ubuntu partition cannot ping archive.ubuntu.com the lookup fails.

I can ping archive.ubuntu.com from the ubuntu gateway without problems.

Based on this I think the gateway is causing the problem due to an incorrect locally defined version of archive.ubuntu.com, which after it fails to resolv after 30 seconds turns to the bind server for a successful lookup.

To find the answer, I'm looking for the difference between a local dns lookup on Ubuntu and a remote dns lookup.  The answer could also be in bind.

Before I start pasting config files are there any ideas?

Keep in mind this setup was working flawlessly for 6 months resolving everything.  Only now that I've booted into my 2nd partition, Ubuntu, did I realize that I couldn't resolv the update archive names, including ca.archive.ubuntu.com, us.archive.ubuntu.com and archive.ubuntu.com.

---

