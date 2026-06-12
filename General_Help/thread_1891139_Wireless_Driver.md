---
title: "Wireless Driver?"
date: 2011-12-05
forum: General Help
---

### Post by Keith789 on 2011-12-05
Well I have no clue about Ubuntu/Linux. I have always used Windows and some of my friends told me to try out Ubuntu. 

I installed Ubuntu on my Windows 7 using Wubi.

Now I'm stuck on connecting to the internet, I try to install the driver but it says it fails to do so? Is there any way to enable the wireless driver without connecting an Ethernet cable? 

Or is there any version of Ubuntu that comes with a pre-installed wireless driver, I'm confused. 

Well hope this should be enough of some sort of information, please post a reply.

---

### Post by idoitprone on 2011-12-05
> **Keith789 said:**
> Well I have no clue about Ubuntu/Linux. I have always used Windows and some of my friends told me to try out Ubuntu. 

I installed Ubuntu on my Windows 7 using Wubi.

Now I'm stuck on connecting to the internet, I try to install the driver but it says it fails to do so? Is there any way to enable the wireless driver without connecting an Ethernet cable? 

Or is there any version of Ubuntu that comes with a pre-installed wireless driver, I'm confused. 

Well hope this should be enough of some sort of information, please post a reply.

Well there is alot of reason why wireless does not work on linux and in most cases it is because the company refuses to support linux or give a binary blob and tell the user to find the driver. All default linux distros ship wireless drivers as they are part of the linux kernel.

You have to post your wireless card

```
lspci -v
```

---

### Post by Keith789 on 2011-12-05
> **idoitprone said:**
> Well there is alot of reason why wireless does not work on linux and in most cases it is because the company refuses to support linux or give a binary blob and tell the user to find the driver. All default linux distros ship wireless drivers as they are part of the linux kernel.

You have to post your wireless card

```
lspci -v
```

I have the wireless card called,


'Dell Wireless 1397 WLAN Mini-Card'

Thanks for the help.

---

### Post by oldtimer7777 on 2011-12-05
> **Keith789 said:**
> I have the wireless card called,


'Dell Wireless 1397 WLAN Mini-Card'

Thanks for the help.

Try using Ndiswrapper:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by idoitprone on 2011-12-10
> **Keith789 said:**
> I have the wireless card called,


'Dell Wireless 1397 WLAN Mini-Card'

Thanks for the help.
 

ummm that info is not that helpful, since i am dont wanna google search that rebranded chip. Wireless chipset are like graphic cards they get rebranded although the main component probably all comes from the same company. It kidda like comparing msi n580gtx or rvga 580gtx. It might cost different. Sure...but it is still the same stupid nvidia geforce 580gtx with only a different vendor. I made that example randomly.

You get the point?

Since your on the forums with wireless issues, then it probably broadcom wireless chip

there links should help
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
[http://ubuntuforums.org/showthread.php?t=25683](http://ubuntuforums.org/showthread.php?t=25683)

---

