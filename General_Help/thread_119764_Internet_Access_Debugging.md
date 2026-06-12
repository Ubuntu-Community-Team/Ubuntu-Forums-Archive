---
title: "Internet Access Debugging"
date: 2006-01-20
forum: General Help
---

### Post by SteveF on 2006-01-20
Recently, when I restarted my PC and logged into Ubuntu, I could not access the internet.  I thought maybe somethign was wrong with my router and tried logging into it (using web browser and local ip address).  The browser would not load the web page.  It was at that point that I realized I had no idea what to do to fix the problem.

I rebooted into Kubuntu (I have both installed) and I was able to get on.  I rebooted to Ubuntu and had no problems.  So it must have been some glitch.

But for future reference, what are some ways to debug what happened (or is happening) so that I can try to fix the problem.

Thanks for any information,

Steve

---

### Post by stream303 on 2006-01-24
> 
But for future reference, what are some ways to debug what happened (or is happening) so that I can try to fix the problem.

Most of my soho problems revolve around DNS issues.  Thus whenever I have a problem, I doublecheck my **/etc/resolv.conf** file to see if the proper domain name servers of my isp are being referenced.

More often than not, I find that there is no nameserver referenced at all, or perhaps the nameserver is pointing to the dns services of a local piece of hardware that I don't want doing dns - I want the isp dns.

The symptom of this is either a total failure to resolve any names, or unusually long delays when loading pages in a browser while waiting for the "wrong" dns server to time out.

I've written several messages about editing /etc/resolv.conf manually for a temporary fix, or editing /etc/dhcp3/dhclient.conf for more long-term solutions.

I wrote up a [generic article about it]("http://www.greertech.com/nixnotes/dhcpfix.html") if anyone is interested

---

