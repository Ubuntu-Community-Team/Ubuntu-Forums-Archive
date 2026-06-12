---
title: "Error installing plugin for Compiz Fusion"
date: 2011-11-18
forum: General Help
---

### Post by jasoncruz98 on 2011-11-18
I am interested in installing experimental and unsupported plugins for Compiz-fusion from Git. My primary interest is in the plugin Snow.

I followed the instructions on the Compiz website, and created a directory called compizplugins in my home folder. After that, I navigated to that directory using terminal, and ran this command:
> git clone git://anongit.compiz.org/fusion/plugins/snow

After that, I navigated to the directory ~/compizplugins/snow , and ran the command ***make***. But all I got was this error:

> [B]convert   : snow.xml.in -> build/snow.xml
bcop'ing  : build/snow.xml -> build/snow_options.h
bcop'ing  : build/snow.xml -> build/snow_options.c
make: *** No rule to make target `build/snow.lo', needed by `c-build-objs'.  Stop.[/B]

So I ran the command ***make install***. Still, I got the same error:

> **make: *** No rule to make target `build/snow.lo', needed by `c-build-objs'.  Stop.**

Can someone tell me why can't I install this plugin? I need to know what I was doing wrong and how to install the plugin Snow without encountering any errors (using Git).

---

### Post by kurru on 2011-11-28
Same issue for me. Any help would be appreciated. Thanks.

I run Ubuntu 11.04 with linux kernel rev. 3.0.6-030006.

---

