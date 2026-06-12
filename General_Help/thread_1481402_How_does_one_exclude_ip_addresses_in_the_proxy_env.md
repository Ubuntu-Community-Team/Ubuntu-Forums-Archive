---
title: "How does one exclude ip addresses in the proxy environment variable?"
date: 2010-05-12
forum: General Help
---

### Post by robkey on 2010-05-12
Hi I have set my environment variable for a proxy server as such
export http_proxy=http://username:password@10.6.26.256:3128 
which works fine. wget rsync etc all use this proxy automatically. The problem is when I access other 10.x.x.x addresses on my private network all access goes through the proxy and is slow.

How can I exclude 10.0.0.0 and 127.0.0.1 from the proxy server so that all applications obey this?

Thanks,
  Rob Key

---

### Post by obaid on 2010-05-12
i think in ubuntu there is a utility in gnome panel -> preferences -> proxy

can you setup your proxy there ?

---

### Post by robkey on 2010-05-12
Solved, one can set the environment variable

no_proxy=elecfs.cput.ac.za,10.6.29.89

to avoid using the proxy to access these ip addresses.

Also add the following to the end of the sudoers file: /etc/sudoers
Defaults env_keep="no_proxy http_proxy https_proxy ftp_proxy XAUTHORIZATION \
XAUTHORITY TZ PS2 PS1 PATH MAIL LS_COLORS KRB5CCNAME HOSTNAME HOME DISPLAY COLORS"and then when you do a sudo apt-get install package the no_proxy will be available to the sudo command.

Thanks,
 cheers,  Rob key
:)

---

### Post by robkey on 2010-05-12
Hi and thanks, I don't use gnome only the command line but the best way to do it is to use the no_proxy environment variable. See my reply to myself!
Cheers,
  Rob Key

---

