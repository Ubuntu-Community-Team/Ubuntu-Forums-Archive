---
title: "Question about mac address change"
date: 2009-10-11
forum: General Help
---

### Post by moonner17 on 2009-10-11
Hello, everyone.

Is there a way to change MAC address  forever in Ubuntu 9.10 ?

I used 9.04 before, and I could use "gedit" to /etc/init.d/bootmisc.sh to modify something.
ex.
-------------------------------------------
sudo gedit /etc/init.d/bootmisc.sh

add following scripts:

ifconfig eth0 down
ifconfig eth0 hw ether 001122334455
ifconfig eth0 up
--------------------------------------------

The MAC address could been changed automatically after Ubuntu 9.04 started.

But, I upgrade 9.04 to 9.10 and the bootmisc.sh is gone.
The function of auto-change is not working.

Our department network rule is following "One IP to One MAC address" .
I have to use 1 IP for 2 computer, 
so the other mac address would be changed every time.

Can anyone give me some suggestions ?
Very Thanks :)

---

### Post by delcypher on 2009-10-11
There's a tool that will do it for you.
```
sudo aptitude install macchanger
```

Make a note of your previous MAC address (where eth0 is the interface you want to look at, run ifconfig for a list available interfaces)
```
macchanger -s eth0
```

to change your mac address run ( where XX:XX:XX:XX:XX:XX is your new mac address)
```
sudo macchanger --mac=XX:XX:XX:XX:XX:XX
```

run```
man macchanger
```
for more information

If you want a visual interface instead of the command line install
```
sudo aptitude install macchanger-gtk
```

I'm not sure how permanent the changes macchanger makes is.

Enjoy.

---

### Post by Lars Noodén on 2009-10-11
You can try putting your re-configuration lines in /etc/rc.local
```
ifconfig eth0 down
ifconfig eth0 hw ether 001122334455
ifconfig eth0 up
```

Or somewhere in /etc/network/if-up.d/ or /etc/network/if-pre-up.d/

---

### Post by blueridgedog on 2009-10-11
How is it that you have two computers with the same MAC address?

---

### Post by moonner17 on 2009-10-12
To delcypher & Lars Noodén :
 
Very thanks for your suggestions.
 
I use "macchanger" to do , 
the mac address still be recoverd to original one (hardware) at restart.
The other way, I can' find rc.local in /etc/network/if-up.d/ or /etc/network/if-pre-up.d/.
 
I'm appreciate for your helps, and I still want to find the way to solve it.
 
To blueridgedog
 
I registered the mac address of PC1 
but I have a work to use PC2 without power to register a new IP.
 
:) very thanks

---

### Post by Lars Noodén on 2009-10-12
/etc/rc.local is a separate file, for (too) general use.

---

### Post by t0p on 2009-10-12
You could set macchanger to run at startup (in Startup Applications).  Or, if you like, a script containing the ifconfig commands that do the same thing.

Any way you use to change the mac address will be some kind of variation of the above.  I don't think it's possible to *really* change the mac address, as I believe it's hard-wired in the hardware. So you need to spoof the mac - which involves macchanger/ifconfig.

---

