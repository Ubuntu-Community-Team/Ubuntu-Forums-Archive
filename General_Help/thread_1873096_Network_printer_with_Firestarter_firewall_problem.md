---
title: "Network printer with Firestarter firewall problem"
date: 2011-10-31
forum: General Help
---

### Post by winjeel on 2011-10-31
I'm running 11.04 and I have a printer on an internal network. Since installing FireStarter, I've found I couldn't print unless I disabled the firewall. I've tried to add the printer to the Outbound Traffic Policy whitelist, but then all of the internet and other services get blocked. So, setting the firewall back to permissive blacklisting mode then gives me access to the internet but blocks my printer. A catch 22. How can I print without the clumsy work-around of temporarily disabling my firewall?

---

### Post by 3rdalbum on 2011-10-31
If you're on an internal network, is there a particular reason why you need a firewall around the computer as well as a firewall at the gateway of your network?

Also, by default the firewall does NOT stop outbound connections; so you've been barking up the wrong tree there. Counter-intuitively it's probably an incoming port being blocked that is stopping the printing. I don't know what port, but some Googling might help you figure it out.

But yeah, my first suggestion would be to examine whether you really need the personal firewall. The gateway/modem used at the mouth of your network will prevent incoming connections from reaching your computer anyway, at least from the internet.

---

### Post by winjeel on 2011-10-31
Thanks for the reply. It's not an office network, it's a home network, so no big brother computer system between each computer and the big wide world.

I have set the inbound traffic to allow the printer and it's port, but still doesn't work.

---

### Post by 3rdalbum on 2011-10-31
Even a home network has a router that acts as a firewall.

Disable your Firestarter firewall and go to this site: [https://www.grc.com/x/ne.dll?rh1dkyd2](https://www.grc.com/x/ne.dll?rh1dkyd2)

Click on the "Common Ports" button.

If you have a firewall in your router, then the test will pass with "Stealth". If you don't have a firewall, then the test will probably pass with all ports "Closed".*

If you already have a firewall in your router, then there's absolutely no point having one running on your computer too, if you're on a home network where you can trust every computer running on it.

*Yes; even without a firewall, your computer probably won't respond on any common ports anyway. It only will if there's a program specifically listening for incoming connections on a specific port.

---

### Post by winjeel on 2011-11-01
With and without FireStarter enabled I got the same list of messages for all but one port:
> [FONT=Verdana,Arial,Helvetica,Sans-Serif,MS Sans Serif][SIZE=1][COLOR=#000060]Your computer has responded that this port exists but is currently closed to connections.[/COLOR][/SIZE][/FONT]

The printer port even responded

---

### Post by winjeel on 2011-11-02
Help?

---

### Post by Tenis Altos on 2012-03-17
Everyone knows that the firewall in the router is there to protect the LAN from a WAN attacks, and the firewall on the machine is to protect from LAN attacks. After all who knows what might have gotten into your room mate's computer.

3rdalbum, winjeel did not say his firewall was in a default state. If you are printing to the network printer how a blocked incomming port would prevent it? So winjeel you are backing at the right tree.

I had the same problem of not being able to print to a network printer and when I disable Firestarter it would print just fine. I do too block every incoming port and allow, in the white list of Firestarter, selective ports to communicate out. I have a Brother HL-2070N on the network. I had to allow port 515 and it worked right away.

Thank you...

---

### Post by davidvandoren on 2012-03-17
firestarter is no longer maintained.

you don't have to use any frontend for ufw to work.

Just type into the terminal to activate your firewall.
```
sudo ufw enable
```

Then open the port 631 for your printer.

```
sudo ufw allow 631
```

Or you can create a launcher on your desktop with the following to open the port for printing.
```
gnome-terminal -x bash -c "sudo ufw allow 631"
```

and this one to disable printing by closing the port.
```
gnome-terminal -x bash -c "sudo ufw deny 631"
```

---

