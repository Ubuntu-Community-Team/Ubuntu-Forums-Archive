---
title: "smb.conf"
date: 2010-10-13
forum: General Help
---

### Post by s_g_robertson on 2010-10-13
Hi,

I have found that I need to change the default smb.conf file to allow me to browse my home network using Nautilus.  The only change I need to make is to change the name resolve order line to

```
 name resolve order = lmhosts bcast hosts wins
```

from the default 

```
lmhosts hosts wins bcast
```

without that change then I get as far as the WORKGROUP folder but can't get any further.

I have not intentionally set up anything complicated on the other machines on the network so i am surprised that I need to change from the default.  Any suggestions on why this change is necessary.  Is there a chance that it is because I have something setup incorrectly elsewhere on the network.

Thanks
Stephen

my /etc/hosts file, which I have never manually modified is

```
192.168.1.101	stephen-laptop	# Added by NetworkManager
127.0.0.1	localhost.localdomain	localhost
::1	stephen-laptop	localhost6.localdomain6	localhost6
127.0.1.1	stephen-laptop

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

---

### Post by mikewhatever on 2010-10-13
Computers are like that. Sometimes the default setting doesn't work and needs tweaking. A samba guru may be able to tell you why, but if you really want to know and understand the answer, well, study samba.
[http://www.samba.org/samba/docs/](http://www.samba.org/samba/docs/)

---

### Post by luvshines on 2010-10-13
Did you setup Samba by modifying smb.conf or but right_click+share ??

---

### Post by s_g_robertson on 2010-10-13
> **luvshines said:**
> Did you setup Samba by modifying smb.conf or but right_click+share ??

I tried to do it using right_click+share.  Though it was previously set up manually(quite a few ubuntu versions ago) though I cleared out the configuration files and reinstalled samba.

I am trying these days to do everything the simplest way possible and not dive into configuration files or workarounds unless I have to.

---

### Post by Hakunka-Matata on 2010-10-13
Wow, if you've been cruising along with no problems getting into "WORKGROUP" and having everything display OK, count yourself lucky.  You're showing version 9.04 as your current release, if that's correct, then that may be the reason.  

I've had massive problems since about 3 releases ago, I'm now on 10.04 and have wrestled with Samba and local network browsing continually.  Lots, HEAPS of posts have been made about Samba, CIFS, and the local network file browsing issue, defaults have been changed over releases and other changes too.  

Now the really curious thing is that all of a sudden, today, WORKGROUP is working, it hasn't been working, so maybe an update fixed it, I've been using "Connect to server" instead.  

I hope you have no more problems,

---

### Post by luvshines on 2010-10-13
What does these say:
```
net usershare info

smbclient -L <server-ip> -U<user-name>%<user-passwd>
```

If it's guest share, don't give -U<un>%<up>, just press ENTER twice

---

### Post by s_g_robertson on 2010-10-13
> **mikewhatever said:**
> Computers are like that. Sometimes the default setting doesn't work and needs tweaking. A samba guru may be able to tell you why, but if you really want to know and understand the answer, well, study samba.
[http://www.samba.org/samba/docs/](http://www.samba.org/samba/docs/)

I know they are like that but in this case I think the default should "Just Work" for a simple setup like mine.  So I would like to figure out whether there is a configuration issue elsewhere in my setup in which case it is my fault or if not then I would think this would be a bug/enhancement/feature request that this works out of the box.

---

### Post by s_g_robertson on 2010-10-13
> **luvshines said:**
> What does these say:
```
net usershare info

smbclient -L <server-ip> -U<user-name>%<user-passwd>
```

If it's guest share, don't give -U<un>%<up>, just press ENTER twice

```

[photos]
path=/media/disk/Photos
comment=
usershare_acl=Everyone:F,
guest_ok=n

```

The smbclient output is after I have modified smb.conf from the default.  If I change it back to the default it seems to keep working until I reboot the client machine.  I'll do that now and post the output when browsing with nautilus is not working

EDIT: The output is the same in both circumstances.

```
stephen@stephen-laptop:~$ smbclient -L 192.168.1.100
Enter stephen's password: 
Anonymous login successful
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.4.7]

	Sharename       Type      Comment
	---------       ----      -------
	print$          Disk      Printer Drivers
	IPC$            IPC       IPC Service (bressay server (Samba, Ubuntu))
	photos          Disk      
Anonymous login successful
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.4.7]

	Server               Comment
	---------            -------
	BEDROOM              bedroom server (Samba, Ubuntu)
	BRESSAY              bressay server (Samba, Ubuntu)
	SHEILA-PC            
	STEPHEN-LAPTOP       stephen-laptop server (Samba, Ubuntu)
	STEPHEN-PC           

	Workgroup            Master
	---------            -------
	WORKGROUP            BRESSAY

