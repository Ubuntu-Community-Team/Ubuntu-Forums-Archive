---
title: "how to see who is connected to lan"
date: 2010-03-21
forum: General Help
---

### Post by spiky001 on 2010-03-21
From Terminal how can i see who is connected on local lan

---

### Post by 666f6f on 2010-03-21
> **spiky001 said:**
> From Terminal how can i see who is connected on local lan

Not sure what you mean by "who is connected on local lan", so I assume you want to detect nearby computers.

This should work: nmap -sS -O 192.168.1.1/24

You can find more examples here: [http://nmap.org/book/man-examples.html](http://nmap.org/book/man-examples.html)

---

### Post by spiky001 on 2010-03-21
it was on the local lan in house 5 pc connected just wanted to see which 1,s were using net, didn't no if netview or something like that would give ip and pc name but will get nmap if nothing else

---

### Post by 666f6f on 2010-03-21
Hi,

You can monitor network traffic with wireshark (GUI) or it's console counterpart tshark. There is always tcpdump which is pretty basic, but it does the job.

If you run the GUI version of wireshark, make sure you run it with root privileges, or else it may not work as expected.

---

### Post by Jose Catre-Vandis on 2010-03-21
Yep, you will need to install nmap first. Try this command to tidy up the output a bit and give you sumarised info

```
sudo nmap -sS -O 192.168.1.1/24 | grep -E "Interesting|Running|MAC"
```

---

