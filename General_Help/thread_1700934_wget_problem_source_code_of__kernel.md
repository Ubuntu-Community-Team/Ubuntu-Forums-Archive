---
title: "wget problem: source code of  kernel"
date: 2011-03-05
forum: General Help
---

### Post by vivek.pandey on 2011-03-05
hi everyone 
    i was trying to download the source code of the kernel using wget but i am facing an error message

vivek@NEO:/tmp$ wget [http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.38.tar.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.38.tar.bz2)
Error parsing proxy URL [http://localhost:4001](http://localhost:4001) : Bad port number.
vivek@NEO:/tmp$ 

can anyone please tell why am i getting this error and how to rectify it

thanx in advance

---

### Post by asmoore82 on 2011-03-05
That's sounds like a mis-configured or maybe even compromised system.
Have you tried to set any proxy settings for yourself?

Try this and see if you get any results: ```
set | grep -i prox
```

Mine (10.04 LTS) looks like this: ```
			-find -s -nice -nouserlib -noclasspath -autoproxy \
			url proxy fetch push mirror skipDefaultUpdate
		core.gitProxy
		http.proxy
                COMPREPLY=($( compgen -W "$opts --percent --force                 --test --replacepkgs --replacefiles --root                 --excludedocs --includedocs --noscripts --ignorearch                 --dbpath --prefix --ignoreos --nodeps --allfiles                 --ftpproxy --ftpport --justdb --httpproxy --httpport                 --noorder --relocate --badreloc --notriggers                 --excludepath --ignoresize --oldpackage                 --queryformat --repackage --nosuggests" -- "$cur" ));
                            COMPREPLY=($( compgen -W "$opts --ftpport --ftpproxy                         --httpport --httpproxy" -- "$cur" ));
		PreferredAuthentications Protocol ProxyCommand \

```

The "smoking gun" we're looking for would be a line that looks
something like "PROXY=" or "HTTP_PROXY="

---

### Post by vivek.pandey on 2011-03-06
> **asmoore82 said:**
> That's sounds like a mis-configured or maybe even compromised system.
Have you tried to set any proxy settings for yourself?

Try this and see if you get any results: ```
set | grep -i prox
```

Mine (10.04 LTS) looks like this: ```
			-find -s -nice -nouserlib -noclasspath -autoproxy \
			url proxy fetch push mirror skipDefaultUpdate
		core.gitProxy
		http.proxy
                COMPREPLY=($( compgen -W "$opts --percent --force                 --test --replacepkgs --replacefiles --root                 --excludedocs --includedocs --noscripts --ignorearch                 --dbpath --prefix --ignoreos --nodeps --allfiles                 --ftpproxy --ftpport --justdb --httpproxy --httpport                 --noorder --relocate --badreloc --notriggers                 --excludepath --ignoresize --oldpackage                 --queryformat --repackage --nosuggests" -- "$cur" ));
                            COMPREPLY=($( compgen -W "$opts --ftpport --ftpproxy                         --httpport --httpproxy" -- "$cur" ));
		PreferredAuthentications Protocol ProxyCommand \

```

The "smoking gun" we're looking for would be a line that looks
something like "PROXY=" or "HTTP_PROXY="

thanx for an immediate response... i had slept off so couldnt reply back here is what i get as output
vivek@NEO:~$ set | grep -i proxy
HTTP_PROXY='http://localhost:4001 '
http_proxy='http://localhost:4001 '
            -find -s -nice -nouserlib -noclasspath -autoproxy -main'             -- "$cur" ));
        PreferredAuthentications Protocol ProxyCommand PubkeyAuthentication \
vivek@NEO:~$

---

### Post by vivek.pandey on 2011-03-07
bump?/

---

### Post by asmoore82 on 2011-03-07
Did you set or were you aware of that localhost:4001 proxy?

A few legitimate tools such as persistent web caches and
privacy "onion" routers are specialized proxy servers.

If you didn't set up any of the above I would change the thread title to
something about a security breach or compromised system investigation.

If you did install some type of privacy tool, the googled fix for this issue is: ```
sudo apt-get purge anon-proxy
```Sources:
[http://www.linuxquestions.org/questions/linux-networking-3/error-parsing-proxy-url-http-localhost-4001-bad-port-number-770509/](http://www.linuxquestions.org/questions/linux-networking-3/error-parsing-proxy-url-http-localhost-4001-bad-port-number-770509/)
[http://forums.debian.net/viewtopic.php?t=310&](http://forums.debian.net/viewtopic.php?t=310&)

---

### Post by vivek.pandey on 2011-03-07
> **asmoore82 said:**
> Did you set or were you aware of that localhost:4001 proxy?

A few legitimate tools such as persistent web caches and
privacy "onion" routers are specialized proxy servers.

If you didn't set up any of the above I would change the thread title to
something about a security breach or compromised system investigation.

If you did install some type of privacy tool, the googled fix for this issue is: ```
sudo apt-get purge anon-proxy
```Sources:
[http://www.linuxquestions.org/questions/linux-networking-3/error-parsing-proxy-url-http-localhost-4001-bad-port-number-770509/](http://www.linuxquestions.org/questions/linux-networking-3/error-parsing-proxy-url-http-localhost-4001-bad-port-number-770509/)
[http://forums.debian.net/viewtopic.php?t=310&](http://forums.debian.net/viewtopic.php?t=310&)

well i dont remember any such proxy but how to know that i mean is there any command which tells i have so so and so proxy application running?

---

### Post by oldos2er on 2011-03-07
I get a '404 Not Found' with your URL.

---

### Post by vivek.pandey on 2011-03-07
> **oldos2er said:**
> I get a '404 Not Found' with your URL.

are you talking about the url i am trying to wget...well its not the matter of url..any url i am trying i am getting the same problem. is it a compromised system problem..

---

### Post by oldos2er on 2011-03-07
Yes, that URL. Just kind of curious as to where you obtained it.

---

### Post by vivek.pandey on 2011-03-07
> **oldos2er said:**
> Yes, that URL. Just kind of curious as to where you obtained it.

i was trying to download the lattest version of kernel so that i can compile it.... i got the url from some website where it was like x.y.z where x y z refer to the parts in kernel version i mean that decimal parts are there in kernel name 2.6.38 something like this so i was just trying to download it..

---

### Post by oldos2er on 2011-03-07
As far as I know the 2.6.38 kernel hasn't been released yet, but you can find the latest RC version here: [http://www.kernel.org/](http://www.kernel.org/)

---

