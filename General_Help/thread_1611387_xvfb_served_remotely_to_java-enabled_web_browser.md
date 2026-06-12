---
title: "xvfb served remotely to java-enabled web browser"
date: 2010-11-01
forum: General Help
---

### Post by bcarl17 on 2010-11-01
Hello,

What I have is Xubuntu running as a VM with VirtualBox on my Windows 7 Media Center that is always on.  I am trying to be able to remotely access an X display on that box to do network auditing/ various linux stuff from the various places I go.  I would like it to be as simple as possible and leave no trace on the remote computer, so what I would like is to use a java-enabled browser to connect to an xvfb on xubuntu with SSL encryption.  I ALMOST got it working using cherokee/x11vnc/desktop.cgi but it only works once or twice and I get network errors even on localhost.  I would rather just not have X running all the time on the VM and just have an xvfb display waiting/created when I log in remotely from a browser.

Any help would be greatly appreciated.

Thanks

---

### Post by krunge on 2010-11-03
x11vnc can do SSL enabled java applet access via browser to a temporary X session (Xvfb, you need to apt-get it).

[INDENT][http://www.karlrunge.com/x11vnc/faq.html#faq-userlogin](http://www.karlrunge.com/x11vnc/faq.html#faq-userlogin)[/INDENT]

here is the main inetd line to enable this:
```

5900 stream tcp nowait root /usr/sbin/tcpd /usr/bin/x11vnc -inetd \
      -o /var/log/x11vnc.log -http -prog /usr/bin/x11vnc -svc

```
You then point your java-enabled web browser to [https://hostname:5900](https://hostname:5900) where "hostname" is the name or IP addr of the machine with the above inetd service.

There are other ways to do similar things described there as well.

---

