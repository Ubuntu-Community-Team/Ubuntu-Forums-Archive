---
title: "Has any1 had this little problem"
date: 2006-03-29
forum: General Help
---

### Post by megahertza on 2006-03-29
I've recently website with a paid host and go my own domain name. At first Firefox loaded it fine, it did have any problems. Next day, Firefox can not find website. gets stuck on dns lookup. 

I do not have any other DNS problems, and the website loads perfectly in Win Xp. Very Odd.

---

### Post by chocolatetoothpaste on 2006-03-29
you need to be more specific.  What DNS are you using in linux?  Are you behind a firewall?  Or do you have a direct connection to the internet?

---

### Post by megahertza on 2006-03-29
I'm usinf my ISP DNS and I have a direct connection

---

### Post by elamericano on 2006-03-29
That's happened to me, but I didn't have a paid host. Here's the chain of command on the DNS lookup:

1) Your registrar (the company you bought the domain name from) has to assign DNS servers to your domain name. You can check the current assignment here, [http://www.networksolutions.com/whois/index.jsp](http://www.networksolutions.com/whois/index.jsp)

2) Those DNS servers - belonging to your hosting service - have to be responding with the updated info. 'nslookup YOUR_WEB_SITE DNS_SERVER_FROM_STEP_1'

3) And finally, your local ISP needs to be giving your browser the same information. 'nslookup YOUR_WEB_SITE'

If step 1 is pointing to the wrong servers, then you have to call your registrar. If step 2 fails, you should call your website hosting service. And for step 3, you could call your ISP to see what's up.

Anyway, this has nothing to do with Ubuntu. You should be calling the customers service of one of your providers, not posting in a forum. What are you paying those people for :confused:

---