```


Thanks for your help and interest.
Stephen

---

### Post by luvshines on 2010-10-13
Ok !!

Can you access it with smbclient command:
```
smbclient //192.168.1.100/photos 
```

Looks like you haven't tick-marked 'allow guest' option while share
```
[photos]
path=/media/disk/Photos
comment=
usershare_acl=Everyone:F,
[COLOR="Blue"]guest_ok=n[/COLOR]
```

---

### Post by s_g_robertson on 2010-10-13
> **s_g_robertson said:**
> ```

[photos]
path=/media/disk/Photos
comment=
usershare_acl=Everyone:F,
guest_ok=n

```

The smbclient output is after I have modified smb.conf from the default.  If I change it back to the default it seems to keep working until I reboot the client machine.  I'll do that now and post the output when browsing with nautilus is not working

EDIT: The output is the same in both circumstances.

```
stephen@stephen-laptop:~$ smbclient -L 192.168.1.100
Enter stephen's password: 
Anonymous login successful
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.4.7]

	Sharename       Type      Comment
	---------       ----      -------
	print$          Disk      Printer Drivers
	IPC$            IPC       IPC Service (bressay server (Samba, Ubuntu))
	photos          Disk      
Anonymous login successful
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.4.7]

	Server               Comment
	---------            -------
	BEDROOM              bedroom server (Samba, Ubuntu)
	BRESSAY              bressay server (Samba, Ubuntu)
	SHEILA-PC            
	STEPHEN-LAPTOP       stephen-laptop server (Samba, Ubuntu)
	STEPHEN-PC           

	Workgroup            Master
	---------            -------
	WORKGROUP            BRESSAY

```


Thanks for your help and interest.
Stephen

I should clarify that the STEPHEN-LAPTOP is the client that I am working from and it is the photos share on BRESSAY that I am trying to connect to.  In Nautilus with the default "resolve order" I can't get as far as seeing any of the "servers".

---

### Post by s_g_robertson on 2010-10-13
> **luvshines said:**
> Ok !!

Can you access it with smbclient command:
```
smbclient //192.168.1.100/photos 
```

Looks like you haven't tick-marked 'allow guest' option while share
```
[photos]
path=/media/disk/Photos
comment=
usershare_acl=Everyone:F,
[COLOR="Blue"]guest_ok=n[/COLOR]
```

I can access it using smbclient and the ip address if I give it the correct password.

But it doesn't work with

```
smbclient //bressay/photos
```

I get

```
Connection to bressay failed (Error NT_STATUS_UNSUCCESSFUL)

```
Thanks
Stephen

---

### Post by luvshines on 2010-10-13
So from command line, you can access with IP but not through the name.

Check if nmbd service is running at the server side
```
sudo service nmbd status

