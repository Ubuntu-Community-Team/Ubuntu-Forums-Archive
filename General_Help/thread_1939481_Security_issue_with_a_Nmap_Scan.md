---
title: "Security issue with a Nmap Scan"
date: 2012-03-11
forum: General Help
---

### Post by Kitkin15 on 2012-03-11
When i do an Nmap scan on my network i get the Ip address on every computer, but for some reason MY computer is the only one that also shows the name of my computer. I dont understand why. Ive scanned other Ubuntu laptops that were on my network, but i didnt get the name of their computer. Is there any way i can change it so it doesnt show my computers name?

Here is an example of what you would see (The name of my computer is spoofed though)

"Nmap scan report for 192.168.1.106
Host is up (1.2s latency).
Not shown: 999 filtered ports
PORT     STATE SERVICE
5357/tcp open  unknown
MAC Address: (MacAddress)

Nmap scan report for (NameOfComputer) (192.168.1.131)
Host is up (0.0000050s latency).
Not shown: 998 closed ports
PORT     STATE SERVICE
25/tcp   open  smtp
6667/tcp open  irc"

Mine is the second computer. I do like that no scans show my MacAddress, but i do no like that it shows my name of my laptop. I still see that as being a huge security risk. 

  -Kitkin15

---

### Post by Dangertux on 2012-03-11
First off, seeing either the MAC address or the name of the computer isn't a security issue in and of itself. Supposing you're not naming your computer I_RUN_A_VERY_VULNERABLE_VERSION_OF_PROFTP or something like that.

That being said you're seeing that information because nmap is actually scanning over the loopback interface (because it's running on that machine). Your firewall is probably configured to allow all loopback traffic, thus does not do anything about the nmap probes. This is expected behaivor.

Hope this helps.

---

### Post by Kitkin15 on 2012-03-12
> **Dangertux said:**
> First off, seeing either the MAC address or the name of the computer isn't a security issue in and of itself. Supposing you're not naming your computer I_RUN_A_VERY_VULNERABLE_VERSION_OF_PROFTP or something like that.

That being said you're seeing that information because nmap is actually scanning over the loopback interface (because it's running on that machine). Your firewall is probably configured to allow all loopback traffic, thus does not do anything about the nmap probes. This is expected behaivor.

Hope this helps.


A friend came over and he scanned and he got the same thing.

I see this as a security issue because i do not want anyone to know the name of my computer, and i do not want them to try and bring anything to me.

Basically this is me trying to save my self if the cops try and search my network. Though i dont look up anything "illegal" i do look up alot of Hacking, and right now theres stuff going on where that me looking that up could look fishy. So i would like to take care of this if possible.

---

### Post by Dangertux on 2012-03-12
> **Kitkin15 said:**
> A friend came over and he scanned and he got the same thing.

I see this as a security issue because i do not want anyone to know the name of my computer, and i do not want them to try and bring anything to me.

Basically this is me trying to save my self if the cops try and search my network. Though i dont look up anything "illegal" i do look up alot of Hacking, and right now theres stuff going on where that me looking that up could look fishy. So i would like to take care of this if possible.

I don't think you have anything to worry about.

However -- since this seems to be concerning you so much let's get a few basic questions out of the way.


When you say your friend comes over and sees the same thing. Do you mean he ALSO see's his computer name or he is seeing YOUR computer name? (The one you were previously scanning from).

Do you have your firewall enabled? Either via ufw/gufw or a custom set of iptables rules. If so, what type of settings are you using with it, this would be a firewall issue.

If you can answer these questions I can help you get the result you want.

---

### Post by Kitkin15 on 2012-03-12
> **Dangertux said:**
> I don't think you have anything to worry about.

However -- since this seems to be concerning you so much let's get a few basic questions out of the way.


When you say your friend comes over and sees the same thing. Do you mean he ALSO see's his computer name or he is seeing YOUR computer name? (The one you were previously scanning from).

Do you have your firewall enabled? Either via ufw/gufw or a custom set of iptables rules. If so, what type of settings are you using with it, this would be a firewall issue.

If you can answer these questions I can help you get the result you want.


Thank you very much for help.

When my friend came over he scanned and got the name of my laptop, which shouldnt have happened. 

I didnt have a Firewall at the time, though i did get "Firestarter" Today, i have it at the "out of the box" settings, i have no configured it yet. If theres a better Firewall to use please let me know, i honestly dont know which is best for Ubuntu 10.10, ive never bothered to look into it for Linux, only for Windows.

---

### Post by Dangertux on 2012-03-12
> **Kitkin15 said:**
> Thank you very much for help.

When my friend came over he scanned and got the name of my laptop, which shouldnt have happened. 

I didnt have a Firewall at the time, though i did get "Firestarter" Today, i have it at the "out of the box" settings, i have no configured it yet. If theres a better Firewall to use please let me know, i honestly dont know which is best for Ubuntu 10.10, ive never bothered to look into it for Linux, only for Windows.

Okay here is the thing about Firestarter. You only have one firewall, it is the netfilter/iptables kernel modules. Firestarter, UFW, GUFW etc are all just front ends for controlling that.

Additionally Firestarter is quite buggy and no longer in development / supported. I personally prefer to use iptables directly, as it's more portable to other distros and in my opinion more intuitive. However , if you're new you can utilize UFW (which comes with Ubuntu) or GUFW which is a graphical wrapper for UFW.

Hope this helps.

---

### Post by marinara on 2012-03-13
turn off samba and nmbd

---

### Post by Kitkin15 on 2012-03-15
> **Dangertux said:**
> Okay here is the thing about Firestarter. You only have one firewall, it is the netfilter/iptables kernel modules. Firestarter, UFW, GUFW etc are all just front ends for controlling that.

Additionally Firestarter is quite buggy and no longer in development / supported. I personally prefer to use iptables directly, as it's more portable to other distros and in my opinion more intuitive. However , if you're new you can utilize UFW (which comes with Ubuntu) or GUFW which is a graphical wrapper for UFW.

Hope this helps.


Ok i will do :) Thank you very much again, you were very helpful.

---

