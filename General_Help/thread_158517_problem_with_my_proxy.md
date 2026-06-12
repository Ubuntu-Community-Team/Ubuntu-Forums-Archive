---
title: "problem with my proxy"
date: 2006-04-11
forum: General Help
---

### Post by harys on 2006-04-11
hi, i'm now connecting directly via external modem on the intenet. when i tried to install a package via synaptic package manager i got the error message : 
W: Failed to fetch [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/pool/i386/free/libdvdcss2/libdvdcss2_1.2.9-1plf3_i386.deb](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/pool/i386/free/libdvdcss2/libdvdcss2_1.2.9-1plf3_i386.deb)
  Could not resolve ‘proxy.mi.unicatt.it’.
ive already disabled it in the system>preferences>networkproxy and in the firefox browser. what's wrong now? thanks for your help.

---

### Post by Al3xanR0 on 2006-04-11
[QUOTE=harys]hi, i'm now connecting directly via external modem on the intenet. when i tried to install a package via synaptic package manager i got the error message : 
W: Failed to fetch [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/pool/i386/free/libdvdcss2/libdvdcss2_1.2.9-1plf3_i386.deb](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/pool/i386/free/libdvdcss2/libdvdcss2_1.2.9-1plf3_i386.deb)
  Could not resolve &#8216;proxy.mi.unicatt.it&#8217;.
ive already disabled it in the system>preferences>networkproxy and in the firefox browser. what's wrong now? thanks for your help.[/QUOTE]

You will need to configure Synaptic to use proxy and if you install/upgrade packages via apt you will need to configure apt to use your proxy as well.

for Synaptic do the following settings->preferences->network tab (see the attachment for visual) enter the proxy authentication credential as such

uid : passwd@proxyip : port#

for apt you will need to edit /etc/apt/apt.conf and add the following

```


ACQUIRE {
    Retries "3";
    Http {
        Proxy "http://userid:passwd@proxyadd.com:80/";
    }
};

```

hope that this helps

---

### Post by harys on 2006-04-11
hi, thank for the reply ive already change the network for synaptic chosing direct connection to internet. i'm a bit lost about configuring it for apt. could you please tell me the exact path. since i'm directly connected to internet, do i need anymore to set up the proxy with apt ? harys

---

