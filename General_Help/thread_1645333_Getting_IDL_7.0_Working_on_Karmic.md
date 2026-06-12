---
title: "Getting IDL 7.0 Working on Karmic"
date: 2010-12-14
forum: General Help
---

### Post by sweetlu on 2010-12-14
When you are trying to install IDL on Ubuntu 9.10 64bit, you may find that it installs fine. However, when you run it, you might get a fatal error when the software is trying to load. After searching high and low for a solution, I found that the only way to get around this problem was to install libstdc++.so.5.  Here's what I did to get IDL to work:

cd /tmp

wget [http://security.ubuntu.com/ubuntu/pool/universe/i/ia32-libs/ia32-libs_2.7ubuntu6.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/universe/i/ia32-libs/ia32-libs_2.7ubuntu6.1_amd64.deb)

dpkg-deb -x ia32-libs_2.7ubuntu6.1_amd64.deb ia32-libs

sudo cp ia32-libs/usr/lib32/libstdc++.so.5.0.7 /usr/lib32/

cd /usr/lib32

sudo ln -s libstdc++.so.5.0.7 libstdc++.so.5

---

