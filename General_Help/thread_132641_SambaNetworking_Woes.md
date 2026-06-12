---
title: "Samba/Networking Woes"
date: 2006-02-18
forum: General Help
---

### Post by Bruce_C on 2006-02-18
I'm trying to set up samba for my laptop, but can not seem to get things working.

Here's what my smb.conf file looks like:
```

[global]
workgroup = HOME
netbios name = Carbon
encrypt passwords = yes
wins support = yes
security = share

[root]
public = yes
path = /
browseable = yes
available = yes
writable = yes

```

I can see the computer from a Windows computer, but receive and error when I double click on the icon.  This is the error:
```

\\Carbon is not accessible.  
You might not have permission to use this network resource.  
Contact the adminstraor of this server to find out if you have access permissions.  
The network path was not found.

```
I can ping the laptop, but I can't ssh into it.



I have another linux box with which, again, I can  ping, but not ssh into.  I also tried nmap and recieved:
```

Starting nmap 3.81 ( http://www.insecure.org/nmap/ ) at 2006-02-18 14:22 PST
All 1663 scaned ports on 192.168.1.200 are: filtered
MAC Address:  **Correct MAC Address**

Nmap finished: IP address ( 1 host up ) scanned in 35.640 seconds

```

I'm thinking this is more of a network problem than anything else.  Maybe it's the router (linksys wrt54g).  I've had unresolvable nat issues with this router.  Port forwarding doesn't help any.

Any input would be greatly appreciated.

---

### Post by wjp.reg on 2006-02-19
> I can see the computer from a Windows computer, but receive and error when I double click on the icon. 

In order for a SAMBA user to access shares it needs to know their username and password.

Did you setup the SAMBA username and password as in:

```
sudo smbpasswd -a [user]
```

using terminal mode?  I ask because this is a common omission ;)  and should get you access to the linux share from windows.

---

### Post by Bruce_C on 2006-02-19
Yes, I've executed:
```
sudo smbpassword -a `whoami`
```

When I double click the computer icon from a Windows machine I get an error, which doesn't allow me to log in.  I never reach the point of being prompt for my user name and password.

One more thing,  I can't view other computers on my network from my laptop when browsing through Network Servers->Windows Network.

---

### Post by wjp.reg on 2006-02-19
[QUOTE=Bruce_C]Yes, I've executed:
```
sudo smbpassword -a `whoami`
```

When I double click the computer icon from a Windows machine I get an error, which doesn't allow me to log in.  I never reach the point of being prompt for my user name and password.

One more thing,  I can't view other computers on my network from my laptop when browsing through Network Servers->Windows Network.[/QUOTE]

Curious if the above is a typo, or did you really issue a > smbpassword -a `whoami`, 'cause it's not "password"..

Do any of the linux shares show up in Windows Network Neighbourhood ?

Sorry if this seems like a stupid question, but did you set up any linux shares ?

If you don't, you will get the behaviour you describe (clicking on a linux computer icon and getting an error).

have you tried the network tools and pinging the other machines ?

---

### Post by Bruce_C on 2006-02-20
It's a typo.  I meant smbpasswd.  I'm not sure what you mean by linux shares.  Can you elaborate?  An example perhaps?

I have no problems pinging other computers.

---

### Post by wjp.reg on 2006-02-20
[QUOTE=Bruce_C]It's a typo.  I meant smbpasswd.  I'm not sure what you mean by linux shares.  Can you elaborate?  An example perhaps?

I have no problems pinging other computers.[/QUOTE]

Maybe I can help by just walking through the steps I take to set up SMB networking.

1) I check **System | Administration | Networking** to make sure my connection is using the correct Host Settings under the **General** tab (domain/workgroup in particular).
2) Next I go into **System | Administration | Shared Folders** to add my home folder as an SMB share.  Make sure to name it and set the other parameters as required (readonly / browsable).  If Samba server component is not already installed (which it isn't after a fresh intall), you will be prompted and offered a chance to do so right then and there.
3) The last thing I do is to go into **System | Administration | Printing** to setup my WIndows SMB printer, using the IP address of that system, which seems more reliable than trying to use the windows host name.  This assumes you already have a windows printer installed and have set it to be shared and that you know the share name and user/password combo to use it.
4) bring up the terminal and issue the **sudo smbpasswd -a [user]** command to give the windows user permission to access my linux shares.  I don't use anything fancy like passing the `whoami` parameter, I prefer to use the literal name, like "wolf" - which is me.

This is what I have done to set up my SAMBA network without fail; no fiddling with smb.conf, which of course you can do instead if you wish ;)

P.S. You should see your linux shares in Network Neighbourhood if the above works and this is the preferred way to access your linux shares from windows.

---

### Post by gibson on 2006-02-20
Looking at the way you are making your file, it appears you want your shares to be public, i.e. no password to use them?

you also need to let the specified hosts through, eg my network is 192.168.1.1/24 so i use the line

> allow hosts = 192.168.1. 127.0.0.1

in my sbm.conf.

Then change the security levels

> security = share

and finally, the good old restart

> sudo /etc/init.d/samba restart

hope this helps

EDIT: 
just for now, try accessing shares from ip... .this will ensure sambas is working and hostname problems are something else

---

### Post by mr.p on 2006-02-21
how do i make one share public? i have shared a folder and it has user access but i want to make it public and other stuff private with user/password

---

### Post by Bruce_C on 2006-02-21
I tried what you guys recommended and I'm still getting the same error.  I think it's my router.  I'll play around with it when I get home later tonighter.  

Thanks for your input.  :D

---

### Post by jones_jj on 2006-02-21
First thing you have to do is to allow tcp ports135-139 to pass through your firewall.  These are the network neighborhood/samba ports.  As soon as you allow those ports to pass through, you should be able to map network drives, or see the shares through network neighborhood.  I would reboot your windows laptop just b/c it's windows and a good reboot after allowing the ports should clear things up.

---

### Post by Bruce_C on 2006-02-21
I turned off the firewall and the error message is still there.

---

### Post by bosonflux on 2006-02-24
bruce_c. I had similar problems. I was able to fix them all by following the Samba diagnosis procedure that is loaded with your distro. It is located at /usr/share/doc/samba/diagnosis.html. There are 11 tests of which I failed over half at first. My main problems were /etc/hosts did not have my computer name entry, 192.168.xxx.xxx    computer name. I also put one for the windows box. I had to stop firestarter for trouble shooting  and be sure to allow tcp, udp, and icmp from the windows box if it also has a firewall. I found this all to work better if you use a static address as well.

---

### Post by Bruce_C on 2006-03-05
I couldn't find that diagnosis.html, but was able to resolve the problem by removing firestarter.

Thanks for all the help.  \\:D/

---

