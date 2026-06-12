---
title: "New user; Need help configuring my wireless adapter"
date: 2010-01-28
forum: General Help
---

### Post by j4r3du on 2010-01-28
Hello everyone,
I am very new to Ubuntu, and Linux for that matter. I read up a bit on configuring wireless adapters in Ubuntu and have installed ndiswrapper but I am have difficulties detecting my adapter which is the Netgear WN121T.

[IMG]http://i45.tinypic.com/s0uzpw.jpg[/IMG]
[IMG]http://i49.tinypic.com/21nnkut.jpg[/IMG]

---

### Post by warfacegod on 2010-01-28
Do you have Network Manager installed?

---

### Post by j4r3du on 2010-01-28
I dont believe so. Could you direct me to a link so I could download it in my Windows OS as I have no connection in ubuntu?

---

### Post by warfacegod on 2010-01-28
> **j4r3du said:**
> I dont believe so. Could you direct me to a link so I could download it in my Windows OS as I have no connection in ubuntu?

Before we go through tat, check your System> Preferences menu to see if you have Network Connections listed.

---

### Post by warfacegod on 2010-01-28
Assuming you don't have Network Manager installed:

[http://packages.ubuntu.com/hardy/i386/network-manager-pptp/download]("http://packages.ubuntu.com/hardy/i386/network-manager-pptp/download")

It's a .deb package. They work essentially like Windows .exe files, just double click it when you get it to ubuntu.

---

### Post by j4r3du on 2010-01-28
I am using Ubuntu x64. Not sure If that will make a difference. I will try the .deb and report back.

---

### Post by warfacegod on 2010-01-28
> **j4r3du said:**
> I am using Ubuntu x64. Not sure If that will make a difference. I will try the .deb and report back.

64 Bit shouldn't make any difference at all.

---

### Post by j4r3du on 2010-01-28
Well I figured out the i386 version wont work at all so I found the x64 version of it. However I received in error saying it was in conflict with some other network manager which I removed. Upon running the .deb again I received a different error which said:

Error: Dependency is not satisfiable: libnm-util0

**[COLOR=Red]EDIT***[/COLOR]**

I have fixed that problem and installed network manager. Is there anything else I must do now?

---

### Post by warfacegod on 2010-01-28
Open a Terminal:

```
sudo iwlist scanning
```

---

### Post by Lemuel111 on 2010-01-28
Im having a similar problem configuring my wireless adapter (D-link G122 usb). I found this website
[http://anirudhs.chaosnet.org/blog/2005.10.23.html](http://anirudhs.chaosnet.org/blog/2005.10.23.html)

 It looks as though this might solve the problem however being new to Linux I don't know how to do what is suggested. It all looks very confusing to me. Would anyone be able to take me through it step by step in really simple terms?? That would be really appreciated. Thanks.

---

### Post by warfacegod on 2010-01-28
> **Lemuel111 said:**
> Im having a similar problem configuring my wireless adapter (D-link G122 usb). I found this website
[http://anirudhs.chaosnet.org/blog/2005.10.23.html](http://anirudhs.chaosnet.org/blog/2005.10.23.html)

 It looks as though this might solve the problem however being new to Linux I don't know how to do what is suggested. It all looks very confusing to me. Would anyone be able to take me through it step by step in really simple terms?? That would be really appreciated. Thanks.

Go to: System> Admin.> Hardware Drivers> activate the recommended wireless driver if there is one.

---

### Post by j4r3du on 2010-01-28
oops. see next post

---

### Post by j4r3du on 2010-01-28
I received an error stating scanning was not allowed.

---

### Post by j4r3du on 2010-01-29
I've tried everything I can think of and still no go. Anyone have any other ideas? I do remember A couple years ago I got the adapter to work with Xubuntu but I really have no idea how, it was more of an accident.

---

### Post by billyboy1995 on 2010-01-29
have you tried it without any windows drivers? I know i had this problem aswell and i can only use it without windows drivers.

---

### Post by j4r3du on 2010-01-30
I haven't actually. Could you elaborate on what exactly you mean though?

---

### Post by billyboy1995 on 2010-01-30
just uninstall the nidswrapper and then click the wireless icon on the top tool bar and see if it will find and networks. Or you can connect to it manually by going to system - preferences - network connections. Then under the wireless tab click add and add in all of your info for you network.

---

### Post by warfacegod on 2010-01-30
ndswrapper uses Windows .dll driver files if I'm not mistaken.

---

### Post by Lemuel111 on 2010-01-31
> **warfacegod said:**
> Go to: System> Admin.> Hardware Drivers> activate the recommended wireless driver if there is one.

I tried this but none are showing.

---

### Post by j4r3du on 2010-02-02
> **Lemuel111 said:**
> I tried this but none are showing.

Same for me, I've tried both ways. I really wish I could get this working :sad:

---

### Post by j4r3du on 2010-08-24
I am sorry to resurrect this thread but I am still having this issue. PLEASE someone :D

---

### Post by uRock on 2010-08-24
I'd ditch the Netgear. My Netgear USB NIC is incompatible with Ubuntu 10.04, so I am waiting until Karmic is no longer supported or when I have the extra money, whichever comes first, to go get a new non-Netgear USB.

---

### Post by j4r3du on 2010-10-08
Has anyone gotten this working yet?

:confused:

---

