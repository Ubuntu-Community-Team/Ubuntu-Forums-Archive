---
title: "SVN sshtunnel using old lan ip: where to change"
date: 2011-10-31
forum: General Help
---

### Post by InkyDinky on 2011-10-31
I have a subversion service setup on my computer.
On my old lan the computer's ip was 192.168.0.3.
On my new lan the computer's ip is 192.168.1.76.
When I issue a svn command it is picking up the old ip and giving me an ssh error saying that there was no route to host.
I set up the service a couple years back and am not sure where svn is getting this ip from.
I've checked 
~/.subversion/config <-only thing I did here was to add the non-standard port to the ssh command
/etc/ssh/ssh[d]_config
and my aliases.
Does anyone know where svn might be picking up the old ip and where I might change it to the new ip.
I know that I can write out the ip in the command and it'll work but would like the shorthand method.
Thanks

---

### Post by InkyDinky on 2012-06-05
I finally found the soluttion.
You need to use the svn switch command.
syntax:svn switch --relocate OLD_URL NEW_URL
e.g. svn switch --relocate svn+sshtunnel://192.168.0.1/home/bob/fu svn+sshtunnel:/192.168.1.1/home/bob/fu

---

