---
title: "ubuntu 11.04 LTSP"
date: 2011-08-17
forum: General Help
---

### Post by qwerty-user on 2011-08-17
Hi, I'm a bit new to Ubuntu 11.04 so I'm turning to you experts. I am trying to set up a LTSP system with Ubuntu 11.04 server 32bit. I have spent one whole week trying to make this work but had no success. The one thing which isn't working is the isc-dhcp, where every time I restart it, it [fails]. I have searched all the errors which came up during my configuration and although I tried everything on the web, I still can't make it work. Can any one please list the steps clearly how the LTSP is set up including all the software/hardware/network configuration please? Thanks a lot. Hope this post helps a lot of new Ubuntu users like me and makes their life a little easier.

---

### Post by dino99 on 2011-08-17
[http://www.basicconfig.com/linuxnetwork/configure_dhcp_server_ubuntu](http://www.basicconfig.com/linuxnetwork/configure_dhcp_server_ubuntu)
[http://www.howtoforge.com/dhcp_server_linux_debian_sarge](http://www.howtoforge.com/dhcp_server_linux_debian_sarge)
[http://www.amagob.com/wpmu/?p=641](http://www.amagob.com/wpmu/?p=641)

---

### Post by qwerty-user on 2011-08-17
I have gone already through these sites, tried them but none worked. Any other suggestions please? Really need help.

---

### Post by christiaan_ on 2011-08-21
After many hours of pain I decided to create a step-by-step LTSP setup guide.

[How to create a Ubuntu 11.04 x64 LTSP server with 32bit thin clients]("http://www.thefanclub.co.za/how-to/how-create-ubuntu-1104-x64-ltsp-server-32bit-thin-clients")

The guide is written for a 64bit server but will work for 32bit as well.

---

### Post by xordox on 2011-08-30
> **christiaan_ said:**
> After many hours of pain I decided to create a step-by-step LTSP setup guide.

[How to create a Ubuntu 11.04 x64 LTSP server with 32bit thin clients]("http://www.thefanclub.co.za/how-to/how-create-ubuntu-1104-x64-ltsp-server-32bit-thin-clients")

The guide is written for a 64bit server but will work for 32bit as well.

Thanks for great tutorial. Please tell me did you try to use ltsp for FAT client? I have only blank screen after login on fat client machine. I tried to install on different hardware servers and clients.
thanks

---

### Post by christiaan_ on 2011-08-31
> **xordox said:**
> Thanks for great tutorial. Please tell me did you try to use ltsp for FAT client? I have only blank screen after login on fat client machine. I tried to install on different hardware servers and clients.
thanks
No I have not tried FAT clients on LTSP. Apparently the you need to build a Fat Client image on the LTSP server that will work for both thin and fat clients.

The command for building the fat client image is:

```
sudo ltsp-build-client --fat-client --arch i386
```

For more information I found this :
[How do LTSP Fat Clients work?]("http://jonathancarter.org/2010/11/24/how-do-ltsp-fat-clients-work/")
[UbuntuLTSPFatClients]("https://help.ubuntu.com/community/UbuntuLTSP/FatClients")
[Ubuntu Manpage: lts.conf]("http://manpages.ubuntu.com/manpages/natty/man5/lts.conf.5.html")

---

