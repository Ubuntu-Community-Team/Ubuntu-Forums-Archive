---
title: "Video Card Not Compatable...?"
date: 2006-04-17
forum: General Help
---

### Post by JohnnyHaff on 2006-04-17
I'm using an evga geforce 6600 256mb video card which runs fine with windows xp pro, but when i install ubuntu and i get a whole bunch of colorful lines which doesn't look like anything.  any suggestions on how to make the video card compatable with both windows and ubuntu??

---

### Post by krismatth3 on 2006-04-17
Get the nvidia drivers: [https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29)

Edit: of course, this might not be easy if you can't see the video to run Synaptic. The packages you want to install are "nvidia-settings" and "nvidia-glx". Then run "sudo nvidia-glx-config enable". Then read over that page..

---

### Post by JohnnyHaff on 2006-04-17
i install these drivers in windows xp, then install ubuntu, right? and everything should work fine?

---

### Post by krismatth3 on 2006-04-17
No, you have to install them in Ubuntu. Boot up Ubuntu, and then when it gets to the multicolored screen, press "Ctrl+Alt+F1" and it should get you to a text console where you can log in and run those commands:

```

# sudo apt-get install nvidia-settings nvidia-glx
# sudo nvidia-glx-config enable

```

---

### Post by JohnnyHaff on 2006-04-17
would it be a pain in the *** to give me all the commands i'm gonna need?  i'm kinda of new at this... or is it gonna be self expanatory when i get there?

---

### Post by krismatth3 on 2006-04-17
Oh, that actually should be all the commands you need. When you get to the text login screen, enter your user name and password, and then run the following commands:

1. sudo apt-get install nvidia-settings nvidia-glx
2. sudo nvidia-glx-config enable
3. sudo /etc/init.d/gdm restart

You should be able to figure out any prompts that come up (I don't expect any..) but if you have trouble, don't hesitate to ask. :)

---

### Post by JohnnyHaff on 2006-04-17
When i type in the first code this is what i get: "Package nvidia-settings is not available, but is referred to by another package.  This may mean that the package is missing, has been obsoleted, or is only available from another source.
E: Package nvidia-settings has no installation candidate"
Any suggestions??  how can i get my video card to display ubuntu?????

---

### Post by Ramses de Norre on 2006-04-17
You'll need an internet connection, do you have that?
If so try running sudo apt-get update before executing the other commands.
Otherwise: what ethernet card do you have and how would you connected to the internet?

---

### Post by JohnnyHaff on 2006-04-17
i have an onboard lan, and a linksys wireless adapter which i use now to access the internet using windows xp

---

### Post by Ramses de Norre on 2006-04-17
I wouldn't try the wireless, can you plug a cable into the onboard lan? You can configure the wireless through a GUI then when you've got the right drivers.
You can activate the network with sudo ifup eth0 (but it probably will be on automaticaly).

---

### Post by JohnnyHaff on 2006-04-17
i run the update and i get the message "reading package lists... Done"  then i type in "sudo apt-get install nvidia-settings nvidia-glx" and i get the message "reading package lists... Done
Building dependency tree... Done
Package nvidia-settings is not available, but is referred to by another package.  This may mean that the package is missing, has been obsoleted, or is only available from another source."
what am i doing wrong??

---

### Post by JohnnyHaff on 2006-04-17
does anyone have any suggestions on how to get my video card compatable with ubuntu?

---

### Post by krismatth3 on 2006-04-18
From the list of your error messages, it doesn't sound like you're having any network connection problems. One way to determine for sure: try to run "ping google.com". If it looks something like the text below, it worked. (Press Ctrl+C to make it stop running, otherwise it will run forever.)
```

PING google.com (64.233.187.99) 56(84) bytes of data.
64 bytes from 64.233.187.99: icmp_seq=1 ttl=244 time=32.4 ms
64 bytes from 64.233.187.99: icmp_seq=2 ttl=244 time=34.3 ms
64 bytes from 64.233.187.99: icmp_seq=3 ttl=244 time=32.9 ms
64 bytes from 64.233.187.99: icmp_seq=4 ttl=244 time=34.5 ms
64 bytes from 64.233.187.99: icmp_seq=5 ttl=244 time=33.0 ms
64 bytes from 64.233.187.99: icmp_seq=6 ttl=244 time=34.2 ms

--- google.com ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 5003ms
rtt min/avg/max/mdev = 32.439/33.575/34.553/0.825 ms

```

