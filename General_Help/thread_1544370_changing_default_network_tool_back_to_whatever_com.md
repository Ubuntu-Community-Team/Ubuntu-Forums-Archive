---
title: "changing default network tool back to whatever comes as standard"
date: 2010-08-02
forum: General Help
---

### Post by tonyuk123 on 2010-08-02
i have changed the network/internet tool on ubuntu 9.04 to wicd
which now doesn't work, ethernet or wireless connection
how do i change it back to whatever the default is?

---

### Post by tonyuk123 on 2010-08-02
ok well all i want to do is get some kind, any kind of internet connection back
as all the solution for the wireless atheros card i have, use apt-get, install etc
so without any sort of connection i can do nothing

has anybody got any idea?
the realtek ethernet card worked fine until i followed some instructions on getting the atheros card work
then suddenly i have no internet atall
i know the ip address etc as the laptop works fine on it

help!

---

### Post by xircon on 2010-08-02
Uninstall wicd from synaptic, take it all out, reboot and it should work.  I take it you did not uninstall the networkmanager applet?

---

### Post by tonyuk123 on 2010-08-02
ok thanks i will try that, not i didnt uninstall the networkmanager applet, should i have done?
i was following instructions on this forum for getting the atheros wireless card to work, and all was ok, until i got the bit where it suggested that they use wicd, i did this and suddenly not wired network either
will post what happens
thanks for the idea, much appreciated

---

### Post by xircon on 2010-08-02
I read somewhere that the built in applet does not play nicely with wicd, once wicd is installed nothing works.

---

### Post by tonyuk123 on 2010-08-02
ok, i have unistalled completely the wicd from synaptic
i restarted, but now i get no network tool at the top atall
the strange thing is the wired network card has its main LED on when cable is plugged in, and when i try access any network the other LED flashes
the light on the modem also flicks briefly too
but if i use firefox and put 192.168.1.1 it will not connect to the modem
but on this laptop i use the same address it lets me talk to it no problem

i am thinking you could be right about wicd, shame the wireless tutorial didnt mention this !

any more ideas, is hard to do anything without having internet acess especialy to post info here as i cannot copy and past output from terminal easily!

---

### Post by xircon on 2010-08-03
Weirder and weirder.

What is installed?  Have a look in synaptic, this is what I have:

[[IMG]http://i367.photobucket.com/albums/oo118/xircon/th_network-1.png[/IMG]](http://s367.photobucket.com/albums/oo118/xircon/?action=view&current=network-1.png)

Sorry about the cursor!!  Gnome is not my strong point, but also check your startup applications for an entry for network manager mine runs the command "nm-applet --sm-disable"

[[IMG]http://i367.photobucket.com/albums/oo118/xircon/th_network2-1.png[/IMG]](http://s367.photobucket.com/albums/oo118/xircon/?action=view&current=network2-1.png)

Cheers

Steve

---

### Post by tonyuk123 on 2010-08-03
ok i have taken some screen shots and chnaged them over using a usb stick onto laptop

here they are [ATTACH]165377[/ATTACH]
[ATTACH]165378[/ATTACH]
[ATTACH]165379[/ATTACH]
[ATTACH]165380[/ATTACH]

i have run the system from the 10.04 ubuntu cd
it works fine (if a bit slow of course) it even works on wireless!

i looked at various network settings while it was running and tried making sure the 9.04 system was set the same
main difference being that there is no network managment on the menu, i assume it was removed when i did the wicd install, uninstall?

any more ideas from the images?

---

### Post by xircon on 2010-08-03
Can't see network-manager-gnome is it out of sight?

Where are you? I am in Sheffield.

---

### Post by tonyuk123 on 2010-08-03
ah ok
network manager gnome is not installed
but as i dont have the internet, how can i install it?
i'm in kent near Margate

---

### Post by TeoBigusGeekus on 2010-08-03
Try to configure your network via command line with [this]("http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html") page and then install gnome n.m.

---

### Post by xircon on 2010-08-03
It should be on the CD, add your install CD to your repositories from synaptic>settings>repositories.

---

