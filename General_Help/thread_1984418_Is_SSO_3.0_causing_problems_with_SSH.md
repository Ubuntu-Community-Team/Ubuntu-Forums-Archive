---
title: "Is SSO 3.0 causing problems with SSH"
date: 2012-05-21
forum: General Help
---

### Post by paulg500 on 2012-05-21
On Friday, May 18 my SSH tunnel from an MS Windows computer at work to my Ubuntu computer at home was working fine - it was working since November of last year and continued to work after upgrading to Ubuntu 12.04.  Monday morning I got to my office and attempted to open my SSH tunnel to my home Ubuntu computer as I do every morning.  Suddenly it no longer worked.

I checked the software center to see what updates might have run between Friday afternoon and Monday morning and found that on Saturday the SSO 3.0 updates had been applied to the machine.

I have already gone through a number of exercises to determine that the SSH software is running and listening on port 22 but when I attempt to connect using either locally, using "ssh -v localhost" or remotely using Putty on my windows machines as I always have done, I get the log on attempt rejected.

Given that SSO is concerned with Single Sign On I am wondering if this update might be causing some hidden problem.

All help is appreciated.

Thanks,
Paul

---

