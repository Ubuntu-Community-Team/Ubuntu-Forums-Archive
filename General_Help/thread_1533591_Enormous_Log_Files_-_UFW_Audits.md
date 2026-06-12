---
title: "Enormous Log Files - UFW Audits"
date: 2010-07-18
forum: General Help
---

### Post by Andrew Howe on 2010-07-18
Hi,

I've had a problem ever since I installed Ubuntu a few months ago. Every  so often, Ubuntu will tell me that I am running out of disk space and,  upon inspection, I see that the log files are what is taking up the  room. I can delete them, but this is only a temporary solution as they  soon grow back again.

The logs in question are kern.log, ufw.log, syslog and messages. They  seem to be being filled with 'UFW Audits' such as:

Jul 16 00:56:09 andrew-desktop kernel: [  aaa.bbbbbb] [UFW AUDIT] IN=  OUT=eth0 SRC=192.168.2.3 DST=aaa.bbb.ccc.ddd LEN=60 TOS=0x00 PREC=0x00  TTL=64 ID=aaaaa DF PROTO=TCP SPT=60009 DPT=80 WINDOW=5840 RES=0x00 SYN  URGP=0

(where I've blanked out the uniquely identifiable stuff)

What are these messages for and how can I stop them filling up my logs?

Thanks.

---

### Post by sinthetek on 2010-07-18
The messages you refer to are logged by your firewall (UFW). They can be disabled either by turning the firewall off or by disabling ufw logging.

You can modify which files get logged to if there are duplicate entries by editing syslog.conf. If you want to only log certain activity, you should probably disable ufw logging entirely and use iptables for the purpose.

More detailed instructions for all of these options can be found here: [https://help.ubuntu.com/10.04/serverguide/C/firewall.html](https://help.ubuntu.com/10.04/serverguide/C/firewall.html) (search the page for "Logs" and read from there)

---

