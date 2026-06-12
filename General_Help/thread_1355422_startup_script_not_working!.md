---
title: "startup script not working!"
date: 2009-12-14
forum: General Help
---

### Post by deewanagan on 2009-12-14
hi geeks,

i have a script that i want it to run at startup, but i can't get it to work. its some iptable policies. i added the script to the /etc/init.d/ directory then run "update-rc.d FOO defaults", and also made the script executable, but it won't start whenever i boot. any ideas why? 
*ubuntu 8.10

tanx

---

### Post by PseudoLemon on 2009-12-14
Dunno why it's not booting, but go to Startup Applications and enter the path to the script. If it needs sudo to run right, then add that at the beginning. It should look something like "/home/username/rest/of/path/script.sh" or whatever. If that doesn't work, then do the same but with a . before the "/home" part.

---

### Post by john newbuntu on 2009-12-15
I am assuming you have permissions set right and that you are able to see your script linked in /etc/rcX.d directory, where X is your runlevel.  Make sure your script ends with exit 0.  Also try changing its sequence number.  Make it the last job to be run, like S99...
You could also try throwing your script in /etc/rc.local to get it to work in all runlevels.

---

