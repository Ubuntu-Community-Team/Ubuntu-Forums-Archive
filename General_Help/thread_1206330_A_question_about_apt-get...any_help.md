---
title: "A question about apt-get...any help?"
date: 2009-07-07
forum: General Help
---

### Post by abhi_69 on 2009-07-07
Hello, 
i mainly use apt-get from command line to install packages in my ubuntu 9.04. i use a proxy settings for my internet connection. it prevent me from downloading any file larger than 10 MB using proxy settings(actually my ISP apply this method to maintain their bandwith). if i want to download larger file, i hav to use direct connection instead of proxy. so, i use-
**'--no-proxy'** parameter with **wget** to download using direct connection. but, i can't find any method like this for apt-get. so, i always hav problem in installing larger packages (>10 MB) using apt-get. i try to use 'no proxy/direct connection' settings in 'Network settings' in Synaptic. but, it not working. still i can't install larger packages via apt-get & it show error.
is there any method like wget for apt-get? any help for me? how can i use my direct connection to install packages via apt-get?
thanz in advance.

---

### Post by jenkinbr on 2009-07-07
try adding the line

```
no_proxy =
```

to /etc/wgetrc

```
sudo echo "no_proxy =" >> /etc/wgetrc
```

This *should* solve your problem, as well as eliminate the need to add --no-proxy to all your wget commands.

---

### Post by abhi_69 on 2009-07-07
> **jenkinbr said:**
> try adding the line

```
no_proxy =
```to /etc/wgetrc

```
sudo echo "no_proxy =" >> /etc/wgetrc
```This *should* solve your problem, as well as eliminate the need to add --no-proxy to all your wget commands.
thanz for help. this working nice.
but, what can i do when i need proxy back with apt-get? i can download faster using proxy, so, i hav to use proxy settings when downloading file smaller than 10 MB. can i return back to proxy when i installing smaller packages?
can u tell me about this as well?
thanz for ur help again.....

---

### Post by 3rdalbum on 2009-07-07
> **abhi_69 said:**
> thanz for help. this working nice.
but, what can i do when i need proxy back with apt-get? i can download faster using proxy, so, i hav to use proxy settings when downloading file smaller than 10 MB. can i return back to proxy when i installing smaller packages?
can u tell me about this as well?
thanz for ur help again.....

If you open up the /etc/wgetrc file (remember, you need to open it as root), you'll see the "no_proxy" bit at the bottom. If you put a hash symbol (#) at the beginning of that line, it will disable the line.

So, when you don't want to use the proxy, make sure there's no # before the line. When you do want to use the proxy, disable the "no_proxy" by putting the # before it.

---

### Post by jenkinbr on 2009-07-07
> **3rdalbum said:**
> If you open up the /etc/wgetrc file (remember, you need to open it as root), you'll see the "no_proxy" bit at the bottom. If you put a hash symbol (#) at the beginning of that line, it will disable the line.

So, when you don't want to use the proxy, make sure there's no # before the line. When you do want to use the proxy, disable the "no_proxy" by putting the # before it.
Precisly what I was going to say.

You beat me to the punch :)

---

