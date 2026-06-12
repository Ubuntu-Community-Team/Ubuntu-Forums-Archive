---
title: "nic card drivers"
date: 2006-03-28
forum: General Help
---

### Post by slipk487 on 2006-03-28
where should i go to get D-Link drivers for ubuntu because its doenst have drivers for my card

---

### Post by bnj on 2006-03-28
Hello. 
Did you try [ndiswrapper](http://ndiswrapper.sourceforge.net/)?

---

### Post by jamesr on 2006-03-28
What D-link card? wired or wireless?

---

### Post by slipk487 on 2006-03-28
wired pci

---

### Post by jamesr on 2006-03-28
what type eg de220 etc

---

### Post by slipk487 on 2006-03-28
its a D-Link Dfe-530TX

---

### Post by slipk487 on 2006-03-28
and when i find it how do i install it

---

### Post by chocolatetoothpaste on 2006-03-29
I had a similar problem configuring a devil linux firewall. I had a D-Link card, but i didn't know which module to load.  I had a D-Link 21140, and I had to load the de4x something or other driver.  Sorry I can't remember which.  I also think the tulip module works with some D-link cards.  I google searched my card and found a site that told me which module to use.  Also, strangely, I was able to use the realtek 8139too module, and it worked with my D-link card.  Hope this helps.

---

### Post by slipk487 on 2006-03-29
well how do i add the driver because i dont think the card shows up in the device manager

---

### Post by jamesr on 2006-03-29
Could you post the outputs```
sudo ifconfig -a
dmesg |grep eth0
```

There seem to be different drivers if it is 530TX or 530TX+ so the outputs are important.


If I have understood correctly 

```
sudo modprobe via-rhine 
```
or
```
sudo modprobe rtl8139
```

---

### Post by slipk487 on 2006-03-29
when i use sudo command in the terminal it never works

---

### Post by jamesr on 2006-03-29
What do you mean it never works ?
Does it ask for a password.?

Also the modprobe does not return anything unless there is an error.

---

### Post by slipk487 on 2006-03-29
Also the modprobe does not return anything unless there is an error.[/QUOTE]
yes it asks for a password but nothing happens after i hit enter after putting in the password

and would the driver in the attachment work and is there an better way to do it because it seems harder the way it is explained

---

### Post by jamesr on 2006-03-29
It looks as if nothing happens. It the best way to see any change would ```
sudo ifconfig -a
``` before and after noting any change

---

### Post by jamesr on 2006-03-29
I have looked at the file. It is the information about compiling the rhine driver.  If the rhine driver was not on your system, modprobe would generate an error, which you you are saying it is not.

you will still need to```
sudo modprobe etc 
```to load the module.

---

### Post by slipk487 on 2006-03-30
i finally got it to work but its weird because the first time i installed it it had no drivers and i just had to reinstall it to fix system errors and it somehow now has the drivers but it works and thats all that matters and thx for all the help

---

### Post by jamesr on 2006-04-01
All's well that ends well

---

