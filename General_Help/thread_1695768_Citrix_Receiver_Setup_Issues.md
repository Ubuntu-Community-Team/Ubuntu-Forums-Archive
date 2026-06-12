---
title: "Citrix Receiver Setup Issues"
date: 2011-02-26
forum: General Help
---

### Post by gschoper on 2011-02-26
I have Citrix XenServer 5.6.0 up and running on an HP DL360 with no issues for ~8 remote users running Windows. The ICA client works great under Windows with multimedia and video for XenDesktop and runs under Ubuntu 10.10 using the Java client which supplies HD video but no sound.

I've installed the Linux Citrix Receiver client on 10.10 but am having troubles connecting to my dedicated desktop. I believe the issue is with my client config and what specific addresses go where under Network Properties. Please see screenshot. Any Help would be appreciated.

TIA,

g

---

### Post by Reeman on 2011-03-25
The network settings should be to default and the rest of the fields will  be blank. The client on the linux machine will then just find other nodes  and the server on your local network.

You only need to use these fields if you are not on your local net and need to find your server. In which case you will need to use an external service that will always update your dhcp address if you do not have a static address. 

If you do have a static address provided by your isp then these are what goes in the fields. Then the Ubuntu clients will be able to access your local server from anywhere including starbucks or where ever there is internet access. Essentially then the Ubuntu clients will then be asked to log in and to provide credentials that you set for users in the Citrix Server on the Windows server machine.

It is not the same as Go-To-My-PC and the like, it is a true server client or ICA system. If you are using their go to my pc then most likely the linux clients are crippled in some fashion. Go to my pc works with WMP to serve streaming files and will stream to Linux if you install the dreaded codecs on Ubuntu. However streaming media from Windows is a moving target because of Silverlight. 

See the attachment for how to enable sharing and remote desktop on Ubuntu. It is under the System/Preferences/Remote Desktop, if file and access sharing is not created on each of the local Ubuntu users then other access servers and node requests will not be accepted. 

Be careful though as I actually had someone from Brazil try to run my Linux desktop...but fortunately I had it set up to ask first and if not then reject...and I am using DHCP behind a NAT firewall Linksys wireless N router set for strong encryption locally! You can always have your machine seen on the net if you do not shut it down and re-aquire a different dhcp address fairly frequently and if you open up firewall ports for media access as well as remote desktop access. 

Allowing remote desktop access for media is always a security risk whereas local network access is easy to secure. You just only allow local access and remote non local requests then will be rejected by the local server and even the local users desktops if things are set up correctly. And if you have not made your server available over the internet...just a local net setup like mine.

See the attached png of my network discovered by Upnp-Inspector you will see our television set, the computer that is a windows vista machine but shows up as two different devices ( one of which is the computer itself the other is WMP ) and the router. As you can see there is no node for the linux computer that I am using right now as I have it set to discover but be hidden. If I launch my Media DLNA server then it will show up but the computer itself is hidden. 

The second UPNP-inspector screen shot is with my linux installed PS3 media server working as you can see all devices are discovered on the local network and have no remote connections. I can transfer and stream media to and from windows and linux or to my TV all at the same time. 

If someone else joins my network and they have DLNA or file sharing enabled then they can do the same if I allow it. However if someone tries to remotely access this setup then their requests will be reject and logged. My passwords for remote access are long and strong and change if I log too many hack in requests.

..................................................................... 

In my case I am having a shiet load of trouble installing the linux .deb citrix receiver on my intel 64 bit atom...I get a wrong architecture error and I do not know why...did you install the new version 11 citrix receiver on 64 bit Ubuntu without trouble? 

If so I would sure like to know how as it is necessary for my wifes work and I really want to dump my Vista machine and get Windows the hxxx out of my life for a change!

PM me if you like.

Hope this helps 

Eric

---

### Post by gschoper on 2011-03-26
Leaving the fields set to default (Blank) was the correct answer. The problem actually was that Firefox was not calling the Citrix client when connecting to the Xen server. It was using the native Java client. After a browser upgrade to Firefox 4 all is working well with the exception of streaming audio. High Def video works fine via HDX though so it must be a local config issue. I'll have to play around with it as it works fine when I'm connected via my phone using the Android Citrix receiver.

Thanks for your help.

---

