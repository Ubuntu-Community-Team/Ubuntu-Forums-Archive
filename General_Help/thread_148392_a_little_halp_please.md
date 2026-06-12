---
title: "a little halp please"
date: 2006-03-22
forum: General Help
---

### Post by montablac on 2006-03-22
i need to set up ONE laptop with linux to impress the cad teacher about linux,and i chose ubuntu,but ive hit a dead end

iv got it siting on my lap at home,and i want to set up a temp network between both my linux computers

i CAN NOT get any new software onto the laptop besides that that comes on the CDS

the computers are:
one with a net connection(desktop):
ubuntu 5.10
56k connection
256 KB ram
i386 archetucher
2 cd roms/1 cd righter/1 dvd reader
usb 2.0 slots
a pentium 3 processer
a 10 MB network

the laptop:
ubuntu 5.10
PPC archetucher
1 cd drive
an i book V2


you get the pictuer,and i do have a crossover cable

im scred arint i?](*,)

---

### Post by Ubuntuud on 2006-03-22
Does you computer have only 256 KB RAM? I surely hope you mean MB...

---

### Post by Herman on 2006-03-22
Perhaps you would be interested in trying to set up SSH networking between the two machines. 
They both have Ubuntu, so would both already have SSH 'client' software. The 'client' software can make a connection to another computer but is not open for another computer to initiate a connect ion to it.
On your desktop that has a dial-up connection, download and install openssh-server and ssh server, from the networking packages listing in Synaptic. 
That will make your desktop into an SSH 'server' that will be open for SSH connections on port number 22. That should be okay as long as you have a good secure passcode. You should not use a word from the dictionary as a password, it should be a mixture of random numbers and letters and punctuation marks at least eight characters long. You can include spaces and capital letters.
Have your crossover cables plugged into the two computer's ethernet ports and make the connection from the laptop (client) to the desktop (server). 
[ This webpage tells you how to do it]("http://users.bigpond.net.au/hermanzone/p11.htm"), with illustrations, I am not sure if it will matter if you are using a crossover cable rather than a router. Hopefully it won't make any difference. If you want, just give it a try and see what happens. SSH is probably the simplest networking to set up and also the most secure as it uses encryption. (Secure provided you have a good secure passcode). 
:D I hope this helps you. (Herman)

---

### Post by montablac on 2006-03-22
thx herman

and yes,i got messed up,it is MB

any way,can i use synpatic through this connection,cause i want to aim for that if possable

---

### Post by Herman on 2006-03-22
I used to use a 56k dial-up modem for my internet too until a year ago. I'm sure you can still use synaptic although it will take longer, but the SSH software is only a small download as far as I know, I guess maybe it will take two or three minutes or so. maybe less, maybe more, but it should work.

 If you haven't used Synaptic before you really should try it.  You might need to enable some repositories first.
[aysiu's PDF Ubuntu Beginner's Guide]("http://ubuntu.xgn.com.br/ubuntu_user_guide.pdf") is the best way to find out more about enabling repositories and using Synaptic. Save yourself a copy. Synaptic and enabling repositories are only some of what aysiu explains in the guide.
 It is really worth looking that up and following aysiu's instructions. There are thousands of great free software packages you can try out from Synaptic besides SSH networking. You can get some things from 'Applications', Add Applications' too. But if you enable all the repositories the 'Add Applications' will have a lot fewer items 'greyed out' as well.

---

### Post by montablac on 2006-03-22
no,i mean can i use sympatic THROUGH SSH to get software on the laptop

or does any one know whare i can get some PPC software in .deb/.rpm packages

or can i get a guide to compile things from source?

---

### Post by alamba on 2006-03-22
montablac: Allow me to rewrite your query here just to make sure I've got it right. 
1.You have a ubuntu 5.10 desktop that connects to the internet using the dial-up modem. This machine also has a lan port.
2.You have a laptop with ubuntu 5.10 and this has a lan port too.
3.You have a cross over cable
4.You would like your laptop to be able to access the internet (to use synaptic) via the desktop by creating a network between the desktop and the laptop

Now, if the above is correct, below is your solution:
1. On desktop 5.10, use synaptic to get firestarter.
2. Dial-up to the internet and then use firestarter >> properties (i think) to share the internet connection
3. Also enable the DHCP option in firestarter
4. Make sure you have the laptop and desktop lan cards connected with the cross over cable
5. On laptop do the following on a terminal window:
- ifconfig (do you get an IP)
- ping 4.2.2.2 (can you ping the internet)
- ping oracle.com (does the name get resolved to an IP)
- from a browser try accessing any site (does it work)

If you're now able to browse you can then use synaptic to install anything you like on the laptop.

A

---

### Post by montablac on 2006-03-22
THANK YOU
thats just what the doctor orded

---

