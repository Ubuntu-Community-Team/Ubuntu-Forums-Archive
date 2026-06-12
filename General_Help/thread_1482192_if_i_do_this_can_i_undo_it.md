---
title: "if i do this can i undo it?"
date: 2010-05-13
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2010-05-13
i would prefer to switch them using the backlist if necessary
i am considering installing the manufactures wireless driver on my laptop
madwifi-hal-0.10.5.6
for a 2% increase in successful packet transfer from the router to the laptop
unfortunately the wireless button on my laptop will be constant amber with it
if i ping my router using the default driver it will blink amber and blue on windows it just stays blue 
this was my experience with using it on 9.04 where i had about a 40% loss with the default driver and the light was always amber

edit:

screw it *installs driver*
seems to be a 1% improvement
150 pings used
i can toggle it using this command
```
sudo gedit /etc/modprobe.d/blacklist-ath_pci.conf
``````
# For some Atheros 5K RF MACs, the madwifi driver loads buts fails to
# correctly initialize the hardware, leaving it in a state from
# which ath5k cannot recover. To prevent this condition, stop
# madwifi from loading by default. Use Jockey to select one driver
# or the other. (Ubuntu: #315056, #323830)
blacklist ath_pci
#blacklist ath5k
```

ping statistics
```
madwifi:
    100 packets transmitted, 99 received, 1% packet loss, time 99161ms
    rtt min/avg/max/mdev = 1.213/2.908/98.491/10.586 ms

    100 packets transmitted, 97 received, 3% packet loss, time 99163ms
    rtt min/avg/max/mdev = 1.374/1.556/2.238/0.162 ms

    100 packets transmitted, 97 received, +1 duplicates, 3% packet loss, time 99181ms
    rtt min/avg/max/mdev = 1.254/4.140/140.869/16.250 ms

    100 packets transmitted, 100 received, 0% packet loss, time 99169ms
    rtt min/avg/max/mdev = 1.240/1.458/3.172/0.281 ms

    100 packets transmitted, 97 received, 3% packet loss, time 99162ms
    rtt min/avg/max/mdev = 1.176/1.510/11.938/1.106 ms
default:
    100 packets transmitted, 96 received, 4% packet loss, time 99187ms
    rtt min/avg/max/mdev = 0.967/1.276/2.584/0.219 ms

    100 packets transmitted, 97 received, 3% packet loss, time 99177ms
    rtt min/avg/max/mdev = 0.940/1.170/1.984/0.192 ms

    100 packets transmitted, 98 received, 2% packet loss, time 99179ms
    rtt min/avg/max/mdev = 1.026/1.246/1.694/0.152 ms

    100 packets transmitted, 98 received, 2% packet loss, time 99166ms
    rtt min/avg/max/mdev = 0.978/1.202/1.734/0.184 ms

    100 packets transmitted, 98 received, 2% packet loss, time 99149ms
    rtt min/avg/max/mdev = 1.033/1.219/1.860/0.181 ms
```
hardware details in signature

---

