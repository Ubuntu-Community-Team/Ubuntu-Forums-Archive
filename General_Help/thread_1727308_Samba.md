---
title: "Samba"
date: 2011-04-12
forum: General Help
---

### Post by sierra8804 on 2011-04-12
I have installed samba on Ubuntu server 10.10. I edited the smb.conf file and set the following:
workgroup = INFRATECHNET
netbios name = infratechserver1
wins support = yes
name resolve order = lmhosts host wins bcast
comment = File Server Share
path = /srv/samba/share
browseable = yes
read only = no
create mask = 0755
 
I restarted smbd and nmbd
sudo restart smbd
sudo restart nmbd
 
The windows XP box is also in the INFRATECHNET workgroup but I only see the windows box not the samba server. The windows box is on a 192.x.x.x network and the samba/ubuntu server is the external network 98.x.x.x network. I can ping the 98.x.x.x address from the windows box using the IP but not by the server name infratechserver 1.
 
Any suggestions?

---

### Post by sierra8804 on 2011-04-12
More information from the last post.
 
I am able to use the RUN command in windows and see the shares
[\\infratechserver1]("file://\\infratechserver1")
 
but the samba/ubuntu server does not appear in the MS Windows Network. Only the windows box I am browsing from.
 
Is this a samba issue or a hosts issue?

---

### Post by pricetech on 2011-04-12
It's a browsing issue.  If you can connect using the IP of the server, use it that way and be happy.

---

### Post by Wiebelhaus on 2011-04-12
Reboot the windows machine so it refreshes and sniffs out for other machines on the network.

---

### Post by sierra8804 on 2011-04-12
I would be happy with using the //servershare but most of the other users would be confused by it and since they are higher up the food chain I need to satisfy them. I did reboot the windows machine with no luck.
I'm sure it just something simple that I have missed.

Thanks. Maybe I will get some other posts.

---

### Post by Morbius1 on 2011-04-12
Maybe it's just me. Maybe it's too late in the day but this is a very confusing post.

**First**, that can't possibly be your entire smb.conf because despite this post:
> I am able to use the RUN command in windows and see the shares
\\infratechserver1You have nothing to see since you have no shares defined - not one. There should be a share definition header somewhere like [share-name] to let samba know that what follows is a share definition. But you have no such thing.
[B]
Second[/B], even if you had shares defined your machine is invisible on the network since your netbios name is too long:
>  netbios name = [COLOR=Blue]infratechserver1[/COLOR]Drop one character so that it's **[COLOR=Blue]15 characters or less[/COLOR]** and you may have a chance.

**Third**, by default Samba uses broadcast to announce it's presence on the network but it doesn't work across different subnets like what you have set up:
> The windows box is on a [COLOR=Blue]192.x.x.x[/COLOR] network and the samba/ubuntu server is the external network [COLOR=Blue]98.x.x.x[/COLOR] network.**Forth**, it appears you tried to get around that problem by setting your server up as a WINS server:
> wins support = yesBut that means your server has to have a static ip address and all of your other machines have to be set up to point to that server to register their names.

All in all I'm just plain confused.

You might consider posting the output of the following commands so that others can see more detail:
```
net usershare info --long
testparm -s
```

---

