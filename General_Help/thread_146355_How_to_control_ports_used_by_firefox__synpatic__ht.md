---
title: "How to control ports used by firefox / synpatic / http..."
date: 2006-03-18
forum: General Help
---

### Post by linuxfroggy on 2006-03-18
Hello All,

I have a small issue for the last few days with access to internet via http. I have access via mail, ftp, but with http using firefox or trying to reach repositories with synaptic I have some problems. Here follows a summary :

- Synpatic : I can NOT reach the repositories
- I can reach google at google.com
- I can NOT get any other site
- mail : everything OK using Evolution
- ftp : work allright

Considering that and imagining it could be my router box (IPCOP, a speicialized distribution based on SmoothWall), I tried with another PC runnign windows : IT WORKS perfectly.
I also tried with Knoppix live CD on my Ubuntu box : IT WORKS perfectly too.

Looking at the different ports open on my router, I can see the different connexions opened and waiting for a reply and I noticed a difference between windows Internet Explorer (IE) and firefox : firefox is suing ports in the 45000-60000 range while IE is using a lower range : 1000-2000. I wonder if this can be an indication with my internet provider filtering/rejecting too high ports value.

My question is then the following : where can I find the setup of firefox and how can I control ports range used by firefox ?

Best regards,

LinuxFroggy.

---

### Post by powder on 2006-03-18
Not sure where you got those port ranges from.  Web browsers establish outgoing connections on port 80, they don't listen for incomming connections.

---

### Post by Treebeard on 2006-03-18
Maybe "google.com" is still in your browsers cache..
Can you "ping www.google.com" ?
Can you ping to e.g. "82.211.81.166" (ubuntu.com) or some other static IP address that you know ?
It might be related to your DNS.. 
What does "cat /etc/hosts" say ?

---

### Post by linuxfroggy on 2006-03-18
Hello,

Thanks a lot for the answers.

For Powder, I understand that http is listening on port 80, which is what everyone would expect but it seems that once your are behind a router, such as IPTables or the one I use (IPCop), active ports become dynamic. I have checked once again and it appears that the Windows Box is listneing on ports in the 1000-2000 range on the router side and on port 80 on internet side while FireFox or any other applicatins such as Synpatic listen on 45000-60000 on the router side and 80 on internet side. It is not completely unexpected except the http range for the Ubuntu machine which is completely new to me.

For Treebeard, I have tried to erase the cache and it didn't change anything : till can access to google and almost nothing else (few sites in Germany, nothing in France where I live...). I dont' understand why... Looking at the hosts file does not give much hints (I have not copied it as I am on the Windows Box for the moment ; sorry...). Regarding ping ; I have tried it yesterday night : I can ping anybody : [www.ubuntu.com](www.ubuntu.com), [www.google.com](www.google.com), ... That seems to indicate that the DNS is not the problem I guess.

Something new and somehow weird (at least for someone like me who has little knowledge and understanding on Linux) : Thinking that the port range was the problem but that http system on Ubuntu was the not the problem, I have uninstalled FireStarter (I am behing a linux based firewall router, it is not much an issue) and rebooted Ubuntu : IT WORKS NOW. Furthermore, looking at the IPCop routing table, it appears that now the port range from Ubuntu are in the 2000-4000 range.

Well, I do not understand completly why : I expect IPTables to change the port number to ensure routing but I do not understand why exactly range might shift so high and why routing could not be complete any more.

I hope someone can help to understand.

LinuxFroggy.

---

