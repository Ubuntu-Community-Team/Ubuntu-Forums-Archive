---
title: "Problem connecting to internet with 3G modem"
date: 2011-10-25
forum: General Help
---

### Post by johnbdublin on 2011-10-25
Hi,
I recently upgraded to the latest version of Ubuntu. Ever since the upgrade I have been having trouble connecting to the internet. I have a huawei 3G mobile broadband modem and I need to try and connect over and over again until the connection is made. I have never had this problem on the previous versions of Ubuntu. This has only happened since I upgraded last week.
Please help,
Thanks,
John

---

### Post by Gatemaze on 2011-10-25
Was that an upgrade or a fresh install? Sometimes upgrades can break things that used to work...

---

### Post by johnbdublin on 2011-10-25
Thanks for your quick reply.
It was an upgrade as it appeared in the upgrade manager. I upgraded from 10 to the latest version. I think its 11.1. It was working perfectly before I upgraded. I try different things, such as unplugging the modem and adding it again, or deleting the modem from the wireless connections interface and adding it again. If I try over and over again it works. Can you suggest any troubleshooting methods?

---

### Post by johnbdublin on 2011-10-26
Is there anything else I can try here? Please help!

---

### Post by alexfish on 2011-10-27
Can try Sakis3g
[*Sakis3G* - All-in-one script]("http://www.google.com/url?sa=t&rct=j&q=sakis3g&source=web&cd=1&ved=0CCIQFjAA&url=http%3A%2F%2Fwww.sakis3g.org%2F&ei=CwWpTva2N47V8QPQ_rGZDA&usg=AFQjCNFR0OA7GJQY3djYswddHkMjARyyDw&cad=rja")

they also have a forum and a wiki site

alexfish

---

### Post by johnbdublin on 2011-10-28
Hi,
I do not know how to use this sakis3g or install it. THe connection does eventually happen, but it takes about 25 attempts to connect. Each time it comes back with Modem disconnected, you are not connected.
It does register on the GSM home netowrk, but when I try to connect my broadband modem to the internet it does not work.

I rang my mobile operator, and they told me that my modem (Huawei) is not suported on Abuntu! 
It did work on the previous version of abuntu perfectly. Having hte problem with version 11.14.
Please help!

---

### Post by johnbdublin on 2011-10-30
I installed mobile partner and updated the resolve.conf file for a DNS server as installing mobile partner does not do this.
its fixed now, but this is a bad bug on abuntu 11.14. Hope its fixed soon.

---

### Post by alexfish on 2011-10-30
> **johnbdublin said:**
> I installed mobile partner and updated the resolve.conf file for a DNS server as installing mobile partner does not do this.
its fixed now, but this is a bad bug on abuntu 11.14. Hope its fixed soon.
Have you tried Network Manager VPN connections "tab" Ipv4 Settings select > method Automatic (PPP) address only
can enter address in "DNS servers" ; textbox

also check Authentication methods are correct under the PPP settings

alexfish

---

