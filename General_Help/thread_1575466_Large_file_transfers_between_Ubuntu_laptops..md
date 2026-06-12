---
title: "Large file transfers between Ubuntu laptops."
date: 2010-09-15
forum: General Help
---

### Post by aum11 on 2010-09-15
I often have a situation where I need to move many large folders from 1 laptop to another, where both are next to each other.  Both would be running Ubuntu.

Is it possible to do this via a cable?  If so it would be much faster than using an external HDD which is how I currently do the transfer.And these files are too large(200gb) for network transfer.

Suggestions?

Thanks.

---

### Post by moore.bryan on 2010-09-15
Your files (plural) are larger than ~2TB? Holy crap...
[http://en.wikipedia.org/wiki/Ethernet_crossover_cable](http://en.wikipedia.org/wiki/Ethernet_crossover_cable)

---

### Post by aum11 on 2010-09-15
Thanks, that now reads 200GB.

Suggestions? cabling?

---

### Post by theozzlives on 2010-09-15
Just get a router and transfer your files via the network.

---

### Post by moore.bryan on 2010-09-15
Cross-over cable should get the job done... available online in dozens of places.

---

### Post by aum11 on 2010-09-15
So crossover cable rather than Ethernet cable?

And what happens software wise once the cable is connected?  How and where do I find the files on the other laptop?

Thanks.

---

### Post by DarthScape on 2010-09-15
You don't NECESSARILY need a crossover cable. Most computer's will auto-detect. If you connect via ethernet, you could either use the self-assigned ip address or give them each an ip address. Then, just right click the folder, and share :D

---

### Post by CharlesA on 2010-09-15
If both machines have gigabit ethernet ports you can use a regular ethernet cable.

Make sure they can ping each other. :)

---

### Post by Easy Limits on 2010-09-15
Try using Giver.   It's in the Software Center.

---

### Post by aum11 on 2010-09-15
I just tried hooking up 2 relatively new laptops(so Ethernet cable should work?) and tried nautilus and network icon but could see no mention of the other laptop or it's files.

I am sure it must be something simple.

BTW, when I do this both laptops are offline, due to this process tying up their Ethernet slots, and no wireless available here.

Thanks for Your help...much appreciated.

---

### Post by CharlesA on 2010-09-15
Check ifconfig on both to make sure they have an ipaddress.

See if you can ping them.

```
ping ipaddress
```

I'm not too familar with the GUI, but you could always install ssh and use sftp to transfer the files from one to the other, then purge ssh when you are done.

---

### Post by aum11 on 2010-09-15
Just to be clear, there are 2 laptops next to each other and not online.  There is an Ethernet cable connecting them.  How can I transfer large volumes of data between them.

Trying ifconfig with them both offline results in their addresses being the same...127.0.0.1.

I imagine this is a common requirement for lots of folks.

Suggestions please.

Thanks.

---

### Post by CharlesA on 2010-09-15
You have to set an ip address for each of them.

You can set one temporarily by running this command on one machine:

```
sudo ifconfig eth0 192.168.1.2/24
```

And this one on the other:

```
sudo ifconfig eth0 192.168.1.3/24
```

That'll allow them to see each other.

---

### Post by aum11 on 2010-09-15
Thanks CharlesA,

did as You suggested on both laptops, and then I changed (on both laptops)eth0/ipv4 from auto dhcp to link local only...could not find the other laptops folders.

So then I tried changing eth0/ipv4 to "shared to other computers"...still could not locate any folders from the other laptop.

What am I not doing?

Thanks.

---

### Post by CharlesA on 2010-09-16
I've always found that it's a bit of a pain to get file sharing working.

I've not used file sharing between two Ubuntu boxes, but it seems overly complicated.

What I suggest you do is this: See if you can ping each machine from the other by the ip address.

Install openssh server on the machine with the files you want to transfer over, then connect from the machine you want to files on.

Places > Connect to Server > SSH > Put info in > connect.

Then just drag and drop the files where you want them. :)

---

### Post by aum11 on 2010-09-16
Thanks CharlesA,

should I try this using the eth0 option of linked-local only or shared to other computers?

I guess the 1st.  I will try that now.

---

### Post by macem29 on 2010-09-16
noob here, but I've had some success sharing between my ubuntu netbook and an XP desktop...
I think you need 2 things working here: 1. basic connectivity: get yourself pinging, 2.  you need to setup
file sharing

---

### Post by CharlesA on 2010-09-16
> **aum11 said:**
> Thanks CharlesA,

should I try this using the eth0 option of linked-local only or shared to other computers?

I guess the 1st.  I will try that now.

As long as you can ping the other machine, it means you have connectivity. Once you have that, the rest is easy. :)

---

### Post by aum11 on 2010-09-16
the $ ping 192.168.1.3/24
ping: unknown host 192.168.1.3/24


ping did not work using either option.

---

### Post by CharlesA on 2010-09-16
> **aum11 said:**
> the $ ping 192.168.1.3/24
ping: unknown host 192.168.1.3/24


ping did not work using either option.

Ok. Try just pinging 192.168.1.3. The /24 is the netmask, and isn't needed.

If that doesn't work try this:

```
sudo ifconfig eth0 up
```

Then post the output of this: ```
ifconfig eth0
```

---

### Post by aum11 on 2010-09-16
so i finally got a successful ping when I used eth0 with link-local only, and used the auto generated ip addresses found by right clicking the network icon/connection information.

However I could not locate the other computer's folders.

Then, success when installed Giver on both laptops.

It worked fast,clearly and perfectly.

Thanks for Your help and I hope this story helps others.

And this is solved.

---

### Post by mahiyar on 2010-09-16
aum11, can you please, in a nutshell enumerate all the steps you took to get the connection working.  I did read the whole post, was a bit confused. It will help me and others too, a how-to kind of thing. Thanks in advance.

---

### Post by aum11 on 2010-09-16
Ok, so here is a summary of how I am transferring files and folders between 2 Linux computers which are in close proximity.

1. disconnect the internet (cable or wireless) from both laptops.
2. link up the laptops via an Ethernet cable
The following applies to both computers:
3. right click on the network icon on the top panel, edit connections,wired, select auto eth0,IPv4 settings tab,choose method link-local only, apply.
4. left click network icon on top panel, click auto etho.
5. install "giver" via applications/Ubuntu software centre
6. applications/internet/giver to start Giver.

When Giver is installed on both machines it will automatically identify the  usernames installed on each machine.  It is simply then a case of clicking on the name of the desired recipient and identifying which folders or files You wish to transfer to which user. Giver preferences allow for specification of location for received files(default is Desktop).
NB.Giver has problems if You have the same user name on both machines.  Simply change the username slightly on one machine temporarily(system/admin/users and groups/name change).

When transfers are completed,reset auto eth0 to it's original setting.

Sweet.

Hope this helps You.  It has certainly made my life easier by no longer needing to transfer large files via external HDD.

---

