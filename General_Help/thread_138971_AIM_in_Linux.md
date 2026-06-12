---
title: "AIM in Linux"
date: 2006-03-02
forum: General Help
---

### Post by astronerd on 2006-03-02
Hi all, has anyone here tried to install and use AIM for linux from the
AOL site?  I use gaim right now and really love it, but I cant stand the
no file transfer feature.  I know that its supposed to be in Gaim 2.0,
but I just wanna see if anyone has used the AOL version to do file
transfers in the mean time..?  Thanks
Charles

---

### Post by ncappel1 on 2006-03-02
I can't say that I have tried the AOL version on Linux, but I can verify that the file transfer works on Gaim 2.0-- Many a file have been sent back and forth on the LAN. Stick with Gaim if you can, my friend, it supports more protocols, plus it has a streamlined, advertising free interface.

---

### Post by astronerd on 2006-03-02
Is gaim 2.0 stable enough to use right now?  Im just afraid that if I try it and something gets borked I wont be able to fix it...  I want to stay with gaim, its great.  But this file transfer is really bothering me....  Thanks for the help.

---

### Post by ncappel1 on 2006-03-03
Are you positive that 1.5 doesn't have file transfer? i distinctly remember using it, and having it work!

here is a link to the changelog: [http://gaim.sourceforge.net/ChangeLog](http://gaim.sourceforge.net/ChangeLog)

on the gaim site: [http://gaim.sourceforge.net/](http://gaim.sourceforge.net/)

---

### Post by swguru on 2006-03-03
1.5 has a file transfer feature, but the only time I tried to use it, it wouldn't work :( Could be due to the uni firewall though.

---

### Post by slavik on 2006-03-03
I find that when gaim is sending/receiving files, it is much faster than AIM (gaim 1.5 or 2.0)

---

### Post by 3rdalbum on 2006-03-03
I know that GAIM 1.5 can send files on MSN, but I've never tried recieving or using the AOL network.

---

### Post by LordBug on 2006-03-03
GAIM 1.5 will do file transfers, but NAT firewalling tends to get in the way.  I had it figured out once for the Windows version of GAIM (and have forgotten how I did it), but I haven't started yet on the Linux version.

---

### Post by Stormbringer on 2006-03-03
- In case you have a desktop firewall running (i.e. firestarter) ...

To get AIM filetransfers to work you need to open Port 5190-5193 (tcp/udp).

- In case you are behind a NAT firewall ...

You need to reconfigure your firewall so that Port 5190-5193 (tcp/udp) is forwarded to the ip-address of the PC you are working at (also called Port-Forwarding or Destination-NAT). This may be a problem if you cannot administer the firewall yourself (i.e. your company's firewall).

Anyone who's interessted in a list of ports for various types of protocols - take a look at Netgear's website, they have a rather good list there:
[Netgear - Port Numbers for Port Forwarding]("http://kbserver.netgear.com/kb_web_files/n100495.asp")

Cheers,
Storm.

---

### Post by astronerd on 2006-03-03
I am running firestarter 1.0.3 and have port 5190 open.  How do I get the other ports open?  I went to policies, and tried to add one, but I have no idea which one to pick from the drop down.  Thanks.  
BTW I have had very little luck doing AOL file transfers even before I was running a firewall...

---

### Post by Stormbringer on 2006-03-03
Well, I'm not using firestarter so I'm afraid I cannot assist you any further; I'm running my own NAT firewall with forwarding rules - and AIM filetransfer work just fine (Gaim 1.5 from Ubuntu Repo / 2.0 Beta 2 from MighMOS).

However, by looking at the [ Firestarter Policy Page]("http://www.fs-security.com/docs/policy-page.php") I would say you will need to create an Inbound policy that allows 5190-5193 as well as an Outbound policy with the very same ports. Since I'm not using firestarter I have no idea how to create/modify a policy. Sorry.

Maybe someone who actually has firestarter installed can help you more efficiently with this issue.

Storm.

---

### Post by TrendyDark on 2006-03-03
> **Stormbringer]Well, I'm not using firestarter so I'm afraid I cannot assist you any further said:**
>  Firestarter Policy Page[/URL] I would say you will need to create an Inbound policy that allows 5190-5193 as well as an Outbound policy with the very same ports. Since I'm not using firestarter I have no idea how to create/modify a policy. Sorry.

Maybe someone who actually has firestarter installed can help you more efficiently with this issue.

Storm.

Would this make Fire Sharing in Gaim work 100% of the time? (Assuming it works while using a different type of firewall) 

That's the only thing I hate about gAIM is having to tell people "sorry I use Linux & Gaim, you can't send me that file"

---

### Post by Stormbringer on 2006-03-03
[QUOTE=TrendyDark]Would this make Fire Sharing in Gaim work 100% of the time? (Assuming it works while using a different type of firewall) 

That's the only thing I hate about gAIM is having to tell people "sorry I use Linux & Gaim, you can't send me that file"[/QUOTE]

As mentioned above I'm running a NAT firewall on a separate Linux-Box (CentOS r4.2).

Gaim file transfers work 99.9% for me ... the only problem I experienced so far is when the receipient is behind a NAT firewall without proper port-forwarding - in this case the clients cannot establish a direct-connection, so the filetransfer is doomed to fail. Otherwise it works fine.

EDIT: Regarding file-transfers via AOL/ICQ AIM protocol.

Storm.

---

### Post by ncappel1 on 2006-03-03
I stumbled upon this thread earlier today, it has information on installing Gaim 2.0.

[http://ubuntuforums.org/showthread.php?t=133179](http://ubuntuforums.org/showthread.php?t=133179)

---

