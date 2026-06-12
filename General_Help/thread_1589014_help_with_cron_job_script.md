---
title: "help with cron job script"
date: 2010-10-05
forum: General Help
---

### Post by jumpjumpholydiver on 2010-10-05
Hi,
I'm new to scripting and I'd love to get help on this following scenario:

I need to run a script twice a day to stop and restart a particular service. 
The start and stop scripts already exist, and are being used in init.d at startup/shutdown/restart. 
So, I need to do the following:
1. Run the script to stop this particular service (the script is called "stop-pent.sh)
2. I then need to verify that the service is in fact stopped, sometimes this takes 2 seconds, sometimes it takes 3 min, it depends on whats  running. I typically check manuall by doing a "ps -ef | grep biserver" until the only result is my grep command.
3. Once the "ps -ef | grep biserver" only returns my grep, I run the start-pent.sh script

So, how do I set up a script that fires of item number one, then keeps running "ps -ef | grep biserver" until the only response is the grep, then it fires off the start script in item #3?

Any help at all woudl be greatly appreciated, thanks!

AG

btw...I'm running Ubuntu 10.04 server.

Thanks!

---

### Post by SeijiSensei on 2010-10-06
Did you model your /etc/init.d scripts on the ones that came with Ubuntu?  Usually the "restart" option takes care of all this for you.

---

