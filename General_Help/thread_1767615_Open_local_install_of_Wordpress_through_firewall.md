---
title: "Open local install of Wordpress through firewall"
date: 2011-05-25
forum: General Help
---

### Post by greavette on 2011-05-25
Hello,

I have a local install of Wordpress and I've added a port forward rule in my firewall to share our site with family and friends (we're using a members only plugin).  I have a DYNDNS account and my router automatically updates with this account.

The problem I'm having is when I test accessing our local site from outside my network.  I use my dyndns account name and port number to access my local Wordpress, I can see the login screen but once I login, the url changes from my dyndns name to the IP Address of my local server and then I never see any pages on my site.  

I'm thinking it has something to do with either the WordPress address (URL) or the Site address (URL) since they currently have the ip address of my local ubuntu server that hosts our Wordpress site.

So what have I configured incorrectly here?  Any thoughts you may have would be greatly appreciated.

Thanks.

---

### Post by webofunni on 2011-05-25
You need to change WordPress address (URL) and the Site address (URL) to your dyndns name.

---

### Post by greavette on 2011-05-25
Hello and thank you for the response.

I've tried that before (I was running a bitnami vm of Wordpress to test) but once I changed my WordPress address (URL) and the Site address (URL) by removing my IP address and adding my dyndns account name, I wasn't able to access our site from inside or outside our network.  I assumed I did something wrong when I did this.

Now that I'm running Wordpress on an Ubuntu Server VM installed from scratch (and I have a backup), should I change these settings in my General Settings and then restart Apache and try it again?

Thanks,

---

### Post by webofunni on 2011-05-25
what is the dyndns name that you are using ? is that a domain name ?

---

### Post by greavette on 2011-05-26
It's my hostname at dyndns.com.  I have a free account with them.

---

### Post by webofunni on 2011-05-26
I guess it will be like something.dyndns.com. You need to change the wordpress URL to yourhost.dyndns-or-something-else.com

---

