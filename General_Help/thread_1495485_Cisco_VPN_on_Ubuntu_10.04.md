---
title: "Cisco VPN on Ubuntu 10.04"
date: 2010-05-28
forum: General Help
---

### Post by hnarwan on 2010-05-28
Hi All,

I needed to be able to VPN into my work network and access my windows machines (both my xp desktop and VM ESX hosts running Windows 2003/Windows 2008).

I ran the following to allow my Cisco VPN .pcf to be imported:

sudo apt-get install network-manager-vpnc

After this I went into VPN Connections, chose the 'Cisco Compatible VPN (vpnc)' option and then imported my profile.

That works fine, and i'm able to connect. The problems i'm having are:

1. When i'm on VPN i cant use my local internet connection.
2. I cant put my computer name into Applications>Internet>Remote Desktop viewer and connect. I cant even see my work network.

What is the process to get this working? I think i'm just not using the RDP program properly although i've entered the computer name and even tried the FQDN.

Any ideas would be much appreciated. This is the last thing I need to get working to forever make the switch.

thanks all

Hardeep

---

### Post by dino99 on 2010-05-28
[https://help.ubuntu.com/community/VPNClient](https://help.ubuntu.com/community/VPNClient)
[https://help.ubuntu.com/community/SSH_VPN](https://help.ubuntu.com/community/SSH_VPN)
[http://forums.bit-tech.net/showthread.php?t=132029](http://forums.bit-tech.net/showthread.php?t=132029)

---

### Post by dcstar on 2010-05-28
> **hnarwan said:**
> 
.........
1. When i'm on VPN i cant use my local internet connection.
.........

That is because the people who you connect to have deliberately set this to happen.

If you install the kvpnc package you can turn this "feature" off.

---

### Post by hnarwan on 2010-05-28
Thanks. I assume kvpnc is for KDE only? I prefer the Gnome desktop environment so if kvpnc  is not an option for Gnome is there any other way I can get my internet connection working when i'm connected via VPN?

I went through the links but i'm still unsure what i'm doing wrong. If I can connect to my VPN without any problems I would have thought it's just a case of providng the machine i'm trying to connect to on my work network and that should be it?

has anyone used this setup? if so once you're on VPN what steps would you take to connect to your windows machines at work?

thanks
Hardeep

---

### Post by Julita on 2010-05-28
> **hnarwan said:**
> Thanks. I assume kvpnc is for KDE only? I prefer the Gnome desktop environment so if kvpnc  is not an option for Gnome

In fact, you can use any apps, whether they are meant for Gnome, KDE or any other DE. When you install kvpnc, the necessary KDE libraries are installed (and loaded) too.

---

### Post by hnarwan on 2010-05-28
Thanks all, I have KVPNC installed but I cant find the option to allow me to use my internet connection.

Also I actually cant get KVPNC to connect to my VPN succesfully although I dont have any problems doing that with the standard vpn client under network connections.

Has anyone got experiance of connecting VPN to a cisco vpn enabled network and the steps you would take to remote into a windows machine on that network?

thanks
Hardeep

---

### Post by hnarwan on 2010-05-29
So just to confirm is there no way to get the standard VPN client configured to allow me to browse the internet while i'm connected?

I cant get the kvpnc program to connect, it complains of a bad user password but the one entered is definitely correct.

Any help on this would be much appreciated, it cant be as hard as i'm making it out right now.

---

### Post by dcstar on 2010-05-29
> **hnarwan said:**
> Thanks all, I have KVPNC installed but I cant find the option to allow me to use my internet connection.
........

It is an option buried deep in the configuration you have imported, I cannot remember what it is called because I last used it years ago.

Do a Google search and you may find its name.

---

### Post by hnarwan on 2010-05-29
Thanks again. I'll have a play around with it and see if i can find it. The main problem at this stage however is the fact that it keeps complaining of a password which I know is correct.

Can anyone tell me how to RDP once i'm on VPN. What is the process? Do you use RDP and just enter the machinename.

---

### Post by hnarwan on 2010-05-29
Ok so i have KVPNC working ok now, i can vpn and still use the internet at the same time.

the problem is i cant remote into any machine (or see them either).

so simply stated what would i need to do to remote desktop to any machine.

---

### Post by hnarwan on 2010-05-30
By the way I've also tried 'Terminal Server Client' to connect once my VPN has successfully connected but I still cant connect to any windows computer inside my work network.

I thought the hard part would have been getting the Cisco VPN client to work but that's been ok. Once i'm connected actually getting a remote session into one of my windows computers is the problem.

I'm sure there's a lot of people out there who have this working on Ubuntu, hopefully one of them can point me in the right direction.

---

### Post by hnarwan on 2010-05-30
Any ideas anyone? I'm really struggling to get this working and it seems like such a common thing others would have hit.

The VPN part which I thought was going to be a problem is fine, I'm able to connect but it's the remote desktop part that i'm having trouble with.

Not sure if you're supposed to use 'Terminal Server Client' or 'Remote Desktop Viewer' but neither of those applications let me remote into my windows machine.

Has anyone managed to access a windows machine over a Cisco VPN connection from Ubuntu? Some basic steps of what i'm supposed to do once i've got my VPN connected would be very much appreciated.

---

### Post by tlroche on 2010-05-31
> **hnarwan said:**
> I have KVPNC installed but I cant find the option to allow me to use my internet connection.

> **hnarwan said:**
> i have KVPNC working ok now, i can vpn and still use the internet at the same time.

Greetings, hnarwan: could you post regarding how to configure kvpnc to allow simultaneous use of the VPN and the local connection? I would very much like to know. (Fortunately I don't need to do a RDC, just VPN to another linux box :-)

TIA, and good luck with RDC, Tom Roche <Tom_Roche@pobox.com>

---

### Post by Numer0bis on 2010-07-17
what you can do to allow simultaneous connection to your lan and to your vpn is to edit your .pcf profile file. Open it with Gedit and look for 
```

EnableLocalLAN=0
```
and turn it into 
```

EnableLocalLAN=1
```

This worked for me.

---

### Post by tlroche on 2010-07-17
> **Numer0bis said:**
> edit your .pcf profile file.

Where is the .pcf? I get

```
$ find $HOME -name '*.pcf' | wc -l
0
```

---

### Post by CapeCodKiter on 2010-07-22
Been following this thread... Last night I got VPNC working with KVPNC for my work cisco VPN. 

I used this link as my guide

[http://www.blog.arun-prabha.com/2009/11/20/how_to_install_kvpnc-in-ubuntu/](http://www.blog.arun-prabha.com/2009/11/20/how_to_install_kvpnc-in-ubuntu/)

Once this was done, I had to make 2 changes to get VPN working for me.

The first was to allow me to connect to my work network and the second was to allow me to use host names instead of IP's on my work network. 

To get VPN working (for me) I had to change the Cisco NAT Mode

-> Manage Profiles
  -> Connection Specific
    -> Cisco
        -> Cisco NAT Mode: cisco-udp

Then to allow for domain names to be resolved:

kvpnc
 - Manage Profiles
  - > Network
    -> Update DNS Configuration (CHECKED)

I hope this helps anyone that finds this thread.

---

### Post by defaria on 2010-08-04
With my client they use the Cisco VPN stuff but then they also use a thing called "SoftToken". They also have a "HardToken" I guess where you carry around this RSA thing that IIRC generates a 6 digit number and when you are prompted you type in your "PIN" portion and then your 6 digit token. 

Seeing as I don't have the HardToken I don't know what to put in when it asks me for a password. Of course my client's admins are lost as soon as I say Linux.

So what do you put in as a password in such a situation? Is it the PIN+Token thing as I described above?

---

### Post by mimeryme on 2010-09-02
I had trouble installing kvpnc, but the last few posts helped lead me to the right option to enable local internet connections to work -- at least for my case.

You'll need to do the following:
1.  Open Network Connections
2.  Click on the VPN tab
3.  Select the profile you are trying to use
4.  Click the Edit button
5.  Click on the IPv4 Settings tab
6.  Select the Routes... button
7.  Check off the "Use this connection only for resources on its network" checkbox
8.  Click OK, then Apply.

I restarted the VPN connection to make sure and now I can connect to the internet locally!

This is with a manually setup VPN profile by the way.  I could not figure out how to import a PCF.

Hope this helps others. :)

---

### Post by tlroche on 2010-09-02
> **mimeryme said:**
> I had trouble installing kvpnc

I did not need to install anything after I upgraded to lucid today: I used the stock NetworkManager Applet for all of the following.

> **mimeryme said:**
> the last few posts helped lead me to the right option to enable local internet connections to work -- at least for my case.

You'll need to do the following:
1.  Open Network Connections
2.  Click on the VPN tab
3.  Select the profile you are trying to use
4.  Click the Edit button
5.  Click on the IPv4 Settings tab
6.  Select the Routes... button
7.  Check off the "Use this connection only for resources on its network" checkbox

I believe it's clearer to say, 'Check the "Use this connection only for resources on its network" box': 'check off' sounds like 'turn off' or 'uncheck'.

> **mimeryme said:**
> 8.  Click OK, then Apply.

I restarted the VPN connection to make sure and now I can connect to the internet locally!

Me too!

> **mimeryme said:**
> Hope this helps others.

Thanks for posting: it helped me.

---

### Post by pyutaros on 2010-09-08
What I don't get is why kvpnc was recommended in the first place.  If you're editing the PCF file itself, it won't matter what client you use it with.  I edited my PCF file and connected using the standard network manager applet.  I can now access my local network, but cannot access routes on my destination network.  I'll post if I can figure out how to do so.

---

### Post by jonathanmotes on 2012-04-28
> **Numer0bis said:**
> what you can do to allow simultaneous connection to your lan and to your vpn is to edit your .pcf profile file. Open it with Gedit and look for 
```

EnableLocalLAN=0
```
and turn it into 
```

EnableLocalLAN=1
```

This worked for me.

This worked for me. Thank you for posting!

---

### Post by oldos2er on 2012-04-28
Old thread closed.

---

