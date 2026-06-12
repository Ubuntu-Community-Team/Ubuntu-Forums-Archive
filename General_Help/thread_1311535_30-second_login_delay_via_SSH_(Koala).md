---
title: "30-second login delay via SSH (Koala)"
date: 2009-11-02
forum: General Help
---

### Post by jimwillsher on 2009-11-02
Clean install of Koala x64, on a server with 2GB RAM and Quad-core CPU. This is a headless server version.

When I SSH to my server using putty (connecting to 192.168.1.50) I get the SSH login prompt immediately. I key my username, and then get the password prompt. I then key the password. There's then a 20-30 second delay before I get the welcome screen:

===============================================================

Linux wren.jimwillsher.co.uk 2.6.31-14-server #48-Ubuntu SMP Fri Oct 16 15:07:34 UTC 2009 x86_64

To access official Ubuntu documentation, please visit:
[http://help.ubuntu.com/](http://help.ubuntu.com/)

  System information as of Mon Nov  2 19:49:28 GMT 2009

  System load: 0.09              Memory usage: 26%   Processes:       117
  Usage of /:  32.1% of 7.49GB   Swap usage:   0%    Users logged in: 0

  Graph this data and manage this system at [https://landscape.canonical.com/](https://landscape.canonical.com/)

===============================================================

Can anyone suggest what would cause this delay? I don't recall this delay with previous versions of Ubuntu - perhaps 1 or 2 seconds, not 30.

Many thanks,



Jim

PS I have already tried adding the "UseDNS no" entry to sshd_config

---

### Post by jimwillsher on 2009-11-06
Anyone? This is driving me nuts :-(



Jim

---

