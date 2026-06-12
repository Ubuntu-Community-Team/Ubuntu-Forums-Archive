---
title: "&quot;Ubuntu side&quot; of LAN network question"
date: 2006-03-22
forum: General Help
---

### Post by djsroknrol on 2006-03-22
Hello to all....

Well, after fiddling with every cotton 'pickin config file I could look at and tweak, the LAN is running well, except there is this funny quirk I guess you could call it....There are 4 'puters running 98SE and the Ubuntu box I'm on writing this with (BTW, I love it...'can't wait till I say bye-bye to M$). The windows shares all work fine, and the Ubuntu install shares just as well, but if I go to Places>Network servers, it takes 10 to 15 secs to load...it almost fooled me the first time I tried, I  thought it was broke....once you go to a shared drive on another 98 machine, and you open it, it moves thru files as fast as the windows shares do. File transfers are no problem either way.  I am at a loss as to why it does that. Any takers?..I'll be happy to post whatever info you might need to help me thru this...

Thanks,

Bob

---

### Post by dragomirov on 2006-03-22
A first tip is to "CTRL+L" in the nautilus window to bring up the address line, then type "smb://xxx.xxx.xxx.xxx (substitute the various x with the ip of the machine you want to connect to)

Another way is to open gnome menu choose "Connect to server" and configure it.

Hope it will help

---

### Post by dbott67 on 2006-03-22
It could be related to name resolution as well.  As Dragomirov suggests, you may just try to connect via the IP address.  Normally, on smaller Windows networks, Netbios is responsible for name resolution (it rides on top of TCP/IP).  This allows users to browse by name using **\\computername** (aka the NETBIOS name) or by browsing the Network Neighbourhood.  By just using the IP address, you would be bypassing the name resolution and perhaps speeding up the connection.

