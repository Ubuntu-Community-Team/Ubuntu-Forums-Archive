---
title: "Some Epic grep guru help?"
date: 2009-08-05
forum: General Help
---

### Post by matessim on 2009-08-05
Edit: Scrap that, change to something that will just give the ip thats up in this format and append it to an new file like this
10.0.0.1 - -
10.0.0.2 - -
10.0.0.3 - -
10.0.0.138 - -

So, i need to generate a nice host list from a nmap host file, problem is i can't do it by hand because the network has like twenty subnets and aah 150-200 computers
lets say i have this file which has this:
Host 10.0.0.0 appears to be down.
Host 10.0.0.1 appears to be up.
MAC Address: 00:0F:B0:CE:00:D9 (Compal Electronics)
Host 10.0.0.2 appears to be up.
MAC Address: 00:0F:B0:CE:00:D9 (Compal Electronics)
Host 10.0.0.3 appears to be up.
Host 10.0.0.4 appears to be down.
Host 10.0.0.5 appears to be down.
Host 10.0.0.6 appears to be down.
Host 10.0.0.7 appears to be down.
Host 10.0.0.8 appears to be down.
Host 10.0.0.9 appears to be down.
Host 10.0.0.10 appears to be down.
Host 10.0.0.11 appears to be down.
Host 10.0.0.12 appears to be down.
Host 10.0.0.13 appears to be down.

i want to turn it into this:
10.0.0.1 00:0F:B0:CE:00:D9 -
10.10.0.2 00:0F:B0:CE:00:D9 -
10.0.0.3 - -

can anyone Please HELP me with this?
format is IP MAC -(don't know whats suppose tobe here in the format i need it in, might be Compal electronics but i don't wanna risk it as it really doesn't matter, so just -)
and if mac adress isn't there, just IP - -

---

### Post by Scienceman123 on 2009-08-05
I think you'll need an awk wizard for this one.

---

### Post by matessim on 2009-08-05
that tough? simple grep won't cut it here?
lets change it to this
gives only the IP adresses that are up
in this format
IP - -

---

### Post by matessim on 2009-08-05
bump.. not sure if it allowed, but it got to page 2 so i woulden't get any help there :S

---

### Post by Glyndwr on 2009-08-05
Your post is a little short of details.  Most of the IP's dont have a MAC address, can you add some info on what the criterion for selection is - do you only want IPs that have a MAC address, IPs that show as up etc?

---

### Post by Glyndwr on 2009-08-05
> **matessim said:**
> 
lets change it to this
gives only the IP adresses that are up


grep up file.txt|awk '{print $2, " - -"}'

---

### Post by matessim on 2009-08-05
> **Glyndwr said:**
> grep up file.txt|awk '{print $2, " - -"}'

That seems to work, can  anyone figure out a solution that works with mac adresses too? so IP's that i don't have they're macs will simply be IP - -
and hosts that i have they're mac will be IP MAC - (the ip's with mac have the mac said a line after as seen in the example)

---

### Post by matessim on 2009-08-05
After an hour of trial and error i got this:
i started with premade code i found to this:

```
#!/bin/sh
OUTFILE=hosts_scanned.dat
[ -f hosts_scanned.dat ] && rm hosts_scanned.dat
echo "nmap -sP -R -iL subnets.dat -oN $OUTFILE | grep up | awk '{print $2, " - - "}'"
echo ""
nmap -sP -R -iL subnets.dat -oN $OUTFILE | grep up | awk '{print $2, " - - "}' | sed -n '$!p' > cleandata.dat


```
now that i have this i need to get the thing with the MAC's working, i just figured my program won't work with just IP's, i need the macs too :S, later i will remove all ip's with no mac, but for now i need to find a way to sort out the MAC adresses.

---

