---
title: "DNS/DHCP question"
date: 2006-04-18
forum: General Help
---

### Post by HiltonL on 2006-04-18
Hi.

I suck at networking, so I may be missing something fundamental here.  I'm trying to add an ubuntu machine to a primarily Windows network.  I've given the machine a hostname during the install (5.10).  It gets an IP automatically with DHCP, and I can see the network and the internet no problem.

However, I can't look up this machine with any other Windows machines on the LAN.  I have to use ifconfig to find out it's IP, and access it that way.  And it keeps getting allocated new IP addresses.  I don't want to use a fixed IP address, I'd like the DHCP server to allocate me one.

But what do I have to set up so that other machines can look this machine up by name?  Something with the DHCP config?  Or something else, like Netbios or WINS or something?

Aaaargh!  Stuck on this problem for AGES.

Thanks in advance for your help.

---

### Post by dcstar on 2006-04-18
[QUOTE=HiltonL]Hi.

I suck at networking, so I may be missing something fundamental here.  I'm trying to add an ubuntu machine to a primarily Windows network.  I've given the machine a hostname during the install (5.10).  It gets an IP automatically with DHCP, and I can see the network and the internet no problem.

However, I can't look up this machine with any other Windows machines on the LAN.  I have to use ifconfig to find out it's IP, and access it that way.  And it keeps getting allocated new IP addresses.  I don't want to use a fixed IP address, I'd like the DHCP server to allocate me one.

But what do I have to set up so that other machines can look this machine up by name?  Something with the DHCP config?  Or something else, like Netbios or WINS or something?

Aaaargh!  Stuck on this problem for AGES.

Thanks in advance for your help.[/QUOTE]

Do a forum search for netbios lookups, there are many posts outlining the solution.

---

### Post by bscbrit on 2006-04-18
I think that you need to install 'winbind'.

EDIT  If dcstar says otherwise - then I'm prepared to bet that he is correct and I am wrong! :D

---

### Post by bscbrit on 2006-04-18
[http://www.ubuntuforums.org/showthread.php?t=88206](http://www.ubuntuforums.org/showthread.php?t=88206)

Hey, what do you know?  Were both right!  Check the thread.

---

### Post by HiltonL on 2006-04-18
Thanks for your many attempts to assist.  However, that thread has my problem backwards.  The Ubuntu box cannot access other machines by name.  My problem is that I cannot access the Ubuntu machine from a Windows machine.

Perhaps I need to understand the network I'm on a little better.  When I type nslookup on a Windows machine, it seems to connect to a nameserver, which it queries against to find out the IP address of various machines.

Can anyone explain how this works?  My understanding was that Netbios was suitable for smaller networks, where each machine could simply broadcast it's information.  This seems to be an NT version of DynamicDNS... Is it WINS?

If I browse "Entire Network" in "Network Neighbourhood", I can see the Ubuntu machine.  But I just can't look up it's IP.  This suggests to me that NetBIOS is working, but some DNS registration is failing when it gets its IP allocated from DHCP.

Please excuse my lack of knowledge if I'm talking TOTAL rubbish.  I'm clueless here. ](*,)

---

### Post by bscbrit on 2006-04-18
OK, sorry if I got it back to front.  A quick bit of Googling (with a lot more still to do...) suggests that the easiest way to resolve this problem is to make the DHCP server allocate a specific IP based on the NIC hardware address.  By doing this it will allocate a fixed IP to computers that it recognises and allocate a spare IP address to new machines.  See if this thread explains it better than I can.

