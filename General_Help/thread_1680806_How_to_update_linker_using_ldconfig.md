---
title: "How to update linker using ldconfig"
date: 2011-02-03
forum: General Help
---

### Post by begroup on 2011-02-03
Hello all,
We are currently using libpcap for our project work. The default library installed in ubuntu is 0.8. We want to install libpcap1.1.1 as our custom library. we did the following:-
We manually compiled and installed libpcap-1.1.1.

1. In directory /etc/ld.so.conf.d :
    created a file called "libpcap.conf".
    
    2. In the file "libpcap.conf" add the path where your custom library is     installed i.e.  /usr/local/lib
    
    Once the above is done, we need to update the linker using command "ldconfig".
For doing this which command is to be used??
We are stuck here???


Eagerly waiting for reply....

---

### Post by blueridgedog on 2011-02-03
have you simply tried 

```
sudo ldconfig -v
```

Is include /etc/ld.so.conf.d/*.conf in your /etc/ls.so.conf?

---

