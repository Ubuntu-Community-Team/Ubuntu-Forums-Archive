---
title: "Public IP"
date: 2009-12-21
forum: General Help
---

### Post by Skidbladniir on 2009-12-21
How do I go about getting my public Internet protocol address?  I'm running server, so don't say, 'Go to [http://whatismyip.com/](http://whatismyip.com/)' or else you'll force me to download gnome.

---

### Post by mac666 on 2009-12-21
Their must be a command for this but my question is,
how do you connect to the server, if you dont know the IP?
If you are on the same LAN, you should se the IP in the router, etc?

---

### Post by Grenage on 2009-12-21
```
traceroute google.com
```

That should show you your external IP as it leaves.

---

### Post by sisco311 on 2009-12-21
[http://www.whatismyip.com/automation/]("http://www.whatismyip.com/automation/")

```
IP="$(wget -q -O - http://www.whatismyip.com/automation/n09230945.asp)"
echo $IP
```

---

### Post by StuartN on 2009-12-21
Oops - too slow again...
```
wget -q -O - http://www.whatismyip.com/automation/n09230945.asp
wget -q http://checkip.dyndns.org/
```

---

### Post by wojox on 2009-12-21
```
w3m -v http://www.whatismyip.com/automation/n09230945.asp
```

---

### Post by Grenage on 2009-12-21
> **w3m** -v [http://www.whatismyip.com/automation/n09230945.asp](http://www.whatismyip.com/automation/n09230945.asp)

I had no idea that existed, cheers!

---

### Post by pbrane on 2009-12-21
To simplify one the the earlier posts:

```

echo "$(wget -q -O - http://www.whatismyip.com/automation/n09230945.asp)"

```
works too.

This would be good in a script.

---

### Post by stinkeye on 2009-12-21
```
curl 'http://www.whatismyip.org'
```

---

### Post by Skidbladniir on 2009-12-21
All of those: -bash command x not found

---

### Post by lewisforlife on 2009-12-21
What does your router say your IP address is?  From your computer you can really only check your computer's IP address.  If you have a router connected to the "outside world", than you would have to check your router's IP.  If you are not sure how to do this, look in your router's documentation.

---

### Post by Grenage on 2009-12-21
All of those (bar one) should be installed by default on Ubuntu!

---

