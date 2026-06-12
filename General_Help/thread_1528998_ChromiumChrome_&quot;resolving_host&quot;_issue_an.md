---
title: "Chromium/Chrome &quot;resolving host&quot; issue and WINS"
date: 2010-07-11
forum: General Help
---

### Post by Nixie Pixel on 2010-07-11
Hello, I have been having the dreaded "resolving host" issue in the Google Chrome and Chromium web browsers. After reading the following I suspect I know what the problem is:

[URL="http://code.google.com/p/chromium/issues/detail?id=12754#c106"]http://code.google.com/p/chromium/issues/detail?id=12754#c106
[/URL]

I too put wins in front of dns in my /etc/nsswitch.conf file to be able to resolve problems with Windows shares on my network.

So how can I get the benefit of wins in /etc/nsswitch.conf for connecting to Windows shares, without breaking Chromium?

Any ideas?

Thank you!  ^.^

---

### Post by Nixie Pixel on 2010-07-13
Hello, does anyone have any suggestions for me? :)

---

### Post by sonicb00m on 2010-08-30
I too have run into this exact same problem.

---

### Post by JonOomph on 2010-10-07
I finally figured out how to solve this problem (at least on my computers). 

1) Edit the following file: **/etc/nsswitch.conf**

2) Find the "hosts" line, and change it to this:
   [INDENT]**hosts: files mdns4_minimal [NOTFOUND=return] dns wins mdns4**[/INDENT]


Just as a reference, here is what my "hosts" file looked like before and after:

BEFORE (i.e. always trying to resolve the host)
  [INDENT]**hosts: files _wins_ mdns4_minimal [NOTFOUND=return] dns mdns4**[/INDENT]

AFTER (loads websites super fast!)
  [INDENT]**hosts: files mdns4_minimal [NOTFOUND=return] dns _wins_ mdns4**[/INDENT]

Now you too can bask in the glory of fast lookups and enjoy Chrome again! :P

---

### Post by TBABill on 2010-10-07
Gonna give this a shot. I had this same issues on both Windows and Ubuntu machines (using Chromium or Chrome). I went into my router's configuration and used a proxy DNS (openproxy) and sites load quickly now for all machines on the network. If your fix helps even more then I'll just use both fixes.

---

### Post by TBABill on 2010-10-08
Noticeable improvement! Thank you!

---

### Post by Nixie Pixel on 2010-11-28
Hello, if I put WINS before DNS, chrome has noticeable problems. However, if I put DNS before WINS, as you suggest, while Chrome is faster, I can no longer connect to Windows shares on my network.

Does a solution exist that helps with both?

Thanks!

---

### Post by Vincentlaborant on 2010-11-28
I guess you have tried this:

>    1. In the System menu, click Preferences, then click Network Connections.
   2. Select the connection for which you want to configure Google Public DNS. For
example:
          * To change the settings for an Ethernet connection, select the Wired tab,
then select your network interface in the list. It is usually called eth0.
          * To change the settings for a wireless connection, select the Wireless
tab, then select the appropriate wireless network.
   3. Click Edit, and in the window that appears, select the IPv4 Settings tab.
   4. If the selected method is Automatic (DHCP), open the dropdown and select
Automatic (DHCP) addresses only instead. If the method is set to something else, do
not change it.
   5. In the DNS servers field, enter the Google Public DNS IP addresses, separated
by a space: 8.8.8.8  8.8.4.4
   6. Click Apply to save the change. If you are prompted for a password or
confirmation, type the password or provide confirmation.
   7. Test that your setup is working correctly; see Testing your new settings below.
   8. Repeat the procedure for additional network connections you want to change.

And after that editing resolv.conf because it was not edited by the first operation: 
# Edit /etc/resolv.conf:

sudo vi /etc/resolv.conf

# If any nameserver lines appear, write down the IP addresses for future reference.
# Replace the nameserver lines with, or add, the following lines:

nameserver 8.8.8.8
nameserver 8.8.4.4

# Save and exit.
# Restart any Internet clients you are using.

I will look into it deeper after I have eaten some breakfast since thinking on an empty stomach is not my strongest point.:popcorn:

---

### Post by Wrathfarnham on 2010-11-28
For what its worth, I had the same issue a while back but I actually changed the order of lookups (name resolve order) in my samba.conf file rather than in msswitch.conf.

name resolve order = lmhosts wins bcast host

Just checked my nsswitch file there and no mention of wins in it at all.

---

### Post by oimon on 2010-11-28
An entry for wins may not be necessary since windows shares send netbios broadcasts on the local LAN anyway. 

Alternatively if the windows servers are not on the local LAN and your DNS server doesn't know about them, you could always add the hosts to your /etc/hosts file, which will be read first.

---

### Post by rfdeshon on 2010-11-28
I highly doubt there is a solution to this issue that doesn't involve the Chromium/Chrome developers altering the way the browser works. From the sounds of it, instead of going directly to DNS (or it's own built-in DNS cache) the way Firefox does, Chrome is using the lookup order defined by Linux. Technically speaking, this is the correct behavior for DNS lookups on Linux, but it can lead to exactly the kind of problems you're having.

