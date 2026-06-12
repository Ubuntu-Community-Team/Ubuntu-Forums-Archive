---
title: "Startup events"
date: 2006-02-27
forum: General Help
---

### Post by DarkHorizon on 2006-02-27
Hi all!

I'm running a Breezy host as the gateway machine on my network, and one of the problems I have been having is the order in which services launch. I run a webserver on a DSL connection, and have a network behind this. These main three uses of my server don't initialize in proper order (dsl connection, firewall script, then various services), in fact, the pppoe client doesn't want to launch at all even after configuring it via the setup interface and I must start it up manually each reboot. Additionally, because I have multiple domains aliased in Apache, I suspect it's attempting to perform a DNS lookup, and failing, so I must restart Apache manually after connecting DSL manually (otherwise all domains point to the default DocumentRoot).

Before I switched to Ubuntu, I was using Redhat 9, and simply placed these startup events in a bash script; I'm more comfortable doing this, so maybe I should look into pulling them from the autostartup service feature?

I'd like to know more about the services setup, can anyone point me in the direction of some newbie-centric documentation? I have a few articles from around the web, but any particularly comprehensible ones would be appreciated :)

Best regards,
- DH

---

### Post by Xian on 2006-02-27
[QUOTE=DarkHorizon]I'd like to know more about the services setup, can anyone point me in the direction of some newbie-centric documentation?[/QUOTE]

To manage your services I would install sysv-rc-conf. 
The man page is extensive and easy to understand:

$ man sysv-rc-conf

---

