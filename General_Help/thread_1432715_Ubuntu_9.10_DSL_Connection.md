---
title: "Ubuntu 9.10 DSL Connection"
date: 2010-03-18
forum: General Help
---

### Post by sp3kter on 2010-03-18
Hello folks,

I've very recenty installed Ubuntu v 9.10(64amd) but am unable to setup my internet connection.I've gone through quite a few posts where other users have faced the same trouble trying to setup a DSL connection.


I've entered all my Ip4 settings as they are on Win..but that hasn't helped.

Opened up Firefox too and tried to open...[http://192.168.1.1]("http://192.168.1.1/").

That didn't open my modem settings page either.

Modem model : SmartAX MT882 connected via Ethernet and not USB.

Can't quite figure out what I'm doing wrong/need to do.


Being relatively new to this OS,I'd be grateful if someone could please  simplify things for me a bit..(have no clue about coding/terminal  windows,etc yet.)


Thanks in advance,
Spekter

---

### Post by bobcollard on 2010-03-18
Simplify it.  You don't need a Mac address, in IP4 settings you may only need the Automatic DHCP settings.  Sounds like you are hardwiring it so that should be even easier.  Most of the time you just plug it in and it is recognized when you install Ubuntu.  Instead of 192.168.1.1 try 192.168.0.1

---

### Post by DawieS on 2010-03-18
If you are going to do port forwarding (perhaps for using DC++ or Transmission Bittorrent), some modems require that you have a fixed internal IP address on your LAN. Please visit **[http://portforward.com](http://portforward.com)** to see how to do port forwarding on your specific router/modem.

To set a fixed IP address on your PC, right-click on the network icon (top right-hand side). (Ensure networking is enabled) Select **Edit Connections**, then **Wired**, and select **eth0** (or whatever name you may have used), then **Edit**. Enable **Connect Automatically** (to connect each time at boot). At **IPv4 Settings**, at **Method** select **Manual** and enter the fixed IP address you have chosen and used when setting up your router/modem, in the **Address** column, then **255.255.255.0** in the **Netmask** column, and 192.168.1.1 (or whatever address your router/modem has) in the **Gateway** column.

If you cannot remember the fixed IP you gave your PC, at **Method** select **Automatic(DHCP)**, and log into your router/modem with your Internet Browser. Read the IP from the settings of the router/modem, and adjust your PC network settings accordingly.

If you are not going to do port forwarding, at **Method** select **Automatic(DHCP)**.

At **IPv6 Settings**, in both cases at **Method** select **Ignore**.
:grin:

---

### Post by sp3kter on 2010-03-18
Thanks a ton bobcollard and DawieS for your replies.

I use an internet connection which requires a Username and Password...should I be setting it up under 'Wired' or 'DSL?'

(I was unable to locate an option to enter username/password under the wired connection tab.)

I followed the exact steps outlined and setup a connection under the 'wired' tab.
Instantly,a message popped up in the top right corner saying that I was connected to 'Wired 1.'
This obviously wasn't an internet connection...seemed like fixing my lan card settings as on Windows.

Next I setup a DSL connection with the following settings....

[IMG]http://i.imagehost.org/0175/ip1.jpg[/IMG]


For some reason it still doesn't seem to want to work!

So at the moment confused about whether I need to set it up as a WIRED or DSL connection..or have both on together?!

In case it is to be a DSL setup,would be great if someone detailed out the instructions like DawieS.

Thanks again!

---

### Post by DawieS on 2010-03-18
If your modem/router supports it, the login username, password and preferred DNS to your ISP should be entered into the modem/router by login into it with your Internet Browser, and filling in one of the pages provided by the modem/router. In such a case, the modem/router will act as DHCP server, and all PC's connected to the LAN with the **Wired** connection will have access to the Internet. Usually these modems/routers also have a built-in firewall, whereby all traffic not initiated from the LAN side, is ignored.

If you have an older type modem that does not support these functions, the modem merely acts as an interface between your PC and your ISP by using the DSL protocol on the phone line. In such a case, at **Network Connections** click on the **DSL** tab, enable **Connect Automatically** (to connect each time at boot) then **Add**. Now fill in your Username and Password on the page provided. At **Service** fill in PPPoE LLC (or whatever was provided by your ISP). Click on the **IPv4 Settings** tab, at **Method** select **Manual** and fill in the IP information provided by your ISP. Enable **Available to all users** if you want to share your Internet connection with others PC's on the LAN. In such a case, your PC will act as the DHCP server on the LAN.
:grin:

---

### Post by sp3kter on 2010-03-19
Hey DawieS,

Thanks once again for your reply.Sorry to be bothering again,but still can't get it to work. :(

Below are a few screenshots for your convenience.

[IMG]http://d.imagehost.org/0938/1_13.jpg[/IMG]




[IMG]http://e.imagehost.org/0806/2_4.jpg[/IMG]


Screenshot 1 : Composite shot of settings entered.

Screenshot 2 : A tiny window that pops up soon after I setup the connection...disappears instantly,even before I can type out the entire password and a notification appears in the top right corner saying I've been disconnected from 'Wired 1.'

Not only am I still not being able to connect,what is strange is

a) 'Wired 1' was the Wired Connection I had created earlier(it no longer exists)

and

b) post deleting the 'Wired 1' connection that I had been instructed to setup earlier,I am not being able to login to my Modem settings page ([http://192.168.1.1](http://192.168.1.1) )

Could there possibly be some sort of driver/or other failure in Ubuntu communicating with the modem?

I face no problems on Win.


Thank you yet again..hope this helps you to identify what exactly is going wrong.

---

### Post by DawieS on 2010-03-19
I have done a quick search, it seems as if that modem does not support automatic IP addressing. PC's on the LAN must have static addresses of 192.168.1.10;11;12; etc.

Create a wired connection as before, by adding it under the **Wired** tab (or edit an existing wired connection). Enable **Connect Automatically**. At **IPv4 Settings**, at **Method** select **Manual**. Enter 192.168.1.10 in the **Address** column, then 255.255.255.0 in the **Netmask** column, and 192.168.1.1 in the **Gateway** column. At **IPv6 Settings**, at **Method** select **Ignore**. Close and wait for the connection to become active. If it does not, first delete the **DSL** connection, and retry.

Once the wired connection is established, right-click on the network icon, and select Connection Information. Copy the **Hardware Address** and paste into a text file (something like 00:0E:E8:EB:B7:20). Close and again right-click on the icon and select **Edit Connections**. Select **DSL**, then **Add** (or** Edit** if one already exists). At** DSL** fill in your login details, at **Wired** paste the **Hardware Address** from the text file into **MAC address**, leave **MTU** automatic. At **IPv4 Settings**, at **Method** select **Manual**, then fill in 192.168.1.10 at **Address**, 255.255.255.0 at **Netmask**, 192.168.1.1 at **Gateway**. Fill in 61.1.96.69;61.1.96.71 (or whatever addresses was provided by your ISP) at **DNS** servers. Click Apply.

You can also fill in your login details into a modem page (Log in to the modem with a Internet Browser). Check if you can connect to the Internet. If not, at **PPP settings**, at **Configure Methods** try disabling some of the **Authenticating Methods** and retry. You can visit your ISP's website or contact them for all supported authenticating methods. You can also download a manual for that modem. (Google **SmartAX MT882 modem**)

---

### Post by sp3kter on 2010-03-20
Hey DawieS...thanks again!

Tried everything..still doesn't want to work for me.

Giving up.Thanks to all of you once again for your time and inputs. :)

---

### Post by sp3kter on 2010-04-03
Hey guys,

Thought of letting you know that I reverted to version 9.04 and managed to have the connection set up and working in a matter of minutes! :)

Sp3k!

---

