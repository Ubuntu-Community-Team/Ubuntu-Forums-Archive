---
title: "Downloaded command"
date: 2009-11-10
forum: General Help
---

### Post by SpinningAround on 2009-11-10
Is there a way to check the amount downloaded and uploaded? The command ifconfig | grep TX wont only return the amount. My explanation isn't very good but what I'm trying to say is that i looking for someway to check the amount downloaded with a command.

So that the following can work

//get downloaded
down = $(get downloaded)
if("$down" -gt 1 GB) //GB, Byte, KB, MB
...

make any sense? :lolflag:

---

### Post by hwttdz on 2009-11-10
vnstat might be what you are looking for.  I had to chmod 777 /var/lib/vnstat before I added my interface to the monitored list.  And I find that to "watch" network traffic "watch "vnstat -u -i eth0; vnstat"".

---

### Post by SpinningAround on 2009-11-11
Nice program it have the information i want :) only question is how do I get the info out?

I wish to get the 6.22 MB out so it's saved into a variable 
```

Database updated: Wed Nov 11 09:15:01 2009

	eth0

	   received:       7.17 MB (100.0%)
	transmitted:        415 kB (0.0%)
	      total:       7.58 MB

	                rx     |     tx     |  total
	-----------------------+------------+-----------
	yesterday      1.19 MB |     171 kB |    1.36 MB
	    today      5.98 MB |     244 kB |    6.22 MB
	-----------------------+------------+-----------
	estimated        --    |      --    |      --   



```

---

