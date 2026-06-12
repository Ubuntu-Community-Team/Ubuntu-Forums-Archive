---
title: "Configuring aptitude with a proxy server"
date: 2006-05-17
forum: General Help
---

### Post by tread on 2006-05-17
I could setup the proxy server I have to use in synaptic, and can upgrade/install through synaptic just fine.

I would rather use aptitude though, does anyone know how to configure the proxy for this?

---

### Post by louis_nichols on 2006-05-17
This should work:

1. ```
sudo gedit /etc/apt/apt.conf
```

2. add this text into it:

```
ACQUIRE {
http::proxy "http://username:password@proxy:port/"
}
```

4. Save and exit.

5. Try aptitude.

---

### Post by jsa13 on 2008-02-07
The /etc/apt/apt.conf didn't work for my system.  I had to export environment variables...

```

export http_proxy="http://username:password@proxy:port"

```

It then functioned properly.  These can be added to your ~/.bashrc as shown above or /etc/environment as shown below (no 'export').

```

http_proxy="http://username:password@proxy.mcg.edu:port"

```

---

