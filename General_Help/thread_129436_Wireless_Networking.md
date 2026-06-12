---
title: "Wireless Networking"
date: 2006-02-13
forum: General Help
---

### Post by kenetik on 2006-02-13
Heh always probs with wireless networking right? =(

Ok, just installed Ubuntu on my Toshiba Satellite A1, setup the network settings (i think i did everything right).. I see the Signal Strength, looks like its connected and everything, but its only sending packets, never receiving.. what am I doing wrong? What do I need to post to give you as much info as possible? Basically I cant go anywhere on the net ;)  

Thanks!

---

### Post by m.musashi on 2006-02-13
I'm no expert here but having had some similar problems I can think of a few things to check. Does your router have encryption set up? If so, what type WEP, WAP, etc. I didn't have any luck with encryption beyond WEP. Since most say it isn't very secure anyway I now have mine set up without encryption.

Are you connecting to your router? That may sound dumb but I often had trouble with it trying to connect to my neighbor's router.

If this isn't helpful, perhaps you could provide a bit more specifics. I probably won't be much help but others might be.

---

### Post by kenetik on 2006-02-13
Yah Im using WEP, the iconbar seems to show that Im connected, but when I try to go to 192.168.1.1 in firefox it says connection refused.

I've tried w/ no encryption, same exact issue. And how can I tell if Im conencting to the router or not? I mean its giving me the signal strength and its showing packets sent, but just no response..

---

### Post by m.musashi on 2006-02-13
Is your router set to allow wireless admin? Mine isn't as a security precaution (actually I don't know that it is a precaution). As a result, from a wireless computer if I try 192.168.1.1 I get the connection refused or similar error. However, that should not preclude you from using wireless - just using wireless (might be called remote) admin.

As for your actual problem of no connection I'm not really sure. I'm no expert (actually just a newbie myself) but I'll try and suggest what has worked for me.

Perhaps someone can ask for the relevant files to help troubleshoot.

---

### Post by kenetik on 2006-02-13
Yah I can do the remote admin from the other wireless pc just fine. I've got my XP machine setup and running on it just fine, but I cant get the Ubuntu lappy to work.. 

I can give any information needed, please ask.. Woo, please help me someone, heh..

---

### Post by kenetik on 2006-02-13
Also it may help that for some reason its telling me that the DHCP server isnt working correctly, but the XP box is configuring everything automatically through the DHCP server.. Why wouldnt the ubuntu lappy? Any ideas on that..

---

### Post by neoflight on 2006-02-13
I have a strange problem as well...

I have all my hardware working on my thinkpad. 
I was at my gf's place and the wireless was working perfectly. i came back home and tried to connect to my home network its not working !!!

it says its connected...but i cannot ping any .com. 
we use WEP hexadecimal key. nothing fancy...but it WAS working at home before. I could connect from XP though (dual boot) I have seen that before...

Before I went to gf's place my home wireless was working just fine. but i reinstalled ubuntu at gf's place and there again it worked (it didnt work before i reinstalled!!!)

why is it so problematic when i move from one network to another? it just refuse to connect !!! STRANGE!!!!

---

### Post by nanotube on 2006-02-13
hey
you might want to try installing the network-manager package. that one does well at detecting and connecting to wireless lans, and moving between locations.
see [http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Multiple_Wireless_Profiles](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Multiple_Wireless_Profiles)
for details. (specifically, dont install the network-manager package from the repositories, use the custom nobind package on the site above)

---

### Post by kenetik on 2006-02-14
Very new to linux, thanks for the links, install the 3 packages, now how do i start the service?

---

### Post by ifwntrends on 2006-02-14
I'm having the same problems. I just installed the 3 packages above, after which i couldn't connect at all. Then from a prompt I entered 'sudo NetworkManager', now i'm connected again but i can't find a front end for it (applet, systray, etc).

---

### Post by nanotube on 2006-02-14
hi
the "frontend" for it is called "nm-applet"
just run it from a terminal
might also want to add it to session startup (system>preferences>sessions, and on the last tab, add "nm-applet" ).

---

### Post by kenetik on 2006-02-14
Hmm, yah I installed it, and running it currently but it says:

> 
REDUCED NETWORK FUNCTIONALITY

The network device "(null) (eth1)" does not support wireless scanning. It will not be completely functional.


Im so frustrated :(

---

### Post by nanotube on 2006-02-14
hmm... well it should still work if you enter the ssid manually, i would think...

---

### Post by kenetik on 2006-02-14
network manager didnt ask me anything.. i dont know where to input the ssid on network manager sorry for the noobish questions, i really do appreciate your help, if you can help get this up tonight, i can paypal you some cash

---

### Post by nanotube on 2006-02-14
haha do not worry about cash and paypal, man. :)

to enter ssid and stuff: just click on the nm-applet in your gnome-panel, and you will see a menu - one of the items says "connect to other wireless network". choose that, and it should allow you to enter ssid and stuff.

---

### Post by kenetik on 2006-02-14
OMG, IT WORKS, dude you are AWESOME, muchos gracias.. THANKS!!

---

### Post by ifwntrends on 2006-02-14
thanks for the help, it's up and running now and i'm connected to my network at home (which was working before with gtkwifi)...we'll see how it works on the network at school ;) .

---

### Post by nanotube on 2006-02-14
hehe, you are welcome, dudes. :) have fun with ubuntu!

---

### Post by kenetik on 2006-02-14
See if you can fix my other problem ;) - You sure you dont want some paypal love?

---

### Post by nanotube on 2006-02-14
hehe, well, why don't you tell me what your other problem is, first? ;)

---

### Post by kenetik on 2006-02-14
Sorry - [http://ubuntuforums.org/showthread.php?t=129551](http://ubuntuforums.org/showthread.php?t=129551)

---

### Post by nanotube on 2006-02-14
posted a link to your other thread. check it out :)

---

