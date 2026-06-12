---
title: "Disable Internet access for a single user"
date: 2011-01-17
forum: General Help
---

### Post by rusty_vin on 2011-01-17
I have a Lucid Ubuntu installed on my home PC with two user accounts, AmHero and simple. 
I would like to have all internet access disabled when my kids login with the 'simple' userid. And yes, internet should work when I login using AmHero.
I tried this:

[http://www.ubuntugeek.com/disable-internet-access-for-particular-user-in-ubuntu.html]("http://www.ubuntugeek.com/disable-internet-access-for-particular-user-in-ubuntu.html")

..but this does not work and gives some errors on the terminal.

I can paste the errors, though I am not sure this will even work as I found this in an old post.

---

### Post by cariboo on 2011-01-17
open network-manager, highlight your interface, and select edit, in the window that opens up make sure Available to all users is not selected.

---

### Post by rusty_vin on 2011-01-17
wow! you guys reply quick!
and yes!!! this worked -- apart from the fact that there was a minor typo in the terminal command, totally my fault.

---

### Post by rusty_vin on 2011-01-18
I just found that I was able to access internet when logged in with the user id 'simple'. However, it got blocked again, when run the the sudo command :
sudo iptables -A OUTPUT -p tcp -m owner --uid-owner simple -j DROP
I do recall, testing it yesterday with a reboot, but my question is will this work beyond reboots ??

---

### Post by rusty_vin on 2011-01-18
I just found that I was able to access internet when logged in with the user id 'simple'. However, it got blocked again, when run the the sudo command :
*sudo iptables -A OUTPUT -p tcp -m owner --uid-owner simple -j DROP*
I do recall, testing it yesterday with a reboot, but my question is will this work beyond reboots ??

---

### Post by rusty_vin on 2011-01-21
Is there really any way I can permanently disable Internet for any a single user?? (or any command that *works* until I revoke it)

---

### Post by uberDoward on 2011-06-03
Bumping this, as I'm also interested.  We've got a specific system here that we want administrators to access the internet, and normal users unable to do so.

---

