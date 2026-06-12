---
title: "Block all traffic except whitelist"
date: 2011-12-01
forum: General Help
---

### Post by Valpskott on 2011-12-01
At my job I got the task of setting up some computers for the local library in town. The ordinary Internet kioskes are all done, but the library also would like a couple of machines that are restricted to certain sites (library catalogue site and a couple of other sites).

The way the system works on these machines is that GDM autologins on a profile with a custom session which only launches firefox (no desktop enviornment). Upon restart, the computer will reset the profile. Any firewall used to block everything except the sites on a whitelist should have to be activated during boot (probably via scripts if I need to add new sites in the future via ssh).

I've started fiddling with iptables but I can't seem to figure out how to make it drop all outbound traffic except certain webpages.

Any help with the scripts(preferably sh script), or if there is a GUI for iptables with the option to only allow sites on a whitelist, would be apprechiated. I also need port 22 open so I can reach these machines through SSH.

---

### Post by DroidVPN on 2011-12-01
You might want to use a Squid Proxy instead of using iptables to block websites since ip addresses of websites can change.

Another easy way is to use OpenDNS and block all domains and just whitelist the domains you want to use.

---

### Post by Valpskott on 2011-12-06
Are these softwares installed locally on the computer? Cause I can't setup a server over at the library.

Also, I could not find Open DNS nor Squid Proxy in the Ubuntu repos, only admin tools for them.

---

### Post by Valpskott on 2011-12-06
I found a workable solution for our needs. An add on for Firefox that both has "block all" and complementary whitelist functionality.

[https://addons.mozilla.org/en-US/firefox/addon/procon-latte/](https://addons.mozilla.org/en-US/firefox/addon/procon-latte/)

Maybe not the most secure solution out there, but I think it's sufficient in our setup (no desktop enviornment, and the user profile is recreated during restart).

---

