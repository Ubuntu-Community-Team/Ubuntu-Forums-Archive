---
title: "Ubuntu unable to find/connect to any routers at all."
date: 2011-07-18
forum: General Help
---

### Post by rXu on 2011-07-18
I just installed my Ubuntu 11.04 alongside with my Windows 7. The only problem I have with my Ubuntu is that it cannot seem to find or connect to any routers. I think it COULD be the drivers that are missing. When I try to use the router I have at home with my Windows 7, (on the same laptop) it works fine. I use a Airport Extreme router. Can anyone help me with this? 

P.S: Sorry if this is too vague by the way. If you need anymore included information, I will give it to you.

---

### Post by rXu on 2011-07-18
Bumping in hopes of getting a response. I really need help.

---

### Post by Hulkiedulkie on 2011-07-18
Try bringing up the interface with "sudo ifup wlan0" and see if it gives any errors. That usually indicates a driver problem.

Install ethtool and post the output of "sudo ethtool wlan0". Perhaps that will give us some clues (don't know if ethtool works for wireless but it helped me with wired problems)

---

### Post by rXu on 2011-07-18
> **Hulkiedulkie said:**
> Try bringing up the interface with "sudo ifup wlan0" and see if it gives any errors. That usually indicates a driver problem.

Install ethtool and post the output of "sudo ethtool wlan0". Perhaps that will give us some clues (don't know if ethtool works for wireless but it helped me with wired problems)

Can you give me steps on how to do this? Sorry, I am an Ubuntu noob.

---

### Post by rXu on 2011-07-18
Bumping again for more responses.

---

### Post by rXu on 2011-07-18
If I don't get help after this final bump, then I'm just going to give up and erase my Ubuntu

---

### Post by garvinrick4 on 2011-07-18
It takes time sometimes to get help, there are no paid employee's in these Forums.
Anyway your problem would be drivers for your Network card. This below will
tell what you have going on. Open a terminal and copy and paste these. (ctrl/alt/t)
Post results:
```
sudo lshw -C network
```
```
 lspci -nnk | grep -iA2 network 
```

---

