---
title: "I'd like to create a Server: what choose: Ubuntu Server or Ubuntu Desktop?"
date: 2012-03-10
forum: General Help
---

### Post by Bruno81 on 2012-03-10
Hi.

I'd like to create a Home Server and use a laptop that momentanely I don't use.
This laptop will be linked to the main router directly via LAN cable.

I want to know if it's we suggest me to install the Server version or the Desktop version (and after install the various programs)

I know that the Server version run only via command line (so is not graphical).... (please correct me if I'm wrong)

I'd like to have a suggestion by you and also how to start to set it (if there are some .pdf guide it will be appreciate).

P.S. :
This Server will be a Home Server and will offer some services as:
Internal E-Mail
Personal web site
ftp
chat
bbs
Possibility to install the OS (and surf) withous install directly it  (via LAN or Wireless -and any user will have a personal account for the access- )
VPN Service if a user connect itself outside the home.
Wake Up On Lan Service (if available)
Tnx so much for the answers!!!!!!!!

Best Regards

---

### Post by imachavel on 2012-03-10
I'd assume ubuntu server would be better, although ubuntu desk top can be configured as a server. So you want to have your own web site that is run from local host? Do you plan to host this on the internet? When you say e email client, you mean to say you will use mail clients like outlook, thunderbird, or evolution, and sync them with your internet mail clients? Really you don't need a server for such purposes, if you plan on just syncing with dns servers online through your I.S.P. etc. etc. etc. a server is to create a private lan that gives out i.p. addresses and has it's own private manageability, that people at work can do all sorts of stuff, access email, etc. even vpn into a computer from a remote location outside the network but within the networks firewall

if you are looking into file sharing with another computer that uses windows, you will need to know how to configure samba, which I am not aware of how to configure. If you just want to use or host a printer, you just drivers for your printer or printer server that are host based or network based etc. You'd have to be more descriptive, but the simple answer, any ubuntu distro will work. I think ubuntu server just makes it easier to configure ubuntu as a server but both as a back end have the same programs and functions built in, either through synaptic manager, or somewhere else in the back that can be configured.

If you want to set up an internal dhcp network in an office, I'd say a laptop might not have the processing power, but then if only a few people access it a day, it definitely has the processing power. Anyway w/e you know how to download the .iso of the distro you want, burn it to a cd, then boot to and install it right? If you plan to keep a windows OS you want might to check how large of an hdd you have, and look into partitioning a new spot with gparted or some other partition manager(avoid shrinking a partition unless absolutely necessary, it can cause data loss)

good luck, and if possible, describe how you want mail clients set up more in depth

---

### Post by matt_symes on 2012-03-10
Hi

Personally i would install the server version and configure it using ssh or webmin. I have used both.

> This Server will be a Home Server and will offer some services as:
Internal E-Mail
Personal web site
ftp
chat
bbs
VPN Service if a user connect itself outside the home.
Wake Up On Lan Service (if available)


I can't see there being a problem with any of those services. There are loads of tutorials on the net to set them up. Any specific question you can ask here.

Wake up on Lan will depend on your box but it is possible from the tutorials i have seen (i've never used it myself).

> 
Possibility to install the OS (and surf) withous install directly it (via LAN or Wireless -and any user will have a personal account for the access- )



I'm not sure what you mean here.

Kind regards

---

### Post by 3rdalbum on 2012-03-10
Install either. The only difference is the GUI. You could use Desktop and then remove the GUI once your system is set up.

---

### Post by Cheesemill on 2012-03-10
> **3rdalbum said:**
> The only difference is the GUI.

And the kernel :)

---

### Post by Bruno81 on 2012-03-10
Hi again and tnx for the answers.

I'll try to be more precise for give to you the possibility to help me.

So....

At home we're 5 person (I think that a laptop with dualcore can bee good....) and 4 person use Windows and I use Ubuntu Linux Natty Narwhall.

I'll link the "Server" to a wireless router Cisco.

After made all the settings to the OS Ubuntu (Server or Desktop) I'll set the config to the router.

Now.....

My parents and all people that would like to use the connection will be forced to sign in to a primarely web page (shared by the home server) and after they can use the connection. (In this case I'll use a web page and the web service).

If a person would like to store video or photo of the holidays they can put it into an hd via ftp (so they must use the ftp service).

If I need to sent (into the home) an e-mail with an info (for example) to a partent I'll use the internal e-mail (for example [email]brother@home.pvt[/email]) (so in this case the'll use the mail service).

And if they would like to don't delete or install Ubuntu on the hd, the'll use the lan connection or the wireless to use the version of Ubuntu after have access to the pesonal account (via PXE on the Home Server)....

For the chat and the BBS I'll install the services found online.

For the Wake Up On Lan I must make a little bit of sarch on the NET......

Tnx so much again for the answers and for the help.

Believe these info can help you.

Best Regards.

---

