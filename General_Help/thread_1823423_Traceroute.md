---
title: "Traceroute?"
date: 2011-08-12
forum: General Help
---

### Post by xtremo on 2011-08-12
Hi guys....can you tell me how I run a traceroute on 11.04?

I have done a search but I'm none the wiser.

Many thanks!

---

### Post by Nytram on 2011-08-12
One way is to open a terminal and type **traceroute <hostname>**

---

### Post by xtremo on 2011-08-12
Cheers mate!

---

### Post by haqking on 2011-08-12
whenever you are stuck with how to use a command then use the following:

man traceroute

info traceroute

will show you parameters, syntax and information relating to its use.

---

### Post by IT Support on 2011-08-12
SYNOPSIS
       traceroute [-46dFITUnreAV] [-f first_ttl] [-g gate,...]
               [-i device] [-m max_ttl] [-p port] [-s src_addr]
               [-q nqueries] [-N squeries] [-t tos]
               [-l flow_label] [-w waittime] [-z sendwait]
               [-UL] [-P proto] [--sport=port] [-M method] [-O mod_options]
               [--mtu] [--back]
               host [packet_len]
       traceroute6  [options]
       tcptraceroute  [options]
       lft  [options]



have you try to install it ?
sudo apt-get install traceroute

---

### Post by dcstar on 2011-08-13
> **haqking said:**
> whenever you are stuck with how to use a command then use the following:

man **tracert**

info **tracert**


Linux is **not** Windows.

---

### Post by haqking on 2011-08-13
> **dcstar said:**
> Linux is **not** Windows.


ha ha yeah i know, my bad...dunno why the hell i wrote that.

Cheers

---

### Post by t0p on 2011-08-13
You can also do traceroute in GUI (for all you CLI-phobes out there!):

Go to **System > Administration > Network Tools**

You can also do Ping, Netstat, Port Scan, Lookup, Finger and Whois there.

---