On larger peer-to-peer Windows networks (more than 20 or so Windows 9x boxes), people would frequently experience this problem of not being able to see all computers in the Network Neghbourhood.  One of the work-arounds would be to add the IP address and computername to the 'lmhosts' file, but it required static IP addresses.  In linux, you can configure the lmhosts file in a similar fashion (/etc/lmhosts).  For more info check here [http://www.die.net/doc/linux/man/man5/lmhosts.5.html](http://www.die.net/doc/linux/man/man5/lmhosts.5.html)

On large client-server networks (pre-Windows 2000), network admins would utilize the WINS service that would "register" the name of each computer that logged onto the network dynamically and would allow you to easily search for other computers by using the Network Neighbourhood.  Today, Windows 2000/2003 networks use DNS to resolve computers in the same fashion.

Hope this information helps.

-Dave

---

### Post by djsroknrol on 2006-03-22
first off...thank you guys...it's been bothering me for about two weeks now...Dragomo, I went thru all of that..SMB.conf was off like everyone else in the forum to start off with...I worked that and got the LAN running...but the problem is one way, and not the shares...finding 'puters from "Ubuntu" was slow...everything works fine, and when you get to a certain point into that computer, it "flys" again....that's what makes me agree with gabott...it might be a name resolution issue somehow....I don't know enough about topology to know if the linux side can be static, while the rest of the winboxes can be on dhcp and still comunicate properly...any other ideas or suggestions ??

---

### Post by djsroknrol on 2006-03-22
Gentlemen...

It seems as though I owe Dargomirov an apology...not to take his suggestions lightly, I tried it, and it was lightning...it solved what I wanted...now, how do I make that permenant?..like I said earlier, I don't quite understand larger LAN's and especially guess, without windows "automatic"help...help me break the M$ chains....

---

### Post by djsroknrol on 2006-03-23
[QUOTE=dbott67]It could be related to name resolution as well.  As Dragomirov suggests, you may just try to connect via the IP address.  Normally, on smaller Windows networks, Netbios is responsible for name resolution (it rides on top of TCP/IP).  This allows users to browse by name using **\\computername** (aka the NETBIOS name) or by browsing the Network Neighbourhood.  By just using the IP address, you would be bypassing the name resolution and perhaps speeding up the connection.[/QUOTE]

Dave..would you have any ideas or know how to make IP address lookups permanent?...Dragomirov and you were right...the more I move around that way, the more it acts like it should....The one strange thing that I noticed was that when I do address lookups in Nautilus, the history shows things like "Windows network: Analee on Analee" when I lookup her 'puter.....is that right?...it doesn't seem right to me...

---

### Post by dbott67 on 2006-03-24
It depends on how your network is configured as to which is the best/easiest way to set ip up.

Do you have a home cable/dsl router (such as D-Link, Linksys or Netgear) that uses Network Address Translation (NAT) and DHCP to supply interal LAN computers with IP addresses?  If so, there is a feature in the DHCP settings called "Static DHCP" (or something similar) that allows you to assign an IP address to a specific machine (by checking the MAC address of the NIC).

You could assign a specific IP address to each machine, and then create an lmhosts file (it's just a plain text file called 'lmhosts' in the /etc directory) that contains the IP address and computer name of each computer.

The format is as follows:

IP.address.of.computer1 <tab> computername1
IP.address.of.computer2 <tab> computername2

Just substitute the correct IP address and computer name.  For example, if I've got 3 computers named **winxp**, **win98** and **breezy**, and the respective IP address of each was 192.168.1.100, 192.168.1.101 and 192.168.1.102, then my lmhosts file would look like this:

```
192.168.1.100       winxp
192.168.1.101       win98
192.168.1.102       breezy
```

Whenever I browse the network, my computer will check the lmhosts file first for name resolution and speed up the process.

Hope this helps.

-Dave

---

### Post by dbott67 on 2006-03-24
Oops, I forgot the other way you could do it...

You could just assign 'static IP addresses' to each computer, which isn't so bad for a few computers, but if you have lots, then it's a pain.

You would need to enter/assign the following information for each computer:

- IP Address (unique for each computer)
- Subnet mask 
- Gateway address
- DNS server address

You would still need to create the 'lmhosts' file on each computer (in Windows, the location depends on the version.  For XP, it's **C:\WINDOWS\system32\drivers\etc**.  For 9x/Me, it's **C:\Windows**).

Of course, making a small mistake in any of the settings above can cause connectivity issues, so I prefer using 'static DHCP' as outlined in my previous post.

---

### Post by djsroknrol on 2006-03-24
Hi again Dave...I want to thank you and Dragomirov again for your help...I love this distro, and I'm sure I'll be going with Dapper too in June....back to my problem...

I'm running a cheepie CompUSA cable/dsl router going into a Kensington 
KNE8TP/WG workgroup hub. Here is the listing for all the 'puters in the house...

DHCP Client List
Assigned IP Address 	Host Name 	MAC Address
192.168.8.17 	  Analee 	00-09-5B-08-F6-DD
192.168.8.18 	  JEN 	00-00-E8-13-22-8B
192.168.8.19 	  (Unknown) 	00-0D-87-6D-F6-5C
192.168.8.20 	  AMD400 	00-80-19-30-49-8D
192.168.8.21 	  Fred 	00-40-05-05-43-1A

This is a readout from the router itself...it has already assigned  IP #'s and MACs to everyone...

AMD400 is the test bed 'puter that is off alot lately..."server" (which is the Ubuntu box) comes up oddly as "unknown". That might be part of this DNS problem? (haven't figured out how to fix that yet either). My lmhosts file is empty...now it's starting to make sense..will post again on the results...thanks again...

---

### Post by dbott67 on 2006-03-24
Just for clarification, the MAC address is not assigned by the router, it's a unique serial number that's been assigned to the network card in each computer during manufacturing.  The MAC address is what every device ultimately requires in order to communicate.

Of course, humans have a hard time remembering all of those hexadecimal numbers, so they developed an addressing scheme (IP) that assigns decimal numbers to machines (i.e. 192.168.8.17).  ARP (address resolution protocol) maps the IP address to the MAC address.

Add another layer (DNS) to make it easier to remember computer addresses is to map IP addresses to fully qualified domain names such as [www.ubuntuforums.org](www.ubuntuforums.org), so that we don't have to remember IP addresses.

On smaller Windows networks, they had a service called WINS (Windows Internet Naming Service) that mapped the netbios computer name to IP address and allowed people to search by using \\computername.

The difficulty is that you need servers running the DNS or WINS service in order to automatically register & map the computer name or FQDN to the IP address.  Without those services running, you need to manually maintain your own 'hosts' file (for DNS) and 'lmhosts' file (for WINS).

```
hostname.domainname.com <-uses-> hosts file/dns <-to get-> ip.address.of.computer <-which uses-> ARP <-to get-> MAC address 
```
```
hostname (aka Netbios name) <---> lmhosts file/WINS <---> ip.address.of.computer <---> ARP <---> MAC address 
```

There's also rdns and RARP (reverse DNS and reverse Address Resolution Protocol) that performs the lookups in the reverse order (from MAC to IP to FQDN).

-Dave

---

### Post by dcstar on 2006-03-24
[QUOTE=djsroknrol]Hello to all....

Well, after fiddling with every cotton 'pickin config file I could look at and tweak, the LAN is running well, except there is this funny quirk I guess you could call it....There are 4 'puters running 98SE and the Ubuntu box I'm on writing this with (BTW, I love it...'can't wait till I say bye-bye to M$). The windows shares all work fine, and the Ubuntu install shares just as well, but if I go to Places>Network servers, it takes 10 to 15 secs to load...it almost fooled me the first time I tried, I  thought it was broke....once you go to a shared drive on another 98 machine, and you open it, it moves thru files as fast as the windows shares do. File transfers are no problem either way.  I am at a loss as to why it does that. Any takers?..I'll be happy to post whatever info you might need to help me thru this...

Thanks,

Bob[/QUOTE]
What is in your /etc/nsswitch.conf file?

[http://ubuntuforums.org/showthread.php?t=100739&highlight=hosts+dns](http://ubuntuforums.org/showthread.php?t=100739&highlight=hosts+dns)
[http://ubuntuforums.org/showthread.php?t=88206&highlight=hosts+dns](http://ubuntuforums.org/showthread.php?t=88206&highlight=hosts+dns)

---

### Post by djsroknrol on 2006-03-24
Hello Davids'.....

This forum has been a great help in solving problems for me, and this one has been the toughest so far....here's the latest:

Dbott67....I edited hosts and lmhosts, but got locked out of the sharing 'puters unfortunately.  I studied your posts and went snooping to learn more about DNS. I was convinced you were on the right path, and these forums are for Ubuntu, not networking. I didn't want to waste peoples time on my ranting over not understanding.

dcstar...I looked at the thread and followed the code....not much  difference...and then I had a thought....I went to System>Administration>Networking and looked at the config on eth0 and for the first time, noticed a "hosts" tab. I decided just for experimentation to plug the IP's and 'puter names into "add's" on that list, and all I can say is YEAH...I cut the loading time by 2/3 !! now going from shared 'puters to shared folders within each box is 2 - 3 sec compared to the 10 - 15 in the begining...I thiink I'll live with that...

I hope this thread can help someone and I'd like to put that thread link up again as it was very helpful....As always, this forum has the answers, and I thank you for them

[http://ubuntuforums.org/showthread.php?t=100739&highlight=hosts+dns](http://ubuntuforums.org/showthread.php?t=100739&highlight=hosts+dns)

---

### Post by dcstar on 2006-03-24
[QUOTE=djsroknrol]
.....
dcstar...I looked at the thread and followed the code....not much  difference...and then I had a thought....I went to System>Administration>Networking and looked at the config on eth0 and for the first time, noticed a "hosts" tab. I decided just for experimentation to plug the IP's and 'puter names into "add's" on that list, and all I can say is YEAH...I cut the loading time by 2/3 !! now going from shared 'puters to shared folders within each box is 2 - 3 sec compared to the 10 - 15 in the begining...I thiink I'll live with that...
.....[/QUOTE]
Did you install the winbind package?

---

### Post by djsroknrol on 2006-03-24
Yes, I followed the thread to the tee, but it didn't seem to make any great difference....It was only after I added the IP's of the other boxes to the hosts tab, was I able to get a significant difference in name resoultion lookups...it was really weird....thanks alot for your help...

Bob

---

### Post by NetMatrix on 2006-03-24
Just thought I'd make a little note here for anyone reading this thread.  I do tech support for a company and we have about 70 sites that we have to ssh into.  Rather than having to mess with pointing every machine to one DNS for name resolution we just enter every site into /etc/hosts and it works really well.  So just in case you have some of the same issues and don't feel like setting up forward and reverse lookup zones and so on.  Just set some static addresses and put them in your /etc/hosts file.

---

### Post by dbott67 on 2006-03-25
[QUOTE=NetMatrix]...we just enter every site into /etc/hosts and it works really well....[/QUOTE]

This does work well for small networks with static IP addresses.  The one thing to keep in mind for anybody that uses this method (or adding to their lmhosts file as I outline in a previous post) is that if the IP address changes (either because the remote machine uses DHCP or a public website switches ISPs or whatever) you would not be able to access the computer until you updated the hosts/lmhosts file.

Not a big deal for those that do this sort of stuff on a regulare basis, but it can lead to problems if you forget that you edited the hosts file.  Just remember to document what you did if you employ this method.

[QUOTE=djsroknrol]...It was only after I added the IP's of the other boxes to the hosts tab, was I able to get a significant difference in name resoultion lookups...it was really weird....thanks alot for your help...[/QUOTE]

Bob, I'm not sure why this worked and directly editing the /etc/hosts file didn't, but I'm glad I was able to steer you towards finding the solution.  I'm also glad because I found out about winbind & mdns... another couple of tools to add to the kit! :)

-Dave

---

### Post by dbott67 on 2006-03-25
Deleted... accidental double-post from above.

---

### Post by djsroknrol on 2006-03-25
Dave;

I'm not sure why it didn't work either, but a sidenote to all of this...i did not uninstall winbind & mdns before I added the boxes in the hosts tab....could it be a GUI "hard wired" thing..I mean, using the graphical interface of Gnome as apposed to doing it via terminal?

Bob

---

### Post by djsroknrol on 2006-04-08
A post postscript to all of this....and I admitted that I didn't know enough about computer networking to know how to blend the Ubuntu box into the mix. The more I learned, the more it became something OTHER than the box(s). I tried ethtool and discovered that the workgroup hub that all the computers are tied to is an older 10mb/s hub, and my card was only running 10mb/s half duplex. all of the cards are 100mb/s full duplex cards, and all of them maxed out at 10mb/s naturally going thru it, including the Ubuntu 'puter. A new D-link 7 port broadband router is on the way. It goes to show that hardware CAN be suspect alot of the time, and should be checked  first before condeming the install. 

Thanks again guys.....

---

### Post by Techno.Scavenger on 2006-12-22
> **djsroknrol said:**
> 
dcstar...I looked at the thread and followed the code....not much  difference...and then I had a thought....I went to System>Administration>Networking and looked at the config on eth0 and for the first time, noticed a "hosts" tab. I decided just for experimentation to plug the IP's and 'puter names into "add's" on that list, and all I can say is YEAH...I cut the loading time by 2/3 !! now going from shared 'puters to shared folders within each box is 2 - 3 sec compared to the 10 - 15 in the begining...I thiink I'll live with that...


This should be the same as editing /etc/hosts file.... I just check it using Ubuntu 6.10.

---

