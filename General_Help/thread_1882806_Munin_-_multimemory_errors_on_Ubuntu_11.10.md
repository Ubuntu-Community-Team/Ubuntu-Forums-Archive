---
title: "Munin - multimemory errors on Ubuntu 11.10"
date: 2011-11-17
forum: General Help
---

### Post by metalrex on 2011-11-17
Hi,

I couldnt find any record of these errors im getting, maybe someone can point me in the right direction?

On Ubuntu 11.10, installed and configured munin and can visit the munin page.

Then tried to install the multimemory plugin with following commands..

```

cd /usr/share/munin/plugins
sudo wget http://wiki.kartbuilding.net/multimemory
sudo chmod 755 multimemory
sudo ln -s /usr/share/munin/plugins/multimemory /etc/munin/plugins/

sudo nano /etc/munin/plugin-conf.d/munin-node
#add the following:
[multimemory]
env.names apache2 named mysqld

sudo /etc/init.d/munin-node restart
#That should do it. Wait and watch for the graphs.

```

munin-node-configure shows 'yes' next to multimemory.

No multimemory graph shows so I get this in munin-node.log,

```

[13999] Error output from multimemory:
[13999]     Use of uninitialized value $uid in concatenation (.) or string at /usr/share/perl5/Munin/Node/Service.pm line 123.
[13999]     User '' required for multimemory does not exist. at /usr/share/perl5/Munin/Node/OS.pm line 209
[13999] Service 'multimemory' exited with status 29/0.
CONNECT TCP Peer: "::ffff:127.0.0.1:54024" Local: "::ffff:127.0.0.1:4949"
[14047] Error output from multimemory:
[14047]     Use of uninitialized value $uid in concatenation (.) or string at /usr/share/perl5/Munin/Node/Service.pm line 123, <STDIN> line 5.
[14047]     
[14069] User '' required for multimemory does not exist. at /usr/share/perl5/Munin/Node/OS.pm line 209\n    ...propagated at /usr/share/perl5/Munin/Common/Timeout.pm line 66, <STDIN> line 5.
[14047] Error output from multimemory:
[14047]     Use of uninitialized value $uid in concatenation (.) or string at /usr/share/perl5/Munin/Node/Service.pm line 123, <STDIN> line 6.
[14047]     
[14070] User '' required for multimemory does not exist. at /usr/share/perl5/Munin/Node/OS.pm line 209\n    ...propagated at /usr/share/perl5/Munin/Common/Timeout.pm line 66, <STDIN> line 6.
[14047] Error output from munin_stats:
[14047]     munin_stats: File rotated, starting at start
Server closing!

```

This is one of those rare moments that I just cannot work this out on my own after scouring the internets, I come here because this is always the most helpful forum for me :)

---

### Post by raja.genupula on 2011-11-18
[http://www.ubuntugeek.com/monitoring-servers-and-clients-using-munin-in-ubuntu.html](http://www.ubuntugeek.com/monitoring-servers-and-clients-using-munin-in-ubuntu.html) 


i hope that complete guide will be helpful to you.

---

