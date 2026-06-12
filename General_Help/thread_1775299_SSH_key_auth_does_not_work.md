---
title: "SSH key auth does not work"
date: 2011-06-04
forum: General Help
---

### Post by hanxue on 2011-06-04
I started an Amazon Web Services EC2 instance of Ubuntu 10.04, and tried to setup FreeNX. When I attempt to connect via SSH again, I just get the general error 

```
Using username "bitnami".
Server refused our key

```

But when I log in using the username **nx** and the default FreeNX DSA private key, I can log in, but not into a proper shell:

```

Using username "nx".
Authenticating with public key "imported-openssh-key"
Linux ip-x-x-x-x 2.6.32-305-ec2 #9-Ubuntu SMP Thu Apr 15 04:14:01 UTC 2010 i686 GNU/Linux
Ubuntu 10.04 LTS

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

  System information as of Sat Jun  4 18:44:20 UTC 2011

  System load: 1.18              Memory usage: 27%   Processes:       132
  Usage of /:  57.2% of 9.84GB   Swap usage:   0%    Users logged in: 1

  Graph this data and manage this system at https://landscape.canonical.com/
---------------------------------------------------------------------
At the moment, only the core of the system is installed. To tune the
system to your needs, you can choose to install one or more
predefined collections of software by running the following
command:

   sudo tasksel --section server
---------------------------------------------------------------------

A newer build of the Ubuntu lucid server image is available.
It is named 'release' and has build serial '20110601'.

     ___ _ _   _  _            _
    | _ |_) |_| \| |__ _ _ __ (_)
    | _ \ |  _| .` / _` | '  \| |
    |___/_|\__|_|\_\__,_|_|_|_|_|

*** Welcome to the BitNami RubyStack 2.1-2 ***
*** Please visit http://bitnami.org/faq/cloud_images
Last login: Sat Jun  4 18:43:55 2011 from 175.136.54.223
HELLO NXSERVER - Version 3.2.0-74-SVN OS (GPL, using backend: 3.5.0)
NX> 105

```

I suspect it is because I mucked around sshd_config. Now I cannot get in via SSH, although I still can get in via FreeNX, but then there is no gnome-terminal or anything that allows me to type a command. Direct root login is disabled by default. 

Any clue how I can recover access to my server instance?

---

