---
title: "DHCPD.conf Error when creating reservations"
date: 2012-08-09
forum: General Help
---

### Post by LookUpSeeBlu on 2012-08-09
Hello,

I am getting the following error after I changed my DHCPD.conf file to include a reservation:

```
~$ sudo /etc/init.d/dhcp3-server restart
dhcpd self-test failed. Please fix the config file.
The error was: 
/etc/dhcp3/dhcpd.conf line 44: expecting a parameter or declaration
host HOSTNAME {
              ^
/etc/dhcp3/dhcpd.conf line 45: expecting a parameter or declaration
***	hardware ethernet MAC:ADDRESS;
                                     ^

```

I just appended the reservation to the end of my dhcpd.conf file.  I also tried embedding it within the scope (subnet) but then it complained that it was global.

Thanks for any help.

Kevin

---

### Post by papibe on 2012-08-09
Hi LookUpSeeBlu.

There's clearly a syntax error, but it is difficult to guess what it is without seeing your conf file. Could you post it so we can take a look?

Regards.

---

### Post by LookUpSeeBlu on 2012-08-09
```
ddns-update-style interim;

subnet 10.0.0.0 netmask 255.255.255.0 {
        range 10.0.0.20 10.0.0.244;
        default-lease-time 86400;
        max-lease-time 86400;
        option routers 10.0.0.1;
        option broadcast-address 10.0.0.255;
        option subnet-mask 255.255.255.0;
        option domain-name-servers 10.0.0.10;
}

host KevinsMacbookAir {
***     hardware ethernet 63:65:81:3a:ba:4d;
***     fixed-address 10.0.0.25; }
```

---

### Post by papibe on 2012-08-09
Remove the '***' strings on both lines.

Tell us how it goes.
Regards.

---

### Post by LookUpSeeBlu on 2012-08-09
Yeah those aren't really there... my bad for grabbing the error output instead of my cat'd dhcpd.conf....

---

### Post by LookUpSeeBlu on 2012-08-09
```
ddns-update-style interim;

subnet 10.0.0.0 netmask 255.255.255.0 {
        range 10.0.0.20 10.0.0.244;
        default-lease-time 86400;
        max-lease-time 86400;
        option routers 10.0.0.1;
        option broadcast-address 10.0.0.255;
        option subnet-mask 255.255.255.0;
        option domain-name-servers 10.0.0.10;
}

host KevinsMacbookAir {
       hardware ethernet 63:65:81:3a:ba:4d;
       fixed-address 10.0.0.25; }
```

---

### Post by papibe on 2012-08-09
A few thoughts:[LIST]
[*]I would put the declaration inside the subnet.
[*]I would use the standard syntax with the '}' in its own line:
```
host KevinsMacbookAir {
       hardware ethernet 63:65:81:3a:ba:4d;
       fixed-address 10.0.0.25;
}
```
[*]I would **not** use 25 as a fix address because it is in the dhcp range (20 to 244).
[/LIST]
Tell us how it goes.
Regards.

---

### Post by LookUpSeeBlu on 2012-08-09
OK OK OK....  turns out... strangely...

some extra characters got in there..... not sure why they weren't showing up from my mac, but I grabbed another ubuntu box and ssh'd in from there.... boom there were extra characters....

removed those, all set....

Thanks for your help.

Kevin

---

### Post by papibe on 2012-08-09
Glad you were able to fix it.

Please mark the thread as solved (read [here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")), when you have the chance.

Regards.

---

