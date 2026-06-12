---
title: "Method to start/stop services under Upstart"
date: 2011-01-22
forum: General Help
---

### Post by santosh83 on 2011-01-22
Hi all,

If this question has been asked before (almost certainly) please excuse me.

I installed MySQL and Apache2 to develop & test out the site I'm writing. However since I'll be using them purely for internal use (not exposed to the Net), I don't want them to start with every boot-up, but would like to start them manually when I desire, and stop them after use.

With previous Ubuntu (Jaunty) I'd used chkconfig to configure services, but since the current version (Maverick) uses Upstart, is chkconfig still applicable?

I also installed 'bum' (Boot-Up Manager), but strangely, it displays the MySQL server as "unchecked" even though it's running (and starts at boot-up), so I cant see how I can prevent it from starting at boot-up through bum. chkconfig also displays MySQL as not active at runlevel 5, when in fact, it is.

I'd like to know what's the recommended (official) way to configure boot-up services with the Upstart system? I don't suppose directly editing the *.conf files in /etc/init is the best (or even correct) way?

Any pointers is much appreciated. I'll be glad to give any additional information if needed.

Thanks.

---

### Post by santosh83 on 2011-01-23
> **santosh83 said:**
> Hi all,

If this question has been asked before (almost certainly) please excuse me.

I installed MySQL and Apache2 to develop & test out the site I'm writing. However since I'll be using them purely for internal use (not exposed to the Net), I don't want them to start with every boot-up, but would like to start them manually when I desire, and stop them after use.

With previous Ubuntu (Jaunty) I'd used chkconfig to configure services, but since the current version (Maverick) uses Upstart, is chkconfig still applicable?

I also installed 'bum' (Boot-Up Manager), but strangely, it displays the MySQL server as "unchecked" even though it's running (and starts at boot-up), so I cant see how I can prevent it from starting at boot-up through bum. chkconfig also displays MySQL as not active at runlevel 5, when in fact, it is.

I'd like to know what's the recommended (official) way to configure boot-up services with the Upstart system? I don't suppose directly editing the *.conf files in /etc/init is the best (or even correct) way?

Any pointers is much appreciated. I'll be glad to give any additional information if needed.

Thanks.
Since no one has replied (serves me right for posting a FAQ), let me ask a slightly different but related question in the same thread.

While reading the replies to someone else who'd asked pretty much the same as above, I came across the suggestion to add 

> service *service_name* stop

just above the last line of the /etc/rc.local script. My question is:

Using this method to disable any daemon/service stops them **after** they've already been started by the runlevel's init scripts, rather than never starting them in the first place right?

If this is so, then I'd still like to know if there is any other way/tool to control Upstart services other than directly editing the files in /etc/init/ or through jobs-admin (which is unfortunately broken on my system, as of now.)

---

### Post by afrodeity on 2011-01-23
try

```

sudo sysv-rc-conf

```

the space bar checks or unchecks services

---

### Post by santosh83 on 2011-01-23
> **afrodeity said:**
> try

```

sudo sysv-rc-conf

```the space bar checks or unchecks services

In my case this doesn't seem to help. When both apache2 and mysql are enabled, sysv-rc-conf shows them as **not** enabled (the boxes are blank) for all runlevels!

Sysv-rc-conf was the first program I tried. Using Boot-Up Manager I can properly disable apache2 but not mysql, since again it shows mysql as not enabled in the first place, though it's in fact running. Finally I tried jobs-admin, but it fails to start-up here.

I commented out the 'start on...' line in /etc/init/mysql.conf. This does disable the service, but now when I want to start mysql with 

```
sudo service mysql start
```

service complains that there is no such service in the first place!

So finally I've inserted 'service mysql stop' into /etc/rc.local as a sort of stopgap for now, until I can find a better method to control Upstart managed services.

Thanks.

---

