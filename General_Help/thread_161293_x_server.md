---
title: "x server"
date: 2006-04-16
forum: General Help
---

### Post by Bubolzm on 2006-04-16
what is the x server and how do i configure it so i can use ubuntu.

---

### Post by PriceChild on 2006-04-16
It should be configured already when you do a standard install :S

Why do you need to configure it?

---

### Post by Bubolzm on 2006-04-16
when i load up ubuntu, i get to the login part. it asks my username, i give it. then it gives me some weird error saying i need to configure x server (my graphical interface) and reboot before i may continue. i have no idea how to reconfigure it. perhaps a reinstall of ubuntu would be in order, but how do i get rid of the other copy?

---

### Post by PriceChild on 2006-04-16
Have you simply installed it, then tried to log in for the first time and this has happenned? Or has it happenned after playing with some settings?

---

### Post by Bubolzm on 2006-04-16
i installed on friends computer, it worked. then i installed on mine doing the exact same thing, and it dosent work. it wasnt the first time i installed the software, but it is the first time i did it on my computer.

---

### Post by Qrk on 2006-04-16
configure x-server with

```
sudo dpkg-reconfigure xserver-xorg
```

Its surprising as you should have had to configure it during the install.

---

### Post by PriceChild on 2006-04-16
From the log in screen, press ctrl+alt+F1 to switch to a terminal, from where you can type Qrk's suggestion.

---

### Post by Bubolzm on 2006-04-16
im sorry but i cannot seem type ctrl+alt+F1 in the right place. are you telling me to do it on my desktop or when im booting? because i cant get to my desktop.

and btw i think i have bad software or incompatibility issues. for some reason, even after i installed it onto a different hd it gives same error.

---

### Post by bluetoad on 2006-04-16
You should be able to enter ctrl-alt-f1 from the screen where you are asked to enter your username.  I assume that screen is in the Ubuntu colours - not just a prompt on the screen.

---

### Post by Bubolzm on 2006-04-16
actualy it IS a prompt screen. kinda looks like dos

---

### Post by Qrk on 2006-04-16
ah, then you can just type in the code directly. After logging in with your username and password, you should get a command prompt. Then type the:
```

sudo dpkg-reconfigure xserver-xorg
```

It should bring up a configuration dialog. Write down the driver that is currently selected (second screen of the dialog) You may want to choose "vesa" here, as it has the best hardware support. Once you've got your desktop, search here or on the wiki (or under system--> help for how to get 3-d acceleration)

---

### Post by Bubolzm on 2006-04-16
its weird, it doesn't like me typing in my password. nothing usually shows up, but sometimes, i get

bubolzm@ubuntu: ~@

and i can type stuff after that

---

### Post by Qrk on 2006-04-16
Even though you password doesn't show up, its still being typed. There aren't any characters masking it ( for example ******) but its still there.

---

### Post by Bubolzm on 2006-04-16
great but what about the username@ubuntu: ~@    ?

---

### Post by Qrk on 2006-04-16
That is where you put the command sudo dpkg-reconfigure xserver-xorg

---

### Post by Bubolzm on 2006-04-16
thanks but i was just curious why the ~@ was hanging out in front!

ill try that right now!

---

### Post by Qrk on 2006-04-16
Ah, the ~ means that the prompt is from your home directory. If you were to go to the top level directory, you'd see a /. Another directory might show up as a /usr/share or whatever.

As to the @ sign, I have no idea why it is an @ sign and not a $. Its just to break up the prompt from the command space I believe.

---

### Post by Bubolzm on 2006-04-16
yay thank you guys, i got in.... 
now one problem...
no networking, ugh.

---

### Post by bluetoad on 2006-04-16
What happened when you did 

sudo dpkg-reconfigure xserver-xorg

You will need to put your password in

If the X stuff is installed, we might be able to get that configured without network and then use the GUI tools to configure the network.  

You might as well let us know the state of your network stuff.  It is probably better to do that in a separate thread with a relevant title such as "configuring network from command line" ;-)

In that message, can you please paste the results of the following commands (all typed from the bubolzm@ubuntu: ~@ prompt)

1. ifconfig 
2. netstat -nr
3. cat /etc/resolv.conf

---

