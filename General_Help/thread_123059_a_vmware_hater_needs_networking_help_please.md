---
title: "a vmware hater needs networking help please"
date: 2006-01-29
forum: General Help
---

### Post by danf_1979 on 2006-01-29
Hi to you all:
I'm having some annoying (terribly annoying) problems with my vmware. I DONT have ANY kind of networking. I cant communicate Linux host with Window's guest.

I have re-runned sometimes already vmware-config.pl. Here is the output:
```

Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                   done
   Host-only networking on /dev/vmnet1 (background)                    done
   Bridged networking on /dev/vmnet2                                   done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                          done

```
But no matter what I select on the configuration I never get to have a functional network. No internet in guest, and I cant ping any of the host IP. Anyway, the host is OK.
For example, when I select bridged networking on /dev/vmnet0, Windows loads up and I get "Status: Limited or no conectivity" on the network icon. The same happens with NAT.
When selecting host only, then I dont get the Limited or no conectivity message, but I cant ping any of the host IP.

Till now, I hate vmware.

Is there something I'm missing? I did install vmware with network support and re-installed and re-configured to make sure the right config is installed. Then I selected the config I wanted to use in vmware (bridged or NAT) and executed the guest. No network though. Is there something I'm missing?

---

### Post by otey on 2006-01-29
Are you on a local network (via. a router or whatever it's called)?

If you are, it should be working if you select briged network in the vmware ethernet menu. 
Then make sure that your guest OS is connecting with automatic ip.

---

### Post by MartinG on 2006-01-29
Which version of VMWare are you running?  If less than 5.5 then the first thing I'd try is to update to the latest version, 5.5.1.  Updates from 5.0 are free.

If you're using 4.5 or earlier, or the above doesn't work, then try this (no guarantees):
Remove VMWare, then download the latest any-any patch ([http://ftp.cvut.cz/vmware/vmware-any-any-update96.tar.gz)](http://ftp.cvut.cz/vmware/vmware-any-any-update96.tar.gz)), then re-install vmware using the patch.

(to do this, run the patch "runme.pl" *before* running vmware.config.pl).

If it still doesn't work you need to explore further your network.  Is the router acting as a DHCP server? Will it accept other connections? Is your Guest OS (Windows) configured for automatic ip? What if you configure Windows for a fixed address (within the range the router will accept, obviously)?  Is a firewall somewhere blocking things?  (It's sometimes helpful when troubleshooting to disconnect from the internet to isolate the network, and then turn off *all* firewalls and other security software.)

EDIT:
Sorry, the above is a bit misleading.  You need VMWare installed, but not configured, when you run the patch's runme.pl.

---

