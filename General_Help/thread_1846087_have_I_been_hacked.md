---
title: "have I been hacked?"
date: 2011-09-18
forum: General Help
---

### Post by &gt;hankim&lt; on 2011-09-18
hello, 
my wifi card has got activity even when I'm not using the internet connection for anything, what can it mean?
IPtraf is capturing thousand of packets... that doesn't feel normal! 
please help me solve this, I'm worried!

---

### Post by lkjoel on 2011-09-18
Did it capture that number of packets before? Are you in a secured wireless network? Are there many people around you?

---

### Post by &gt;hankim&lt; on 2011-09-18
it captured them while I wasn't using the internet, it's a shared connetcion from the residence I'm living  secured by password (if you mean so), so there could be more people using the connection and nearby

---

### Post by lkjoel on 2011-09-18
If you see thousands of packets, then it means that some other people were using the network. If it's shared, then that explains it.

---

### Post by &gt;hankim&lt; on 2011-09-18
really? but why should it affect my computer? I mean, I've got a light on the laptop saying when there's activity and it never happened before even when I was using other shared connections, it's weird...
thx for answering

---

### Post by lkjoel on 2011-09-18
The application shows packets for everyone in the network, not just you. If you really want to see, try Wireshark.

---

### Post by SparTacux on 2011-09-18
I've never used the application you mentioned - but i guess it's picking up broadcast traffic from the other computers on your network. If you have GUFW installed as a firewall then enable logging and take a look at the UFW logs - you'll be able to see what is happening.

---