Okay, next: Read over this howto: [https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29) . Skim through the whole thing and see if anything catches your eye, particularly the note on the "RenderAccel" bug. "nano" is a user friendly editor you can use from the command line to edit /etc/X11/xorg.conf . 

Anytime you edit that file, though, keep in mind to run a "sudo /etc/init.d/gdm restart" when you're finished. :)

---

### Post by JohnnyHaff on 2006-04-18
[QUOTE=krism]From the list of your error messages, it doesn't sound like you're having any network connection problems. One way to determine for sure: try to run "ping google.com". If it looks something like the text below, it worked. (Press Ctrl+C to make it stop running, otherwise it will run forever.)
```

PING google.com (64.233.187.99) 56(84) bytes of data.
64 bytes from 64.233.187.99: icmp_seq=1 ttl=244 time=32.4 ms
64 bytes from 64.233.187.99: icmp_seq=2 ttl=244 time=34.3 ms
64 bytes from 64.233.187.99: icmp_seq=3 ttl=244 time=32.9 ms
64 bytes from 64.233.187.99: icmp_seq=4 ttl=244 time=34.5 ms
64 bytes from 64.233.187.99: icmp_seq=5 ttl=244 time=33.0 ms
64 bytes from 64.233.187.99: icmp_seq=6 ttl=244 time=34.2 ms

--- google.com ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 5003ms
rtt min/avg/max/mdev = 32.439/33.575/34.553/0.825 ms

```

Okay, next: Read over this howto: [https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29) . Skim through the whole thing and see if anything catches your eye, particularly the note on the "RenderAccel" bug. "nano" is a user friendly editor you can use from the command line to edit /etc/X11/xorg.conf . 

Anytime you edit that file, though, keep in mind to run a "sudo /etc/init.d/gdm restart" when you're finished. :)[/QUOTE]
i typed in "ping google.com" and tried "ping yahoo.com"  and both times i got a message "ping: uknown host google.com"  and "ping: unknown host yahoo.com"  does this mean my internet connection isn't working?  how can i configure it to work?  

I don't know anything about the ubuntu program... not sure i should be editing anything.  unless it's easy??

---

### Post by JohnnyHaff on 2006-04-18
could part of my problem be that i'm using an AMD Athlon 64 3200 processor and i installed a regular version of ububtu.  not the 64 bit edition??   just trying to think of anything that i may have done wrong...

---

### Post by JohnnyHaff on 2006-04-18
when i was installing.. i do remember it said it couldn't set up the network because of some dhcp (sp?) thing.. so i chose to not set up the network at this time...   help any?

---

### Post by Ramses de Norre on 2006-04-18
The 64bit doesn't matter, all amd cpu's can run 32bit too.
How do you connect to the internet? If it's through a router you'll need to setup the dhcp correct.

---

### Post by JohnnyHaff on 2006-04-18
how do i do that??  yes.. i connect through a wire to a router then to the internet.

---

### Post by Ramses de Norre on 2006-04-18
Browse to your router settings page, search for dhcp settings and set them correct.. Set gateway to the routers ip, correct dns servers are normally displayed at status page of router, ...
This is only needed when it's configured wrong (does dhcp work in windows?), disable wep and mac control and other security too (you can turn it back on later when configured through gui).

---

### Post by Omnios on 2006-04-18
Try using from command line 
```
sudo dpkg-reconfigure xserver-xorg
```

This takes you into the X reconfig from there you can try using the versa driver to see if that can get you into Gnome to set other things up. Think the versa is a standard vgas driver that seems to work. Another option is to to lower the monitor frequency from either sudo "dpkg-reconfigure xserver-xorg" or from the xorg.conf with 
```
 sudo gedit /etc/X11/xorg.conf
```
in the monitor section. Basicly you want to lower your refresh rates to what you have them running in windows. I think the last number is the inportant one and I have done this with one of my computers before and should be safe as long as you do not increase them. 

 X tryes to run the monitor at the highest setting so say if your refresh is 80 or even 100 it will try to run it at that when you try to log in.

---

### Post by JohnnyHaff on 2006-04-18
i got my video card to work... i skipped the apt-get install nvidia-settings  command and just installed nvidia-glx and it worked fine....  but i still have a problem with the network... can't get it to recognize..  i'll post a new topic

---

