---
title: "installing squid"
date: 2011-03-02
forum: General Help
---

### Post by slaz on 2011-03-02
Hi,

I am trying to make a proxy server. I want to install squid with some options. 
--enable-storeio=null ( this is the option I want to use)
can I do this with the sudo apt-get install squid --optionsIwanttouse
Or what command could I use to do this.

thanks,
slaz

---

### Post by blueridgedog on 2011-03-02
I think that is a runtime option for squid, so I would install it with apt-get, then configure the launcher for the service to use your option or code them into the configuration file.

---

### Post by blueridgedog on 2011-03-02
Here are the options for runtime:

[http://wiki.genunix.org:8080/wiki/index.php/Configure_options_-_squid](http://wiki.genunix.org:8080/wiki/index.php/Configure_options_-_squid)

---

