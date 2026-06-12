---
title: "Apt configuration for proxy"
date: 2009-09-04
forum: General Help
---

### Post by apparle on 2009-09-04
I have a private repository which does not require any proxy.
And the normal ubuntu requires proxy to connect to internet.
Also I have the environment variable 'http_proxy' set as required.

Now everytime I use apt-get, it does not take values from the apt.conf.d/proxy file but it takes from the environmental variable http_proxy.

Can I configure apt in such a way that it does not read the environment variable but reads the values from apt.conf.d/proxy

---

### Post by bodhi.zazen on 2009-09-04
Can you give us more details on your set up ?

Usually I configure a proxy in the browser , as a proxy server for http is mos t common.

---

### Post by apparle on 2009-09-05
I have [http://10.1.101.150:3128](http://10.1.101.150:3128) proxy for normal net use

Also I have private repository setup at the ip address 10.1.11.48
This private repository does not connect through proxy. It has to be connected directly.

I have this in /etc/apt/apt.conf ```
Acquire::http::Proxy::10.1.11.48 "DIRECT"; 
```

I have the environment variable 'http_proxy=http://10.1.101.150:3128'

The environment variable overrides the apt.conf settings.
If I unset the 'http_proxy' variable then everything works fine.

But I require the 'http_proxy' for wget etc.
Can I make any settings such that apt does not see the environment variable but directly the apt.conf file.

---

### Post by bodhi.zazen on 2009-09-05
I am not sure, but I would script it. A simple alias would do it as well.

---

