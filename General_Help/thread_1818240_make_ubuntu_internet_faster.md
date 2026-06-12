---
title: "make ubuntu internet faster"
date: 2011-08-04
forum: General Help
---

### Post by jRdbRR on 2011-08-04
i ran across this online, what do you think? does it work? is it just an illusion? 

[http://ubuntumanual.org/posts/10/how-to-increase-internet-speed-in-ubuntu](http://ubuntumanual.org/posts/10/how-to-increase-internet-speed-in-ubuntu)

Internet speeds in Ubuntu can be increased. Simply follow the steps.

Open a Terminal via Applications->Accessories->Terminal  and type the following
                          sudo vim  /etc/sysctl.conf         (press i for edit mode)

Then Paste the Following at the end of the file:
         ## increase TCP max buffer size setable using setsockopt()
         net.core.rmem_max = 16777216
         net.core.wmem_max = 16777216
         ## increase Linux autotuning TCP buffer limits
         ## min, default, and max number of bytes to use
         ## set max to at least 4MB, or higher if you use very high BDP paths
         net.ipv4.tcp_rmem = 4096 87380 16777216
         net.ipv4.tcp_wmem = 4096 65536 16777216
         ## don't cache ssthresh from previous connection
         net.ipv4.tcp_no_metrics_save = 1
         net.ipv4.tcp_moderate_rcvbuf = 1
         ## recommended to increase this for 1000 BT or higher
         net.core.netdev_max_backlog = 2500
         ## for 10 GigE, use this, uncomment below
         ## net.core.netdev_max_backlog = 30000
         ## Turn off timestamps if you're on a gigabit or very busy network
         ## Having it off is one less thing the IP stack needs to work on
         ## net.ipv4.tcp_timestamps = 0
         ## disable tcp selective acknowledgements.
         net.ipv4.tcp_sack = 0
         ##enable window scaling
         net.ipv4.tcp_window_scaling = 1
 

Then  type the follwing to exit and save what you have just done. Press ESC to quit the edit mode and type the following.
                                    :wq

Then type the following to to apply the settings.
             sudo sysctl -p          
You can disable all these settings by removing these lines you added via:
             sudo gedit /etc/sysctl.conf

---

### Post by raja.genupula on 2011-08-04
was it possible to increase the speed even though modem is in use ?

---

### Post by The Cog on 2011-08-04
I have my doubts though I haven't tried those instructions.

I do know that the default setting for window scaling in Ubuntu is 1 already, so that bit won't make any difference.

I'd be interested to hear if it makes a measurable difference to you. I'm sure it wouldn't to me, because I already get my internet saturated when I download things, but that may vary from isp to isp.

---

### Post by jRdbRR on 2011-08-05
i haven't tried it yet. im somewhat wary of some things and its been really crazy at work so we'll see if i can get to it tomorrow.

---

