---
title: "Safety Question of Using PC as Host"
date: 2010-08-31
forum: General Help
---

### Post by tklh27 on 2010-08-31
Hello my name is TKLH27 and this is my first question on the forums.

I've been using a dual pc/ubuntu and virtual pc (windows xp) on ubuntu as a host. 

However these options seemed a bit still limited in on terms of gaming and flash (oh how I loathe it, Flash). 

Thus I decided to try virtual box ubuntu on PC host, however I am quite unsure how safe this will be, in terms of security.

I know that the virtual XP on ubuntu host will be generally safe for the host computer on surfing the net, but is the opposite combination true? 

Since PC doesn't have the same security as Ubuntu, would making PC a host for it be alright in terms of security for both systems?

---

### Post by bodhi.zazen on 2010-08-31
Not sure what you are asking, basically there is no difference in security between a physical and a virtual machine with the only possible exception in the network tab, you can use NAT , host only, or bridged networking.

If you are using Ubuntu as a host, Windows as a guest, and NAT or Bridged networking, Windows is vulnerable (Ubuntu does not protect the windows virtual machine in any way).  Host only or no network connection would be the same as disconnecting the internet on windows, and thus more secure.

---

### Post by tklh27 on 2010-08-31
So if I used windows as the host and ubuntu as a guest, and shared files between them, would the host windows be vulnerable more than the guest ubuntu?

---

### Post by bodhi.zazen on 2010-08-31
> **tklh27 said:**
> So if I used windows as the host and ubuntu as a guest, and shared files between them, would the host windows be vulnerable more than the guest ubuntu?

IMO yes, but only because IMO a default installation of Windows is more vulnerable then a default installation of Ubuntu.

You need to treat security on a VM exactly the same as on a physical machine. Virtual machines are no more or less vulnerable then physical machines (with the exception of networking options [ NAT / host only / none ] I mentioned above.

The host OS does not interact or protect the virtual machine in any meaningful way, although virtualization keeps the guest OS isolated.

Sharing files is sharing files, does not matter all that much if you use shared folders, samba, ftp, or a flash drive.

---

### Post by tklh27 on 2010-08-31
Thank you very much!

---

