---
title: "Disable IPv6"
date: 2006-06-03
forum: General Help
---

### Post by maxbaggi on 2006-06-03
How do I disable IPv6 across the whole system?  I'm using Kubuntu Dapper Drake 6.06

---

### Post by dresnu on 2006-06-03
Put this line: ```
KDE_NO_IPV6=true
```
at the end of /etc/environment

---

### Post by givré on 2006-06-03
If you are using firefox, open a new tab, type about:config in the adress bar and search for network.dns.disableIPv6.
Set the value to true and it should be ok

---

### Post by maxbaggi on 2006-06-03
@ dresnu
I'll try that and report back in a minute :-D 

@ givré
I'm not using Firefox... thanks anyway :)

---

### Post by maxbaggi on 2006-06-03
@ dresnu
It didn't work... even after a reboot.
The method described in the following page worked in Breezy but it doesn't work in Dapper.
[http://ubuntuforums.org/showthread.php?p=477822#post477822](http://ubuntuforums.org/showthread.php?p=477822#post477822)

---

### Post by ozorba on 2006-06-03
[QUOTE=maxbaggi]@ dresnu
It didn't work... even after a reboot.
The method described in the following page worked in Breezy but it doesn't work in Dapper.
[http://ubuntuforums.org/showthread.php?p=477822#post477822](http://ubuntuforums.org/showthread.php?p=477822#post477822)[/QUOTE]

Now that is ver odd. All you need to do is edit /etc/modprobe.d/aliases file

find 

alias net-pf-10 ivp6

and change it to 

#alias net-pf-10 ivp6

and type the following 3 lines

alias net-pf-10 ipv6 off
alias net-pf-10 off
alias ivp6 off

It certainly works on my PC and it is not Kubuntu dependent.

You may need to restart your computer after this.


OZ

---

### Post by maxbaggi on 2006-06-03
> and type the following 3 lines
 
 alias net-pf-10 ipv6 off
 alias net-pf-10 off
 alias ivp6 off

Are you sure it's "alias ivp6 off" and not "alias ipv6 off"?

I'm attaching my /etc/modprobe.d/aliases

---

### Post by void_false on 2006-06-03
How about just removing IPv6 module?

```
$sudo mv /lib/modules/$(uname -r)/kernel/net/ipv6/ipv6.ko /lib/modules/$(uname -r)/kernel/net/ipv6/ipv6.ko.bak
$sudo depmod -a
```

---

### Post by Rackerz on 2006-06-03
Why are you trying to turn off IPv6? Just wondering.

---

### Post by khughes on 2006-06-03
[QUOTE=Rackerz]Why are you trying to turn off IPv6? Just wondering.[/QUOTE]

Because some dsl modems choke on ipv6 traffic. Take mine for example. I am using a qwest actiontec gt701-wg. It is a dsl modem/wireless router combined. Opening firefox and typing about:config in the address bar allowed me to search for ipv6 and turn that option off so I could surf, but that setup only affects my browser. 

My apt-get still will not work. The only resolution I had ever found for the rest of my system is to run a constant ping to whatever address I am trying to access. So if I wanted to update my packages, I would have to open a constant ping window for every repository in my sources.list file before I ran apt-get update. This resolution doesnt seem to be working on dapper though.

What I am mostly concerned about is that I installed dapper yesterday and all traffic was being passed just fine so I thought the ubuntu devs resolved the ipv6 issue. But I wiped my windows partition and reinstalled dapper to the whole drive and now I am back in the same "sinking" boat.

---

