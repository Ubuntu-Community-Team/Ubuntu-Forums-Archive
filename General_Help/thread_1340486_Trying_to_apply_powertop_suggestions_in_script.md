---
title: "Trying to apply powertop suggestions in script"
date: 2009-11-28
forum: General Help
---

### Post by jbrown96 on 2009-11-28
I'm a big fan of powertop and Powerdevil in KDE. I have set up several profiles in Powerdevil (power management daemon in KDE) to automatically suspend the computer after a while, turn off the monitor, dim screen, etc. I can also choose scripts to run. My idea was to take everything that powertop recommends and put it in a script to run. 

Powertop has to be executed by root, and then it gives suggestions that you can execute by pressing certain keys. For example, > echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
 is a suggestion and I can execute it by pressing "s". I thought that I could manually run this outside of powertop by running ```
sudo echo min_power > /sys/class/scsi_host/host0/link_power_management_policy

``` However, I get "permission denied" errors. I put sudo in front of the command; how can I lack permission to alter that file? When I run powertop, I give it the same permissions; is powertop actually running a slightly different command (possibly using D-Bus?)?
I've tried running all of the other powertop suggestions, but I get permission errors for all of them. 

If I get that working, then I need to be able to put them in a script. Since all of these commands presumably need root authorization, I will need to execute this script as root. I'm guessing that Powerdevil will either run it as my user or some other non-admin. Will I have to make the script SUID, so it executes wihtout silently prompting for a password?

Thanks.

---

### Post by ibuclaw on 2009-11-28
You command is actually 2 commands on one line:

```
sudo echo min_power
```
Is the first, ran as the default sudo user (root).
```
> /sys/class/scsi_host/host0/link_power_management_policy
```
Is the second, ran as a normal user (yourself).

What you instead have to do is reverse this:
```
echo min_power | sudo tee /sys/class/scsi_host/host0/link_power_management_policy
```
Regards
Iain

---