[http://www.tldp.org/HOWTO/DHCP/x369.html](http://www.tldp.org/HOWTO/DHCP/x369.html)

By doing this you could then enter the fixed IPs into your /etc/hosts file and the resolution would be done automatically.  This would work but seems to be a stop-gap solution for what you want.  I agree with you that it would be nice if, once the DHCP has allocated an IP lease, it then informed the DNS of the new IP and everything would then be automatic.  I don't know whether there is something to do this or whether it is simply a case that both you and I know too little about networking and this is already possible. :-k 

I'll continue to Google. However, there comes a point of diminishing returns.  For my small network, (usually 6 machines with 2 additional boxes from time to time) I use fixed IPs and simply ensure that my /etc/hosts is sent to all boxes on the network.  But as the network gets bigger, this method becomes more and more difficult to manage.  Only you can decide whether fixed IPs would meet your requirements or should we keep looking for a solution that will cope with any size of network but that you, in fact, will never actually need?

---

### Post by bscbrit on 2006-04-18
My first discovery is that this might be a problem that, in the Windows world at least, has no current solution:

> 
DHCP and DNS
Here is a favorite interview question of mine when I&#8217;m interviewing a technical professional: &#8220;Given your choice, which would you use on a network, DNS or DHCP?&#8221; Of course the answer is my favorite tax law response of &#8220;it depends.&#8221; I then probe further into why my perspective employee might use only DNS on network, make use of DHCP, or more likely than not, use both DNS and DHCP on the network. Of course I am still speaking of a Windows NT Server&#8211;based network, because if I&#8217;m discussing a UNIX-based network and my candidate mentions DHCP, he or she is out the door (remember that the UNIX community uses BOOTP, not DHCP). Let&#8217;s explore the relationship between DNS and DHCP.

Tip: Although you can use DNS to provide names for network resources, remember that a DNS configuration is static, and that can create problems. With DHCP, a host can easily have a different IP address if its lease expires. But no standard exists for updating DNS servers dynamically when IP address information changes in Windows NT Server 4.0. Note this will change in Windows 2000 Server when Dynamic DNS is introduced (this topic is discussed at the end of this chapter). So in Windows NT Server 4.0, DNS naming conflicts may occur if you use DHCP for dynamic allocation of IP addresses.



But I never accept such defeatist thoughts, so I will keep on looking....

---

### Post by bscbrit on 2006-04-18
Perseverance pays off:

[http://www.mattfoster.clara.co.uk/ddns.htm](http://www.mattfoster.clara.co.uk/ddns.htm)

[http://www.ops.ietf.org/dns/dynupd/secure-ddns-howto.html](http://www.ops.ietf.org/dns/dynupd/secure-ddns-howto.html)

[http://www.debian-administration.org/articles/343](http://www.debian-administration.org/articles/343)

[http://sourceforge.net/project/showfiles.php?group_id=132995](http://sourceforge.net/project/showfiles.php?group_id=132995)

Let me know if this solves your problem.

---

### Post by pappo on 2006-04-18
Do you have Samba running ?  If you do, you should be able to see your Ubuntu machine from your Windows machines.  That is what my network is.  1 Ubuntu, and 2 XP machines.   What I did was use DHCP for my network card on the Ubuntu machine, and installed samba on the Ubuntu machine.   Once I did that, I could see the Ubuntu from my XP.  When I bring up XP explorer, it sees my Ubuntu by the hostname I assigned it, and I can search through all my Ubuntu folders.  I don't care what the IP address is on the Ubuntu.  Unless you are doing something using fixed IP network stuff like a game server , I don't know why you would care what the IP address it, as long as your DHCP is issuing IP addresses that are in the same network as all your other boxes are in...for example I set my DHCP server (which is in my Dlink router) to use 192.168.0.120 to 192.168.0.130 for DHCP, and since I only have three machines that is more than enough and I know that all my machines are on the same Class C network.  I use DHCP for all my machines.

---

### Post by bscbrit on 2006-04-18
And finally, if you open Synaptic and search for 'dynamic DNS' it finds several packages which seem to do just what you want, already Ubuntu'ified ready for use. Good Luck:-D

EDIT:  I know that most of the results of the search are not what you are looking for, but autodns-dhcp, dnsmasq and others seem to fit the bill.

---

### Post by HiltonL on 2006-04-18
Wow!

Let me just say - I'm blown away by the level of effort that people, bscbrit in particular, have gone to to help me find a solution!  This Ubuntu community is unlike any other Linux or Open Source community I have seen, and it really gives me hope for the future of Open Source.
:KS :KS :KS 

Let me expand on my situation a little bit, because it seems that the full context is important.

This is a corporate network, with thousands of PCs, primarily Windows based.  I have been asked to set up a Linux box for application compatibility testing.  So perhaps I need to know more about the network I'm adding the computer to.  What I DO know is that it's Active Directory, DHCP based, but name lookups appear to be DNS, rather than Netbios scanning.

I'll go through the articles you've linked tomorrow when I'm at work again and see if any of them point me in the right direction.

Thanks SO much for all the effort, I'm stunned.

Cheers
Hilton

---

### Post by bscbrit on 2006-04-18
No problem - although now that you have explained exactly what you are trying to do I am less confident that I have found the solution that you are seeking. :-k  Pappo's solution is far simpler and will probably provide all you need, unless you actually need the IP numbers.

---

### Post by HiltonL on 2006-04-19
It appears that the DHCP client needs to inform the DHCP server of its hostname.  Windows seems to do this automatically, but it's not enabled by default on Ubuntu.

The description of the problem, how to fix it, and the logic behind it fix my problem exactly.  I need to edit dhclient.conf and add "send host-name <myhostname>".  I did all this, but it's still broken.  :(

Inexplicable, but it appears that my Ubuntu box is surely doing everything correctly, I'll need to continue to pursue the company domain admins to find out what's up.

Thanks for all the help!  I've learned a lot.
Cheers
Hilton

---

### Post by unholy1 on 2008-01-11
I had a similar problem to HiltonL. Following bscbrit's advice, I used synaptic to install autodns-dhcp, restarted, and the problem was fixed. I can now ping my ubuntu machine by hostname from the Windows boxes.

Thanks very much, everyone!!

---

### Post by unholy1 on 2008-01-14
Oops, nevermind. After speaking to our local network admin he thinks it was something else that he happened to be trying at the same time:

> The problem was that the security team have set DNS so it can be updated from a client that has a Kerberos certified connection to the windows domain (this is to protect against spoofed server addresses, unnecessary if you ask me!)  … samba would probably provide a connection with sufficient security to do this, the problem with this is that it is not guaranteed that the user has a connection to the windows domain that the DNS update can piggy back in on.  I don’t know if the same applies with WINS (I would expect it to) … not an ubuntu problem, it’s a windows one.

I have also set the DHCP server to publish its leases into the DNS (obviously DHCP running on a windows server has sufficient authority to do this) … but this seemed not to be working.


---

