---
title: "Unable to export VPN configuration info"
date: 2010-04-16
forum: General Help
---

### Post by t0p on 2010-04-16
I've got an EeePC, running Jaunty, and I can use the Network-Manager to connect through my ibVPN account just fine.

I want to also use this ibVPN account on my desktop running Hardy.  I've tried to manually transpose all the configuration info, but it keeps coming up with errors (a number of errors, including sometimes "bad username/password").  So I thought: "Hey, why am I even bothering with all this manually transposition of credentials?  I can just **Export** the account config info from the (working) Jaunty machine and then import them straight into the Hardy machine."  Should be pretty simple, huh?  Woulda, coulda, shoulda... Grrr!

I go to the VPN tag in the Network-Manager on Jaunty, select "ibVPN" (the working VPN account) and click **Export**.  I tell it to save the info to a file called *ibVPN (pptp).conf*... and I get an error saying:

```

**Cannot export VPN connection**
The VPN connection 'ibVPN' could not be exported to ibVPN (pptp).conf
Error: unknown error

```

You see that "Error: unknown error" crap?  Means I don't even know what needs changing.  Damn fool network-manager.  I've tried jiggling stuff round, but nothing seems to make a difference.

Anyone suggest why I can't export this config info?

---

### Post by Mike_sk on 2010-04-16
As far as I know there is a bug with the export option in Jaunty.

You should look at the link below for a VPN setup tutorial on Hardy 

[http://tipotheday.com/2008/04/29/connect-to-windows-vpn-server-pptp-with-ubuntu-hardy-heron/](http://tipotheday.com/2008/04/29/connect-to-windows-vpn-server-pptp-with-ubuntu-hardy-heron/)

---

### Post by t0p on 2010-04-16
Thanks for the tip Mike_sk. When I get back home I will check out that info.

---

