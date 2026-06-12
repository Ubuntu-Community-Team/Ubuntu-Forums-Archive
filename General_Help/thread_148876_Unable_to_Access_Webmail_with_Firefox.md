---
title: "Unable to Access Webmail with Firefox"
date: 2006-03-22
forum: General Help
---

### Post by umm Sahlah on 2006-03-22
Hello,

I am trying to access my various webmail accounts (i.e. Hotmail, Gmail, Yahoo!) with Firefox and I am having problems. Basically Firefox just continues to load and never finishes loading so I never see the login screen.

Could this be a problem with my Internet settings? I am connected through an Ethernet DSL connection.

Anyone experience this or know the solution? Thanks in advanced!

---

### Post by sands on 2006-03-22
Most of the webmails use SSL..
If u r using a proxy in firefox..just check the "Use this proxy server for all Protocols" button..

If this is not the case pendown back...

---

### Post by Kereru on 2006-03-22
I had the same problem but on dial up (while I waited for the broadband to be connected), no access to secure pages and some search pages with long urls. Seemed like a DNS problem. It came right when the broadband was switched on)

Suggestions I found for similar problems were 

- disable IPv6 in Firefox 
- check DNS and DCHP etc  
- try with another browser (Konqeror)

---

### Post by aysiu on 2006-03-22
I second the motion to try another browser (Konqueror, Epiphany, or Dillo).

If it works with another browser, it's a Firefox issue. If it works with no browser, it's an internet configuration issue. Of course, if you are having real internet problems, you probably can't install those browsers.

Can you connect to *other* (non-webmail) sites through Firefox?

---

### Post by umm Sahlah on 2006-03-23
Hi,

I am not using proxy so I cannot use that option. Everything else is accessible on the web except for all Web Mail services - Yahoo, Hotmail, Gmail etc.
Is there any other option i can use..if not then i'll try to switch to another web browser.

Thanks again!

---

### Post by frodon on 2006-03-23
First, try another browser to see if the problem come from firefox or not.

Before trying to disable ipv6 try that : 
1- type in the firefox address bar "about:config" and then set the parameter *network.dns.disableIPv6* to true.
2- Install the [User Agent Switcher]("https://addons.mozilla.org/extensions/moreinfo.php?id=59&application=mozilla") extension of firefox because some sites only allow windows browsers to get in, so with this extension you can surf with an IE or netscape signature.

If it still don't work my next question is do you use firestarter ?

---

### Post by mcoomes on 2006-03-25
In Firefox choose Edit then Preferences then Advanced click do not use OSCP for certificate validation.

This also fixed gmail access.

---

