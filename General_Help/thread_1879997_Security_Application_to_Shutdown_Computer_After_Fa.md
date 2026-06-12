---
title: "Security Application to Shutdown Computer After Failed Attempts"
date: 2011-11-12
forum: General Help
---

### Post by chiques on 2011-11-12
Hello,
I am planning on opening some ports on my home firewall to access my Ubuntu machine via VPN. As a security measure I would like to only allow 2 password attempts. If those two attempts fail then I would like for the machine to power down. 

Is there an application that will do this for me?

Thanks for any feedback.

---

### Post by Dangertux on 2011-11-12
> **chiques said:**
> Hello,
I am planning on opening some ports on my home firewall to access my Ubuntu machine via VPN. As a security measure I would like to only allow 2 password attempts. If those two attempts fail then I would like for the machine to power down. 

Is there an application that will do this for me?

Thanks for any feedback.

I'm not so sure about shutting down the machine, though you could script it yourself based on the output of an application like fail2ban. Personally, I would use fail2ban to block the connection attempt there is really no need to shut down the machine.

Here is some relevant documentation on setting up fail2ban for OpenVPN [http://www.fail2ban.org/wiki/index.php/OpenVPN](http://www.fail2ban.org/wiki/index.php/OpenVPN)

hope that helps.

---

### Post by chiques on 2011-11-12
> **Dangertux said:**
> I'm not so sure about shutting down the machine, though you could script it yourself based on the output of an application like fail2ban. Personally, I would use fail2ban to block the connection attempt there is really no need to shut down the machine.

Here is some relevant documentation on setting up fail2ban for OpenVPN [http://www.fail2ban.org/wiki/index.php/OpenVPN](http://www.fail2ban.org/wiki/index.php/OpenVPN)

hope that helps.

Hi Dangertux,
Thanks for the response. It sounds like blocking the connection is more practical. I have an inexperienced security question though:

Is it common that an attacker would change their IP address? If the attacker has infinite IP addresses, would this allow for infinite password entries until the log in is cracked? 

By shutting down the machine, this would make future attacks impossible until I powered it back on.

Thanks in advanced for any comments.

---

### Post by Dangertux on 2011-11-12
> **chiques said:**
> Hi Dangertux,
Thanks for the response. It sounds like blocking the connection is more practical. I have an inexperienced security question though:

Is it common that an attacker would change their IP address? If the attacker has infinite IP addresses, would this allow for infinite password entries until the log in is cracked? 

By shutting down the machine, this would make future attacks impossible until I powered it back on.

Thanks in advanced for any comments.

In theory your statement is correct. However the attacker does not have infinite IP addresses, and he/she will realistically get 2 to 3 tries per IP address, have to change IP addresses (assuming they even have more than one, they're not using a home connection more than likely a compromised machine elsewhere) which will take a few minutes. The point is it will slow down the process so much the system will no longer provide a positive return on investment for the attacker.

---

### Post by JKyleOKC on 2011-11-12
An additional point to consider: while the default duration of a fail2ban block is set at 10 minutes, it's quite simple to configure it to block for a longer interval -- for instance, one second less than 24 hours. That would get rid of many would-be intruders for a full day.

I have to maintain an open server to support my little business, and use fail2ban with its default 10-minute setting. It has reduced the number of break-in attempts each day from several hundred to only about 30 (that is, three individuals making 10 attempts each before fail2ban shuts them out; they don't return after 10 minutes, but just go elsewhere).

Examine your /var/log/auth.log file after making several deliberate log-in failures to see what kind of information it makes available about the failures. You can then set up fail2ban using that information, or create your own script to force a full shutdown, as you prefer.

---

