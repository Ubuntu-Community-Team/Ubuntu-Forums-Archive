---
title: "Scanning for open ports?"
date: 2009-11-22
forum: General Help
---

### Post by dgohn on 2009-11-22
Is there a simple way to check your server for what ports are open and by what users or applications?

Thanks in advance

---

### Post by animalprimate on 2009-11-22
this website will scan your main ports and tell you which is open.

[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

this command will show you what applications are running:

top

maybe this informations doesn't answer your question..

sounds like a ufw thing

---

### Post by dgohn on 2009-11-22
The top command is nice, thanks alot I do like that.  I was more or less looking for an internal program or command that would show all open ports on the machine or ports in use by the machine.

thanks

---

### Post by whoop on 2009-11-22
```

sudo apt-get install nmap

```
Used to scan remote machines

---

### Post by CrusaderAD on 2009-11-22
> **whoop said:**
> ```

sudo apt-get install nmap

```
Used to scan remote machines

Good stuff.

---

### Post by dgohn on 2009-11-22
thanks alot

---

### Post by bab1 on 2009-11-22
> **dgohn said:**
> The top command is nice, thanks alot I do like that.  I was more or less looking for an internal program or command that would show all open ports on the machine or ports in use by the machine.

thanks

Use the command ```
netstat
```

I believe the proper switches are -plnt

You can find the information with ```
man netstat
```

---

### Post by dgohn on 2009-11-22
Thats exactly what I was looking for.  Thanks alot!

---

