---
title: "cups service not running after  update"
date: 2010-07-10
forum: General Help
---

### Post by 3pinner on 2010-07-10
Running 10.04, just installed a ton of updates from Update manager.
Printer is HP Officejet 6210
Everything working fine up until after installing updates
When I  try to print I get error message. Starting to troubleshoot tells me that CUPS service is not running, 
when I try to locate using [http://localhost:631/](http://localhost:631/) I cannot connect.
Checking Synaptic it seems everything is installed that should be.

So how do I start/restart this CUPS beastie?

Thanks

---

### Post by 3pinner on 2010-07-10
solved:
sudo service cups start works

Lucid is almost more trouble than its worth

---