Now then, there's two ways you can get this to work the way you want. Both involve no longer using WINS. It's a silly ad-hoc and unreliable system anyway. I'd suggest setting your router up to do DNS resolution for local hosts. Most modern routers can do this. Then you just need to make sure your systems are set to use your router for DNS lookups.

If you can't do the above, then add your local hosts to your hosts file as was mentioned previously. (More info on using your hosts file here: [http://www.faqs.org/docs/securing/chap9sec95.html](http://www.faqs.org/docs/securing/chap9sec95.html))

Either way, dump WINS.

---

### Post by capscrew on 2010-11-28
> **oimon said:**
> An entry for wins may not be necessary since windows shares send netbios broadcasts on the local LAN anyway. 

Alternatively if the windows servers are not on the local LAN and your DNS server doesn't know about them, you could always add the hosts to your /etc/hosts file, which will be read first.

I agree netbios name broadcasts is the most effective way for Samba to find netbios names.  The term *wins *has no place in the nsswitch.conf file.  The "hosts" line really is for the gethostbyname() routine.  I have a hunch that the Linux version has no idea what a WINS server is.

By "windows servers" you mean: *those hosts that have shares*, then you will never be able to successfully share the data.  SMB/CIFS/Samba will not traverse routers.  It is strictly a layer 2 (broadcast) protocol for single LAN usage. The rise of VPN and SSH tunnels might make it possible to have multi-locations, but in reality it still works only on one LAN.

Entering names in host files will not resolve netbios names.  But as you say netbios names are broadcast by windows (and Samba if setup).  

You can see the name checking performed by Samba by upping the debug with the commands **smbclient **and **smbtree** like this ```
smbtree -d6
```.

---

### Post by Nixie Pixel on 2010-11-29
The weird thing is, I am not actually using WINS on my network. The network shares in question are a Windows drive being shared and a Drobo NAS shared through a Droboshare box - it's actually running Linux if I recall correctly.

Unfortunately the only way I could get my Ubuntu machines to connect to the shares was to add wins to /etc/nsswitch.conf and install winbind. This was done at the suggestion of someone on this forum when I couldn't connect to the servers any other way. I'm not sure why I couldn't connect without adding wins to my config file...

---

### Post by capscrew on 2010-11-29
> **Nixie Pixel said:**
> The weird thing is, I am not actually using WINS on my network. The network shares in question are a Windows drive being shared and a Drobo NAS shared through a Droboshare box - it's actually running Linux if I recall correctly.

Unfortunately the only way I could get my Ubuntu machines to connect to the shares was to add wins to /etc/nsswitch.conf and install winbind. This was done at the suggestion of someone on this forum when I couldn't connect to the servers any other way. I'm not sure why I couldn't connect without adding wins to my config file...

For sure Winbind has nothing to do with your problems.  The package that one has to install for Winbind does include some routines that *could *aid in netbios name lookup, but there are other more efficient methods to achieve the goals you have.

If you do not have a WINS server in your network then the *wins *entry in your nsswitch.conf file is not the way to go either.

There are many flavors of Samba out there.  My guess is that the drobo units use Samba 2.0.  This does not mean it can't work with a modern Ubuntu smbfs client (SMB/CIFS), but you have to be aware of the limitations that might present themselves.

I would start with fresh smb.conf and nsswitch.conf  files.  This should be easy to do.  Are there any other modifications to the system?

---

### Post by capscrew on 2010-11-29
> **rfdeshon said:**
> ... Either way, dump WINS.

Unfortunately buried deep in the SMB/CIFS protocols is a reliance on NetBIOS names.  WINS is only a mechanism to store and retrieve NetBIOS names. It is worthwhile if you have multiple subnetworks as the NetBIOS broadcasts don't cross routers.

Unfortunately folks tend to confuse WINS with NetBIOS (names).  You don't need the former, but you certainly have to accommodate the latter.

---

### Post by Nixie Pixel on 2010-11-29
I started with a fresh install of Maverick Meerkat. Trying to connect to the share failed. Adding winbind and wins to /etc/nsswitch.conf allowed me to connect to the share.

Any idea why this might be?

---

### Post by mole666 on 2010-11-30
What are you using to connect to the servers?

Samba's config file has its own lookup settings - see 'wins server', 'dns proxy' and 'name resolve order' in /etc/samba/smb.conf.

Try using the commandline 'smbclient -L <name of server>' it should find that server, list its shares and the other servers it knows about. If that fails then give it the server's IP address...

If that works then consider using 'smbmount' - using name or IP - put it in fstab, write a little script to run manually or run it after login using pam_mount.


Once it's working try disabling winbind, you might not need it.

---

### Post by Nixie Pixel on 2010-12-09
I am connecting via Nautilus - both "Connect to Server" and navigating through the network fail unless I have the above installed/enabled. When navigating I can -see- the network share name, but trying to click on it gives me the same error that entering the server as a Windows Share does unless I have wins in nsswitch.conf and winbind installed.

I will test your suggestions soon and report back. Thanks!

---

