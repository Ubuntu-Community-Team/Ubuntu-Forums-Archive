---
title: "redirecting a URL to a different server using same domain"
date: 2011-12-09
forum: General Help
---

### Post by spizzuto on 2011-12-09
[COLOR=#000000][FONT=Times New Roman][FONT=arial]Here is what I need to do.  I have a public web site (redhat Linux) and a secured application (windows server 2008).  They run on separate servers but need to share the same domain.  So, the domain name is [WWW.my-domain.com](WWW.my-domain.com).
The Linux server will receive all request.

If a request for the secured server is present it will be sent it to the windows server.  I setup in the host file on the Linux

server the internal address to the windows server hoping it will resolve to that server but it just loops with itself.  

From outside NAT rules send the request to 10.10.0.104 (Linux server) and the Linux server redirects to the window server
10.10.0.19 using the same URL.

**Example**:
    [WWW.my-domain.com/index.jsp](WWW.my-domain.com/index.jsp) will be handled by tomcat on the linux server
but
    [WWW.my-domain.com/forms/R.asp?s=1051](WWW.my-domain.com/forms/R.asp?s=1051) needs to go to the windows server.

If the incoming URL is "notice the WWW is not present" **my-domain.com/forms/R.asp?s=1051** I can redirect to
**[WWW.my-domain.com/forms/R.asp?s=1051](WWW.my-domain.com/forms/R.asp?s=1051)** with no problem. It resolves to the ip of the windows server : remember the
address was set in the host file on Linux.  The problem is! when the URL is actually the same it does not work. Remove the
WWW and it works.  The redirect has to be [WWW.my-domain.com](WWW.my-domain.com).

Any help would be greatly appreciated,

Sam



[/FONT][/FONT][/COLOR]

---

