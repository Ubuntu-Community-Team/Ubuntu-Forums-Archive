---
title: "Why is Ubuntu constantly rewriting my /etc/hosts file?"
date: 2010-10-14
forum: General Help
---

### Post by Dave M G on 2010-10-14
Ubuntu Users,

On my main desktop machine I run a LAMP server that is not connected to the internet, it's just for testing web sites locally.

Since upgrading to Ubuntu 10.10, my /etc/hosts on my local testing
machine keeps getting wiped out.

After the first time I noticed it happening, I thought, "okay, fine, must have been over written during the upgrade". So I put back in what I had before.

Then later, my local web sites weren't working again, and it turned out
my /etc/hosts got wiped out again. Maybe after a boot.

So it looks like when Apache starts up, it generates /etc/hosts, or
something, and I need to put my list of domains in some other file... or
something.

I figured I'd go to the Apache web site to see what's up, but it seems like this isn't something Apache does.

My local LUG has suggested that this behaviour is particular to Ubuntu and it's network management "features".

Does anyone know if this is something Ubuntu is doing?

And in any case, does anyone know how I get my /etc/hosts file to not be rewritten every time Apache starts?

Thank you for any advice.

---

### Post by ac14112 on 2010-10-14
I had a similar problem with a different cause, but to make a long story short, I changed the permissions on the /etc/hosts file to read only. If you don't know how to do this, run the command:

```
sudo chmod 444 /etc/hosts
```

To restore the write permissions, run the command:

```
sudo chmod 644 /etc/hosts
```

---

### Post by 3Miro on 2010-10-14
> **Dave M G said:**
> ... network management "features".

The means that you are not supposed to edit the file yourself. You have to use the network manager or some other file/software to make your settings. I am not sure which or where.

---

### Post by ac14112 on 2010-10-14
> **3Miro said:**
> The means that you are not supposed to edit the file yourself. You have to use the network manager or some other file/software to make your settings. I am not sure which or where.

This is not true for the hosts file. I use custom entries in the hosts file and I use Network Manager on many different machines and I've never had a problem. There are some files related to networking that you should not edit, but hosts isn't one of them.

---

### Post by The Cog on 2010-10-14
You might try killing the avahi-daemon process. Or uninstalling it completely - I have never found anything useful it does, but have found that it sometimes does things I don't want. It makes every incoming connection take several seconds to complete, rendering the PC useless as a web server, for instance. Very microsoft-like.

---

### Post by Dave M G on 2010-10-14
Thanks to everyone for responding.

While I could change the permissions or use chattr to prevent the /etc/hosts from being altered, I'd rather know what is actually going on.

Is there no one who can say for sure what exactly is happening?

Or at least confirm if it is in fact some Ubuntu "feature" that is responsible for this, and not some other bug? I have two computers on which this is happening, but there is always the chance I have got some setting wrong.

I looked up avahi-daemon, but I have not yet found any specific mention of it altering /etc/hosts.

---

### Post by emas80 on 2010-10-18
Hi, I've the same problem, and I can confirm that it is a "feature" of the last Ubuntu Maverick because until last week everything worked as expected.

I don't know if it is something related to apache rewriting the file (why should apache do this??) or, probably, something someone put somewhere in ubuntu (why should someone do this?!?).

It's very annoying, a linux system should NOT do something itself, it's the basic difference between linux and windows, why can't I modify my damn host file? 

I'll start doing a research about this behaviour.

**edit**: just an update, it seems that this is the only thread referring to this problem on the internet. In my hosts file I read "#Added by Network Manager" after my ip-address and my hostname. I get an IP from a DHCP server, so probably Network Manager decides to update hosts file with my ip address, and then it removes my modification by resetting the file to its "copy": it's not an empty host file, but simply the version that it found the first boot after the dist-upgrade (because I modify frequently hosts file as I'm a web programmer, and my hosts file was already customised). I will open a ticket on launchpad.

---

### Post by crahan on 2010-10-19
Looks like it's network-manager that's responsible.
 
I was able to reproduce the problem by editing /etc/hosts (and removing the '::1 localhost6.localdomain localhost6' line) and then restarting network-manager (sudo /etc/init.d/network-manager restart)  When you check /etc/hosts you'll notice that the offending line is back.

I've disabled ipv6 through /etc/sysctl.conf
I've also checked all the interfaces in the network-manager GUI in Gnome to see if ipv6 was set to 'ignore' and they all are.  Yet when you restart network-manager it still goes and adds ipv6 specific lines to /etc/hosts

A bug perhaps?

---

### Post by dcstar on 2010-10-20
> **crahan said:**
> Looks like it's network-manager that's responsible.
 
I was able to reproduce the problem by editing /etc/hosts (and removing the '::1 localhost6.localdomain localhost6' line) and then restarting network-manager (sudo /etc/init.d/network-manager restart)  When you check /etc/hosts you'll notice that the offending line is back.

I've disabled ipv6 through /etc/sysctl.conf
I've also checked all the interfaces in the network-manager GUI in Gnome to see if ipv6 was set to 'ignore' and they all are.  Yet when you restart network-manager it still goes and adds ipv6 specific lines to /etc/hosts

A bug perhaps?
This does not happen in my 10.04 system with IPv6 set to "Ignore" in my Network Manager, nothing whatsoever happens to my hosts file when I restart it.

Anyone using DHCP should realise that the DHCP server will always change the hosts file because of the data in the DHCP configuration packet.

---

### Post by florinn on 2010-10-20
I am using Ubuntu Maverick for 10 days now and the overwriting of the hosts file happened to me only twice, not after every reboot but I think after I changed the networks (connected to another wireless network).
Strange behaviour indeed, I have to find a solution. I did not have this problem in any other Ubuntu previous version.

---

### Post by SeijiSensei on 2010-10-20
Could one of you with this problem please post a bug at Launchpad?  This is clearly not the correct behavior.

I don't seem to have this problem in Kubuntu 10.10, by the way.  I just added a custom entry to /etc/hosts, restarted my network connection, and the file is unchanged.

---

### Post by florinn on 2010-10-20
it seems that someone already reported this bug to launchpad
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/663397](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/663397)

---

### Post by Dave M G on 2010-10-23
As long as it is a confirmed bug and a fix is on the way, I'm content to wait for the update. In the bug report it says the fix is upstream and in the queue to get distributed.
 
I was just worried that there was some new "feature" or change in how configurations were done that would impose a new way of managing virtual hosts.

Mistakes I can handle. Arbitrary changes can be harder to swallow.

---

### Post by out_of_time on 2010-11-17
FYI, the bug recommends a workaround that worked for me -- use a different loopback address that doesn't start with 127.0 -- e.g., 127.1.0.0

---

