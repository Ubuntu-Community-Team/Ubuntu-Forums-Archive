---
title: "Proxy configuration mess"
date: 2010-05-04
forum: General Help
---

### Post by hpalma on 2010-05-04
I'm having trouble in reaching to a correct proxy configuration in Kubuntu Lucid.

This is the problem, i want to configure a global proxy so that every application uses it. The only i've found to do this is to set the http_proxy, https_proxy, ftp_proxy and no_proxy variable and then on the the KDE proxy settings set "Use preset proxy environment variables". I've found that if i set the proxy directly in KDE and don't use env. variable applications like gaim and skype don't use the proxy settings.

But with this configuration i've found:
- either konquerer and firefox don't use my proxy settings. It seems they only use the proxy settings if i manually specify them on KDE. In fact, most KDE application don't recognize the proxy with this configuration.

- chrome uses the provided proxy settings but ignores the no_proxy setting.

Any ideas would be appreciated.
Thanks in advance.

---

### Post by hamparawa on 2010-07-20
I'm having the same problem here...
fixed the problem in Ubuntu with the help of this thread,
[http://blog.zenlinux.com/?p=366](http://blog.zenlinux.com/?p=366)

but it does not work in Kubuntu

---

