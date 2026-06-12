---
title: "Where is lts.conf ?? Any LTSP successes out there?"
date: 2006-03-14
forum: General Help
---

### Post by jgregory on 2006-03-14
I just installed Edubuntu 5.10. I'm trying to get an LTSP client to successfully boot. No love yet... Where is the lts.conf file? I've run other distros with LTSP. To the best of my limited knowledge, it needs an lts.conf file to work. I see the lts.conf.sample, but no actual file. Do I need that file? Does the 
EdUbuntu/LTSP integration eliminate the need for that file? 

Has anyone had success with LTSP on Edubuntu Breezy? 

TIA

John

---

### Post by kchiefs on 2006-04-17
I have installed LTSP on Ubuntu Breezy.  My first server is in Denver right now with 12 more left to build.  I am using Denver as sort of a "test" and so far the bugs have all been minimal.  The lts.conf file is in /opt/ltsp/i386/etc/lts.conf.  By the way i'm a noob and it took about 4 weeks of research and trial and error to get it to work.  Now i'm just dealing with exporting and importing emails from evo 1.xx to evo 2.xx. with no luck so far. I might just convert them to thunderbird

---

### Post by jgregory on 2006-04-17
Yup... I ended up scrapping Edubuntu and installing Ubuntu Breezy. It's working for me now. Thanks for the info. I haven't been using email on Ubuntu, so I don't have any advice for you. Sorry. Good luck.

John

---

### Post by Fed7 on 2006-04-18
Hi,
i have install LTSP on Breezy.
My client (NIC PXE) don't run. Error is: TFTP error :(
Why?

---

### Post by kchiefs on 2006-04-18
I have had that same error and it's something in the dhcp.conf file (i think, could be wrong).  I will copy the file from a working sorce for you in a few minutes.

---

### Post by kchiefs on 2006-04-18
allow booting;
allow bootp;

option subnet-mask            255.255.255.0;
option broadcast-address      192.168.0.255;
option routers                192.168.0.254;
option domain-name-servers    192.168.0.254;
option domain-name            "ltsp";
option root-path              "192.168.0.254:/opt/ltsp/i386";
option option-128 code 128 = string;
option option-129 code 129 = text;

shared-network WORKSTATIONS {
  subnet 192.168.0.0 netmask 255.255.255.0 {
     range dynamic-bootp 192.168.0.100 192.168.0.253;
     use-host-decl-names       on;
     option log-servers        192.168.0.254;


     # trick from Peter Rundle <peter.rundle@au.interpath.net>
     if substring (option vendor-class-identifier, 0, 9) = "PXEClient"
     {
        filename      "/2.4.26-ltsp-3/pxelinux.0";
          # NOTE: kernels are specified in /tftpboot/lts/pxe/pxelinux.cfg/
     }
     else
     {
        filename    "/lts/vmlinuz.ltsp";

     }
  }
}

---

### Post by kchiefs on 2006-04-18
If that doesn't help i will get you the other conf files....by the way that is from /etc/ltsp/dhcpd.conf

---

### Post by jgregory on 2006-04-18
Fed7, what is your specific TFTP error message on the client when it boots? Describe what the client does during the boot process.

John

---

### Post by Fed7 on 2006-04-20
[QUOTE=jgregory]Fed7, what is your specific TFTP error message on the client when it boots? Describe what the client does during the boot process.

John[/QUOTE]

Sorry :oops: 
i have solve!
My first installation is wrong!

Now it's run.

A question: the band width of M$ TS is 15kbyte/user. In LTSP?
It's possible connest a remote client? (like a M$ TS)

Thk,
Fede

---

### Post by jgregory on 2006-04-20
I haven't used Microsoft Terminal Server before. I get the impression that LTSP needs more than 15KB/s. But I'm not sure. Someone else might have a better answer for you.

I think you can connect other remote clients, but I haven't done that yet.

John

---

### Post by Fed7 on 2006-04-21
[QUOTE=jgregory]I haven't used Microsoft Terminal Server before. I get the impression that LTSP needs more than 15KB/s. But I'm not sure. Someone else might have a better answer for you.

I think you can connect other remote clients, but I haven't done that yet.

John[/QUOTE]

thk!

i have install NX ... it's great!

---

