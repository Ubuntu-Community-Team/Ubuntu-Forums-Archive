---
title: "Can no longer launch the Cisco VPN web client installer in Firefox"
date: 2012-05-08
forum: General Help
---

### Post by sos314 on 2012-05-08
In 11.10 (64 bit), I could go to my company's Cisco VPN portal in Firefox, log in, then click the "Start AnyConnect" link and it would launch the Java applet to connect me to my company VPN. Now that I have upgraded to 12.04 (64 bit), all I get when I click "Start AnyConnect" is the following:

Cisco VPN Client Download                          
The installer was not able to start the Cisco VPN Client.
  
I have the latest version of OpenJDK and Oracle Java installed and have tried setting each one to my default Java installation using 'update-alternatives --config java' and also made sure I have icedtea installed and the Oracle Java plugin for 7.04 installed in Firefox, but neither successfully launches the AnyConnect installation applet. Any idea why? I really need to connect to this for work and I can't get it anymore. It's very frustrating and I never would have upgraded if I would have known it was going to cause an issue.

Any help I can get would be fantastic and I'd be super grateful. Thanks!

---

### Post by sos314 on 2012-05-08
Any suggestions at all? I really need to connect to the VPN...

---

### Post by steeldriver on 2012-05-08
there seem to be a number of people reporting vpn problems after installing / upgrading to Firefox 12 - no idea why though

[http://ubuntuforums.org/showthread.php?t=1971020](http://ubuntuforums.org/showthread.php?t=1971020)

sorry I can't help but you might want to try rolling back the ff version or uninstalling and using a different browser?

---

### Post by sos314 on 2012-05-08
> **steeldriver said:**
> there seem to be a number of people reporting vpn problems after installing / upgrading to Firefox 12 - no idea why though

[http://ubuntuforums.org/showthread.php?t=1971020](http://ubuntuforums.org/showthread.php?t=1971020)

sorry I can't help but you might want to try rolling back the ff version or uninstalling and using a different browser?

Well, I've also tried in Chrome and it does the exact same thing. I can see it start the Java applet for a split second and then it jumps to the screen where it displays the message I posted above. Same thing in both browsers.

---

