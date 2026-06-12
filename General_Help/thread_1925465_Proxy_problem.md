---
title: "Proxy problem?"
date: 2012-02-14
forum: General Help
---

### Post by Bromden on 2012-02-14
Hi, I'm trying to install the latest "libvpx" but when I insert this string:
git clone [http://git.chromium.org/webm/libvpx.git](http://git.chromium.org/webm/libvpx.git)

into the terminal i get this error...

error: Couldn't resolve proxy 'myproxy.domain.com' while accessing [http://git.chromium.org/webm/libvpx.git/info/refs](http://git.chromium.org/webm/libvpx.git/info/refs)

I think I have mistakenly created a test proxy called "myproxy.domain.com" but I don't know how to get rid of it XD


Sorry for this stupid problem :)

---

### Post by Bromden on 2012-02-14
Ooookay solved with this!

git config --global --unset http.proxy
(it *revokes the proxy settings)*

Thanks to Vogella git tutorial ^^

---

