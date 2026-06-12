---
title: "wget not connecting to internet"
date: 2011-12-30
forum: General Help
---

### Post by rng on 2011-12-30
I am Lubuntu 11.10 and I connect to internet through a proxy server. The connection is working well for firefox but not for command line applications such as wget or axel. The error message for wget is: 

> with wget: 
Resolving xxxx.xxx.xx.... failed: Name or service not known.
wget: unable to resolve host address `xxxx.xxx.xxx'

with axel: 
axel: Unable to connect to server xxxx.xxx.xxx:80   (axel appends ":80" to all urls) 
What could be the reason and how can I solve this? Also how can I setup proxy server settings in Lubuntu?  (I have done it in firefox but it may not be for whole system- there is no option in system tools, unlike ubuntu).

---

### Post by Rodney9 on 2011-12-30
This might help - 

[http://digiassn.blogspot.com/2006/10/wget-using-wget-through-proxy-server.html](http://digiassn.blogspot.com/2006/10/wget-using-wget-through-proxy-server.html)


For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by rng on 2011-12-30
Thanks, it worked. But I need to type it every time I open a terminal. Will it be always there if I give this command in /etc/rc.local ? Also, how can I check whether this variable is there in the environment?

> export http_proxy=http://proxy.example.com:8080

---

### Post by Lars Noodén on 2011-12-30
Put it in [font=Courier New].bashrc[/font] and it will be there every time you open a shell.

You can see the value of [font=Courier New]http_proxy[/font] like this:

```

echo ${http_proxy}

```

---

### Post by rng on 2011-12-30
Thanks. But will it work if I keep it in /etc/rc.local, and what is the difference?

---

### Post by Lars Noodén on 2011-12-30
It won't work if you put it in [font=Courier New]/etc/rc.local[/font].  If you want to apply it to all accounts globally then the place to put it would be [font=Courier New]/etc/bash.bashrc[/font].  That is the place for such settings.

---

### Post by gsgleason on 2011-12-30
just do this from terminal:

```
echo 'export http_proxy=x.x.x.x:port' >> ~/.bashrc
```

---