If not running,
sudo service nmbd start
```

I also added this to my smb.conf on the server side for name resolutions, see if this helps (you will need to restart smbd process if you change smb.conf file)
```
wins support = yes
dns proxy = yes
name resolve order = wins host lmhosts bcast
```

PS: Will see the further developments on this thread in morning, OMG, it's already 3AM in India :)

---

### Post by luvshines on 2010-10-14
Just curious to know, did it work ?

---

### Post by Morbius1 on 2010-10-14
Samba itself I can usually muddle through to get it to work but I'll admit that on the networking part of this issue my knowledge is embarrassingly shallow.

The way I understand the issue with name resolve order is this way. The default is this:
>  name resolve order = lmhosts hosts wins bcastlmhosts and hosts are basically lookup tables that require that all machines on the network have static ip address and is not set up by default so samba ignores them.

"wins" requires that somewhere in the network there exists a wins server. If you have one then a modification has to be done to every client on your network to point to that wins server ( and the wins server must have a static ip address ). By default that also is not configured.

The only option that is operational by default is bcast ( broadcast ). I have noticed ( purely anecdotally I should add ) that with the default priority it gets hung up on "wins" ( worse if you have wireless ) as if it is searching relentlessly for a wins server that doesn't exist.

Although it doesn't work every time, I have recommended that people do exactly what you have done and set bcast if not at the beginning at least before "wins" with successful results.

If you have nothing else to do set the name resolve order back to the default and run the following command:
```
smbtree -d3 > smbtree.txt
```Or even
```
smbtree -d4 > smbtree.txt
``` I can only understand about 20% of the output :) but you will see it tick through the resolve order, note that a given option has failed, move to the next one, and maybe stall. Perhaps on yours it stalls at wins and never gets to bcast.

*BTW the output of smbtree with the d3 or d4 option is enormous so that's why I suggest to send it to a text file.*

---

### Post by s_g_robertson on 2010-10-15
> **Morbius1 said:**
> Samba itself I can usually muddle through to get it to work but I'll admit that on the networking part of this issue my knowledge is embarrassingly shallow.

The way I understand the issue with name resolve order is this way. The default is this:
lmhosts and hosts are basically lookup tables that require that all machines on the network have static ip address and is not set up by default so samba ignores them.

"wins" requires that somewhere in the network there exists a wins server. If you have one then a modification has to be done to every client on your network to point to that wins server ( and the wins server must have a static ip address ). By default that also is not configured.

The only option that is operational by default is bcast ( broadcast ). I have noticed ( purely anecdotally I should add ) that with the default priority it gets hung up on "wins" ( worse if you have wireless ) as if it is searching relentlessly for a wins server that doesn't exist.

Although it doesn't work every time, I have recommended that people do exactly what you have done and set bcast if not at the beginning at least before "wins" with successful results.

If you have nothing else to do set the name resolve order back to the default and run the following command:
```
smbtree -d3 > smbtree.txt
```Or even
```
smbtree -d4 > smbtree.txt
``` I can only understand about 20% of the output :) but you will see it tick through the resolve order, note that a given option has failed, move to the next one, and maybe stall. Perhaps on yours it stalls at wins and never gets to bcast.

*BTW the output of smbtree with the d3 or d4 option is enormous so that's why I suggest to send it to a text file.*

This certainly looks (again anecdotally) like the same situation I am seeing.  Including the fact that accessing share A from machine B(wireless) causes problems but from machine C(wired) seems to work with the default settings.

I'll try the debug outputs over the weekend when I get a chance

Thanks everyone.

---

### Post by luvshines on 2010-10-15
> **Morbius1 said:**
> 
The way I understand the issue with name resolve order is this way. The default is this:
"wins" requires that somewhere in the network there exists a wins server. If you have one then a modification has to be done to every client on your network to point to that wins server ( and the wins server must have a static ip address ). By default that also is not configured.

I have noticed ( purely anecdotally I should add ) that with the default priority it gets hung up on "wins" ( worse if you have wireless ) as if it is searching relentlessly for a wins server that doesn't exist.



From what I read here:
[http://oreilly.com/catalog/samba/chapter/book/ch07_03.html](http://oreilly.com/catalog/samba/chapter/book/ch07_03.html)

With 'wins support = yes' Samba can itself work as wins server (using NMBD). That is why I suggested:
```
wins support = yes
name resolve order = wins host lmhosts bcast
dns proxy = yes
```

Don't know for sure though, but it seems to be working for me.
At my home network and even at my office, although my machine is not reachable by my FQDN(hostname.<domain>), but atleast is very much pingable with my Samba's netbios name. And since I don't have a DNS for the local IP's at home network, I feel that it is working

---

### Post by Morbius1 on 2010-10-15
```
With 'wins support = yes' Samba can itself work as wins server (using NMBD).
```Yes, adding  "wins support = yes" to the smb.conf of a given box will turn that box into a WINS server. 

That means that every other Linux box in the network must have the following line in their smb.conf pointing to that WINS server for name resolution:
```
wins server = ip-address-of-wins-server
```It also means the every Windows box will have to alter their networking component in the "WINS" tab to point to the ip address of the WINS server.

And although I have no idea how one goes about actually doing this, every Mac will also need modification to point to that WINS server. 

It's a workable system but by definition I wouldn't really call it a peer-to-peer network as the WINS server must always be turned on for everything to work.

---

### Post by Hakunka-Matata on 2010-10-17
> **Morbius1 said:**
> ```
With 'wins support = yes' Samba can itself work as wins server (using NMBD).
```Yes, adding  "wins support = yes" to the smb.conf of a given box will turn that box into a WINS server. 

That means that every other Linux box in the network must have the following line in their smb.conf pointing to that WINS server for name resolution:
```
wins server = ip-address-of-wins-server
```It also means the every Windows box will have to alter their networking component in the "WINS" tab to point to the ip address of the WINS server.

And although I have no idea how one goes about actually doing this, every Mac will also need modification to point to that WINS server. 

It's a workable system but by definition I wouldn't really call it a peer-to-peer network as the WINS server must always be turned on for everything to work.

And the wins server box must also have a static ip-address assigned, is that also true?, think I read that on one of these samba threads.

---

### Post by Hakunka-Matata on 2010-10-17
I realise if the wins-server box got it's ip-address via DHCP, that could be a problem, but does the static ip-address requirement go beyond that, for other reasons not yet clear?

---

### Post by Morbius1 on 2010-10-17
The wins server box has to have a static ip address but the other boxes do not. They just have to have their networking components point to the WINS server.

---

