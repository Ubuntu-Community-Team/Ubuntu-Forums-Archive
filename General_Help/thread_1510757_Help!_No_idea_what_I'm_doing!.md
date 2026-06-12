---
title: "Help! No idea what I'm doing!"
date: 2010-06-15
forum: General Help
---

### Post by bryce1 on 2010-06-15
Hello all,

My name is Bryce and I just downloaded Ubuntu because of the reviews I have heard.

I installed the Beta 10 OS on a partitioned harddrive (also running windows 7) Here's the problem, I can't for the life of me access the internet with wired or wireless connection. (Ubuntu recognizes the lan connection, but no internet. Wireless is enabled. I have also tried pointing the browser to default gateway 192.168.0.1)

I did however download the official 10.04 release but I am waiting to see if you all think i can do without installing it. 

The laptop I have is a HP Pavilion DV6 with built in wireless. 

I preformed the sudo lshw -C network code and the message I got back was that my connection was "disabled".

I am sorry if this is the wrong section and that I am such a noob. I really just want to get this working.

I appreciate any and all input.

thank you,

Bryce

---

### Post by bryce1 on 2010-06-16
Any suggestions at all?

---

### Post by pastalavista on 2010-06-16
If you installed from a bootable live CD or USB, boot it in the "Try without changes" mode. Does the wireless or wired networking work then? I don't understand the wired not working unless the router has MAC filters. Check that on another PC on the network.

---

### Post by bryce1 on 2010-06-16
I'm unfamiliar with "try without changes mode"? Do you mean when I boot?

I enabled my router to allow all MAC addresses.

---

### Post by QIII on 2010-06-16
Hey.  I often feel like I have no idea what I'm doing -- and I have been  a computer geek since the 70s.

What pastalavista means is for you to put the LiveCD in your tray and reboot.  When the machine starts up, the menu should give you a choice to "Try Ubuntu without making changes ..."

Choose that, and see if you can access the internet while you are running what we call a "live" session.

That'll help us start to sort this out for you.


By the way...  Might have been better in the Absolute Beginner's section.  But don't worry about it.  You needed help and dialed the first number you found.  No big deal.  I don't think anyone will bend your dog tags.

---

### Post by pastalavista on 2010-06-16
"Try Ubuntu without changes to your system" is one of the options in the live CD boot menu, along with "Install Ubuntu...". It is the recommended way to see if the release will work on your system before installing it.

---

### Post by bryce1 on 2010-06-16
Thanks for all the help guys and sorry for posting in the wrong section. Will read rules next time.

So I tried the "Try ubuntu" with the cd in drive and the wireless still did not work. :(

Any other suggestions? I appreciate all your responses.

---

### Post by lidex on 2010-06-16
Have a look here:
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")
[http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/4#wireless]("http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/4#wireless")

---

### Post by pastalavista on 2010-06-16
What do you find in System->Administration->Hardware Drivers? If something shows up there, you will have to try and connect wired to the router or modem to install it. If the wired won't work, try another CD or linux distro maybe because I don't know. I've never seen wired networking not work... that's a linux strong point.

---

