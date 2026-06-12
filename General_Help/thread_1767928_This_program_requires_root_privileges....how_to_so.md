---
title: "This program requires root privileges....how to solve it ??"
date: 2011-05-26
forum: General Help
---

### Post by sicpteker on 2011-05-26
Hi.......


I have faced a message states that "This program requires root privileges"

how can I get over this thing??
is there a required program for the root?? or any settings ??


thanx a lot

---

### Post by snowpine on 2011-05-26
Please be specific when asking for help; what is "this program"?

In general, use "sudo" (terminal applications) or "gksu" (GUI applications) for example "sudo nano" or "gksu gedit".

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Rubi1200 on 2011-05-26
Hi and welcome to the forums :-)

What program are you trying to run?

Some applications require administrative privileges. This is designed to keep your system safe and secure.

To run graphical applications with root privileges use gksu or gksudo

For non-graphical applications use sudo

The password you enter is the same one you use to login.

If you need to enter it in the terminal, you will not see any visual feedback but just type the password and then Enter.

For more information, see here:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by sicpteker on 2011-05-26
thanx for your fast reply

actually I used to run this command

"   airodump-ng -c 11 --write Linksys001 wlan0  "

but I do not know what is the name of the program??

I do not know what is the problem of that root?

---

### Post by DanR01 on 2011-05-26
The command airodump-ng is from the aircrack-ng package which is a set of tools to test wireless security.

To run it as root you type 

```
sudo airodump-ng -c 11 --write Linksys001 wlan0
```

---

### Post by sicpteker on 2011-05-26
thanx a lot ... it works  :)

so I use this as a role for me 

whenever it require root privileges I add for the command "sudo"

or it depends on the program??

---

### Post by DanR01 on 2011-05-26
If the program runs in the terminal use the prefix sudo to run as root.

If the program has a GUI, for example nautilus (the file manager) use gksudo.

See the link that snowpine gave you.

Best wishes

---

