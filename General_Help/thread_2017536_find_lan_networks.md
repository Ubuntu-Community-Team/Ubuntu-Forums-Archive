---
title: "find lan networks"
date: 2012-07-05
forum: General Help
---

### Post by ddimit on 2012-07-05
hello ..
i would like to ask how is it possible to find the lan devices connected via ethernet on switcher
on windows you just click on "Networks" and all the devices appear ..(so simple)
one friend bought his mac laptop here and like windows the devices appear in a simple click
but on ubuntu i was not able to find them .. can you tell me how can i make it find them  please?
the lan devices i have is an iomega device which i transfer movies on it's hard disk via lan network and then i watch them on living room

---

### Post by alexlpratt on 2012-07-05
I'm not entirely sure what you are asking, however if you are looking for your network interface devices, you'll want to open up terminal and use the command:

*ifconfig*

If you are looking for the visible devices on your network, you will want to find your default gateway using:

*route -n*

Then take that gateway address and use:

*nmap -sP <gateway address>*

This will print out what hosts are available to you. This will be a good starting point to see if these are visible to your Ubuntu box. Good Luck!

---

