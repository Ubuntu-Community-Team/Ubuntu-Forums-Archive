---
title: "Problem using resolver and gethostbyname"
date: 2011-04-29
forum: General Help
---

### Post by TonyC1 on 2011-04-29
I'm not sure if this is the correct place to post this, but I'm hoping someone can help.  I have a C++ program which uses a resolver and gethostbyname.  I need to be able to pass IP addresses to different DNS servers on the command line which are not in /etc/resolv.conf.  When I do this, I first call res_init() in the program to initialize the resolver and then update the _res struct with the new IP address.  However, when I run the program the server I specified is ignored and the first server in resolv.conf is used.  This only happens on my Ubuntu 11.04 server but works correctly on Red Hat and Fedora.  I checked my /etc/hosts and /etc/resolv.conf and they are the same format as my other servers.  I also changed the "hosts: " line in /etc/nsswitch.conf to "files, dns" but it didn't make a difference.  Here is a code snippet:

      res_init();
    _res.nscount=1;
    _res.nsaddr_list[0].sin_family=AF_INET;
    _res.nsaddr_list[0].sin_port=htons(53);
    _res.nsaddr_list[0].sin_addr.s_addr=inet_addr(server);

    struct hostent *ent = gethostbyname(command);

I read the man pages and tried to set RES_DEBUG both through res.options and using the /etc/resolv.conf "options debug" but I don't see anything when I run the program (I assume they should be going to STDOUT?)

I hope someone can help me!  Thank you.

---

