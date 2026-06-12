---
title: "http_proxy enviroment variable and apt problem"
date: 2009-12-29
forum: General Help
---

### Post by sles on 2009-12-29
Hello!

I have http_proxy enviroment variable env | grep proxy
pointing to our proxy server with user authentication:
http_proxy=http://proxy:8090/
but we also have apt-cacher which works on another port, so I wrote:
Acquire {
    http::Proxy "http://proxy:3142";
}

but apt-get always takes environment variable http_proxy , so I have to unset it every time before apt-get.
Is it possible to force apt use proxy from config?

---

