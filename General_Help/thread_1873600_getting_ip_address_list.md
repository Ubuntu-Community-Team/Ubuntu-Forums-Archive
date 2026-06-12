---
title: "getting ip address list"
date: 2011-11-01
forum: General Help
---

### Post by LuniTux on 2011-11-01
Hello,

I am trying to get a list of all active IP addresses in my network. I am able to do this using:

```
#! /bin/bash
for i in {1..254}; do
	x=`ping -c1 -w1 192.168.1.$i | grep "%" | cut -d"," -f3 | cut -d"%" -f1 | tr '\n' ' ' | sed 's/ //g'`
	if [ "$x" == "0" ]; then
		echo "192.168.1.$i"
	fi
done 
```

but I would like to be able to do this using python or php so that I can display the information on a web page.
I would also like the method to be a bit faster if possible. The current method I am using takes approx 4 min to scan...

Thanks

---

