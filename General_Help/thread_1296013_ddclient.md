---
title: "ddclient"
date: 2009-10-20
forum: General Help
---

### Post by any.linux12 on 2009-10-20
Hi!

I have an email server and the dns is given by dyndns.com. My modem changes the ip address everyday (sometimes 2x), so I decided to install ddclient. The configuration was fine the thing is that it's sending the ip from my server and not the ip of my modem. Basically is sending the ip 192.168.1.3 which is my server (where I installed the ddclient software) and I want it to send the ip gateway from my modem (ip 192.168.1.1).

Is there any way to do that? or for example any command to receive the ip address on my machine?

thanks

---

### Post by Lars Noodén on 2009-10-20
Well, to get the ip number for your gateway automatically requires a bit of trickery, which may or may not stay reliable.

If there is nothing weird about your routing, try this:

```
route -n | egrep '^0.0.0.0' | awk '{print $2}'
```
You can use it like this, too:
```

export EXTERNAL_IPv4=`route -n | egrep '^0.0.0.0' | awk '{print $2}'`
echo   $EXTERNAL_IPv4

```
YMMV

---

### Post by any.linux12 on 2009-10-20
> **Lars Noodén said:**
> Well, to get the ip number for your gateway automatically requires a bit of trickery, which may or may not stay reliable.

If there is nothing weird about your routing, try this:

```
route -n | egrep '^0.0.0.0' | awk '{print $2}'
```
You can use it like this, too:
```

export EXTERNAL_IPv4=`route -n | egrep '^0.0.0.0' | awk '{print $2}'`
echo   $EXTERNAL_IPv4

```
YMMV

doesnt work  as I want. it gives me the address from my router 192.168.1.1 and I want the ip of the gateway in my case 92.107.64.102. Maybe I didn't explain me well

---

### Post by Lars Noodén on 2009-10-20
> **any.linux12 said:**
> doesnt work  as I want. it gives me the address from my router 192.168.1.1 and I want the ip of the gateway in my case 92.107.64.102. Maybe I didn't explain me well

I see.  The gateway actually *is* 192.168.1.1, but that would not be so helpful.  ;)

Here's another try.  It's a screenscraper for myiptest.com and thus has the problems associated with screen scrapers: If the web page changes, the script probably stops working...  

Apologies for awk:

```

wget -q -O - 'http://www.myiptest.com/staticpages/index.php/IP-Lookup' \
  |  awk '/<td class="ip">/   \
      { $0~sub(/<[^>]+>/,""); \
        $0~sub(/<[^>]+>/,""); \
        $0~sub(/[^[:digit:]\.]+/,""); \
        print ;} '

```

The first line uses HTTP GET to get the web page from myiptest and send it to stdout.  
The second line pipes it to awk, which chooses only the lines containing a table element (TD) of the class "ip"
The third and fourth lines get rid of the two html elements.
The fifth line gets rid of anything that is not a digit or a period.

---

### Post by P4man on 2009-10-20
> **any.linux12 said:**
> Hi!

I have an email server and the dns is given by dyndns.com. My modem changes the ip address everyday (sometimes 2x), so I decided to install ddclient. The configuration was fine the thing is that it's sending the ip from my server and not the ip of my modem. Basically is sending the ip 192.168.1.3 which is my server (where I installed the ddclient software) and I want it to send the ip gateway from my modem (ip 192.168.1.1).

Is there any way to do that? or for example any command to receive the ip address on my machine?

thanks

Im confused. Both IPs you give here are private IPs on your local LAN. There is no reason why you wouldnt set those statically?

---

### Post by any.linux12 on 2009-10-20
> **P4man said:**
> Im confused. Both IPs you give here are private IPs on your local LAN. There is no reason why you wouldnt set those statically?

I already got it write. I had to change my ddclient.conf because on use I had use="if=eth0" and now I have use=web, web=checkip.dyndns.com/, web-skip='IP Address'

thanks anyways

---

