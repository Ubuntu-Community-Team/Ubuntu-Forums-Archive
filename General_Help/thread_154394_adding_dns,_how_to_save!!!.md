---
title: "adding dns, how to save!!!???"
date: 2006-04-03
forum: General Help
---

### Post by drop_d33 on 2006-04-03
hi. i have a problem with adding a new dns. i go to System-Admiinistration-Networking and under the dns tab i enter the new dns,  click on the add button and add another. when i exit the networking tool, and open it again, everything's okay, the new dns is still there. but when i reboot ubuntu and open the networking tool again, the new dns is gone. only the original dns shows up. what is this? cant u save new dns? how? please people help..

---

### Post by kcbanner on 2006-04-03
I had this problem also.

When you reboot, the DHCP server (router) supplies your computer with DNS information.

Why are you changing the DNS, if it doesn't work, you should change in on your router so all the computers connected run off the new DNS.

Hope this helps
-kcbanner

---

### Post by professor_chaos on 2006-04-03
A hack solution for you would be to use "chattr" to lock the file so that even root can't modify the file. First edit the file /etc/resolv.conf and then...

```
sudo chattr +i /etc/resolv.conf
```

this will prevent changing of the file. To unlock the file use...

```
sudo chattr -i /etc/resolv.conf
```

---

### Post by jude999 on 2006-04-03
I had the exact same problem that I solved yesterday by setting a static IP and got rid of that stupid DHCP. Works wonders for me.

---

### Post by MakubeX on 2006-04-03
Or how about if you just modify /etc/resolv.conf manually? (like via a text editor such as vi or gedit)

Or maybe you can also try deleting /etc/resolv.conf (but create a backup of its content first) then make a new resolv.conf and input the previous contents..

Then, reboot and check! After reboot, try to test the GUI by adding another DNS, then reboot and check if the DNS is successfully placed in the file.

Well, it's just that I don't believe chattr command is the solution..

---

