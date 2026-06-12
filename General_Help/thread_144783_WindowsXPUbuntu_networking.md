---
title: "WindowsXP/Ubuntu networking"
date: 2006-03-15
forum: General Help
---

### Post by comfortably_numb on 2006-03-15
First time I've really tried an linux operating system. 

I've had a look at a bunch of FAQ and troubleshooting sites about networking my windows xp computer with the ubuntu one. Still can't do it.

I want the Windows one to connect to the internet, with the other computer connecting through it. Tried multiple ways of setting up a new network connection through windows. It seems to find the other computer, but then always has 'limited or no connectivity' afterwards. In the networking menu of the ubuntu machine it says that my ethernet connection is activated, but I can't access anything over the network. I tried installing the Samba thing, but I'm not sure if it worked or not. 

I think using this is a slightly steeper learning curve than I expected.

---

### Post by alamba on 2006-03-15
ok....let's get this working. Is your primary XP box and the ubuntu box connected via a hub/switch? I have the same set up at home and it's not difficult at all. 

Assuming that you connect to the internet via a dial-up or usb model on your XP box and the ethernet interface on the same machine connects to a switch. Download firestarter from the repositories. In preferences click on share this internet connection and enable DHCP and you should be off in no time from the ubuntu system.

A

---

### Post by borys on 2006-03-15
yea, i have the same problem, i have mi wninxp machine beside mi ubuntu machine in my win xp i have a usb network adapter and i have another network adater to conect mi winxp to my ubuntu´s machine with a simple crossed cable, i can see my windows machine but i cant get internet, and i configured my network adapter of windows to be 10.0.0.1 and my ubuntu´s network adapter to  be 10.0.0.2 please helppppppp

---

### Post by alamba on 2006-03-16
Since your primary connection is on the WinXP box do you have internet sharing enabled on that box? Also, have you put in a DNS entry in /etc/resolv.conf on your ubuntu box?

If either is not done, click on the two small computers on the XP box and there should be a share internet connection tick box in one of the tabs. Also do start>>run>>cmd and then ipconfig /all

Copy the numbers written under DNS servers, for example, 211.112.221.122 and then go to your ubuntu box and in a terminal do the following:
1. sudo vi /etc/resolv.conf
2. Add a line nameserver <numbers as obtained above>
3. Save the file

Now try accessing a site from the ubuntu box.

A

---

