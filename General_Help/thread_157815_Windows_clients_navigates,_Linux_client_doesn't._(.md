---
title: "Windows clients navigates, Linux client doesn't. (NAT running on a linux server)"
date: 2006-04-09
forum: General Help
---

### Post by leogoiano on 2006-04-09
I have a LAN on my house that I use to share my internet connection(pppoe). We have here 5 machines(1 server on hoary, and 4 clients: 3 on windows xp and 1 linux breezy).
My server runs hoary. I configured my iptables to use nat masquerading and allowed ip_forwarding for my machines.
The problem is that the windows machines can browse internet with no problem but my linux machine client is having problems. I cannot access some sites and even apt-get cant connect to some reppositories also...

I've read about MTU and MSS and thought it was the problem. It said that if I had mtu or mss is set to a higher value(over 1500) inside my lan I could have problems. So I set my linux CLIENT machine to use mtu 1400 and my SERVER has mtu set to 1492 (altough iptables says tcpmss is 1412). Anyway, I tried to use a higher and lower value on my client but it didnt solve the problem.

I just don't know what to do anymore... We had a router until last week(OCR812 3com) working very fine but I tried to upgrade its firmware and if screwed... then I had to install a server to do the routing work. No change was made anywhere over the LAN. The only thing I changed at the clients were the ips, gateway and dns. It was supposed to work. I wonder if Windows
XP can auto set some kind of configuration that my linux(client) can't. 

I also set all the policies to ACCEPT on iptables so I would not filter anything that could cause that problem.

I appreciate if anyone can help here...
Leonardo Rodrigues.

PS- sorry for my poor english.

---

### Post by dcstar on 2006-04-10
[QUOTE=leogoiano]I have a LAN on my house that I use to share my internet connection(pppoe). We have here 5 machines(1 server on hoary, and 4 clients: 3 on windows xp and 1 linux breezy).
My server runs hoary. I configured my iptables to use nat masquerading and allowed ip_forwarding for my machines.
The problem is that the windows machines can browse internet with no problem but my linux machine client is having problems. I cannot access some sites and even apt-get cant connect to some reppositories also...
.....[/QUOTE]
Do some traceroutes from the Linux client to various websites, and post the results.

You may also want to do the same tests from the Windows clients and compare the results.

---

### Post by Celerex on 2006-04-10
My first question is it ALWAYS no 'internet' access on your ubuntu machine? All websites, all ftp, all rsync (apt)? Can you ping an ip address? i.e, can you find the ip address of some website by using your windows boxes and then ping it from your ubuntu box without a problem? Can you surf to pages using the ip address? Can you ubuntu box connect to all your local boxes as it did before?

A network topology might help a little to understand. IP addresses of your machines along with their current DNS, netmask, gateway, wins, etc settings.

---

### Post by leogoiano on 2006-04-10
Here are the traceroutes results for archive.ubuntu.com on windows and linux
[ATTACH]8183[/ATTACH]

[ATTACH]8184[/ATTACH]
I couldnt get any traceroute w/ windows (tracert) even waiting for a high timeout...

# My LAN configuration : 
# gateway    192.168.157.1      (eth0 on server)
# dns           200.204.0.10
# submask    255.255.255.0
#
# clients IP range    192.168.157.2 / 6
# no wins

I can resolve hostnames but navigation is terrible(linux)... Some webpages only open if I keep reloading them up to 20 times(yahoo/mail and gmail)

Look at this. Its my ping(1500 bytes) to archive.ubuntu.com from linux client. Got 63% loss. The same happens on windows.
[ATTACH]8188[/ATTACH]

I think there may be a problem on the server. Somehow Windows XP has something autoset that minimizes some error or anything. Some configuration on window size, error retry, I don´t know...
My server is an AMD K6-II 400mHz - 196Mb RAM

I dont believe thats a common problem and probably needs high network knowledge. But I appreciate any help you can give me. anything on configuring the server etc...

regards

Leonardo Rodrigues

---

### Post by leogoiano on 2006-04-10
I just remebered that a friend told me about having the same problems.
She also has a LAN sharing internet and cant connect to few websites. even google.com wont open. Their server run on a 486.

Look what I just read on cisco.com

#Sometimes a router has a link with a large (1500 byte) MTU, but the router is unable to #deliver a datagram of that size over that link. That router does not return a "Fragmentation #needed but DF set" ICMP error to the sender, because the link does not actually have a small #MTU. However, large datagrams are unable to pass through the link. Therefore, PMTUD does #not help and all large-packet transmission attempts through this link fail.
#
#This is sometimes due to a lower layer problem with the link, such as a Frame Relay circuit #with a too-small MTU and too little buffering, a malfunctioning channel service unit/data #service unit (CSU/DSU) or repeater, an #out-of-spec cable, or a software or firmware #defect. 

Do you think setting a lower MTU could solve the problem? how low can I go? If that is somehow related to the CPU capacity what I can I do not to overflow the server? higher or smaller MTU?

thank you

---

