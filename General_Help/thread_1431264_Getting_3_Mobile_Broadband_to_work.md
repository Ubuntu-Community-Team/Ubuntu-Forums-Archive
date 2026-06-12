---
title: "Getting 3 Mobile Broadband to work?"
date: 2010-03-16
forum: General Help
---

### Post by JayUK20 on 2010-03-16
I have just brought a netbook and would like to run my three mbb on it but i tried it in wubi and it didnt work as the software on the dongle is for windows and not linux, has anyone got a work around for unr?

---

### Post by uylug on 2010-03-16
> **JayUK20 said:**
> I have just brought a netbook and would like to run my three mbb on it but i tried it in wubi and it didnt work as the software on the dongle is for windows and not linux, has anyone got a work around for unr?

You mean 3G?

Haven't you tried NetworkManager? Right click your connection icon on the upper right corner and select Edit Connections. Then go into Mobile Broadband and configure it right there!

---

### Post by JayUK20 on 2010-04-13
Hi, 3 is my network provider.

Also I have made a connection by doing what you said, however it will no longer work and will not display "3" in network manager.

---

### Post by halj32 on 2010-04-13
3G is one of the easiest to get working.. no drivers needed
right click on your network manager, go to edit connections.
go to Mobile Broadband..  new connection..
enter
network name 3Connect
number  *99#
leave everything else blank until you come to
APN  3internet

done
you can have it auto connect if you like by ticking the box

---

### Post by jalirious on 2010-04-27
wvdial is more stable than network manager for huawei stuff in my experience. modeswitch may be necessary in some cases.

---

### Post by mul01 on 2010-04-27
i have 3 mobile broadband on a dongle,i had problems with it. click on the connections manager at the top ,edit connections,mobile broadband.u have to make sure your mobile numbeer  is correct there is no password so dont worry,also click on automatic connect and avalbile for all users.

mine never worked after i set it up i had to go on to a wifi connection and do all the updates 6months worth,then the dongle worked as there was a bug in the kernal when 9.10 was released apprently that sorted my problem out.
You will need to do all the updates as well because usbswitchsmode is part of the update and u need that.

I have desktop ubuntu tho so may be same i dont know.

10.04 is out in 2 days.

---

### Post by polomint77 on 2010-05-08
I have a 3 internet dongle and have installed 10.04.  All I did was plug the dongle in and it worked straightaway..  Not much help really, but maybe you could try 10.04?

John

---

### Post by bumanie on 2010-05-08
10.04 with the latest kernel 2.6.32-22 is kinder on some huawei 3g modems - I have an E620 running on that kernel, but it wouldn't run on earlier ones in 10.04 - at one stage I had to install a development kernel for the E620 to run or use usb_modeswitch. Some huawei models 'work out of the box', some don't. I know of a few others with different models to mine who have also managed OK with the development kernel or usb_modeswitch.

---

