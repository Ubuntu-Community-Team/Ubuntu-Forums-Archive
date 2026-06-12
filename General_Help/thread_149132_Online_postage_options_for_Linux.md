---
title: "Online postage options for Linux?"
date: 2006-03-23
forum: General Help
---

### Post by illiterate_light on 2006-03-23
I just switched my main desktop over to Linux (Ubuntu 5.10) from Windows, and the only real problem I have left is that I can't find a way to print USPS postage with Linux.  I run a small business, so this is pretty crucial.  I was using Endicia on Windows, and tried to run it through Wine, and made some progress -- I can make the app itself run, configure labels, etc., but when it tries to authenticate my account by communicating with Endicia servers, I get this error:

Error 0x80090003 during RSA encryption.  The hKey parameter does not contain a valid handle to a key.

Anyone have a clue how to fix this?  Any help would be greatly appreciated.

---

### Post by dragonfyre13 on 2006-03-23
You may want to try the crossover office trial. See if it works, as I have had better luck with that, so far as office applications go.

---

### Post by illiterate_light on 2006-03-23
Thanks for the tip -- that actually looks pretty cool, but I tried it and had no luck with the software I'm working with (which is called "Dazzle").

I went through the installation process using crossover office, it created a shortcut to Dazzle, but when I try to launch it, nothing happens -- it just goes silent, no errors or anything.  When I launched it previously with Wine, it would open up the app, but then failed only when it tried to make an encrypted connection with Endicia servers.  The new installation through crossover office won't open the app at all, unless there's something I don't know about launching unsupported apps through cxoffice.

Any other ideas?

---

### Post by rhomsy on 2006-03-23
[QUOTE=illiterate_light]Thanks for the tip -- that actually looks pretty cool, but I tried it and had no luck with the software I'm working with (which is called "Dazzle").

I went through the installation process using crossover office, it created a shortcut to Dazzle, but when I try to launch it, nothing happens -- it just goes silent, no errors or anything.  When I launched it previously with Wine, it would open up the app, but then failed only when it tried to make an encrypted connection with Endicia servers.  The new installation through crossover office won't open the app at all, unless there's something I don't know about launching unsupported apps through cxoffice.

Any other ideas?[/QUOTE]

I'm still new to this, but maybe you need to uninstall wine before you install cross-over.

---

### Post by illiterate_light on 2006-03-23
Ok, I tried uninstalling Wine, then uninstalling Crossover Office, then re-installed Crossover Office, then re-installed Dazzle, but it still does the same thing.... any other ideas?

---

### Post by rhomsy on 2006-03-23
[QUOTE=illiterate_light]Ok, I tried uninstalling Wine, then uninstalling Crossover Office, then re-installed Crossover Office, then re-installed Dazzle, but it still does the same thing.... any other ideas?[/QUOTE]

Crossover and Wine are different and may exhibit errors differently.  Launch it from the terminal and see what error spits out.  You may be SOL with using Dazzle this way, and you may need to bite the bullet and go with VMware.

---

### Post by towsonu2003 on 2006-03-23
if you start considering vmware, first consider qemu (with kqemu acceleration, compilation required, easy bc there is a howto in the forum). these two will emulate Windows under Linux (run Win under Lin) like a regular program. difference: qemu is free & open source. printer configuration may be a little hard under qemu - I use pdf printer in windows and print the stuff in Linux -if that helps. You can always try to configure printer under qemu, I just never tried.

---

### Post by illiterate_light on 2006-03-23
[QUOTE=towsonu2003]if you start considering vmware, first consider qemu (with kqemu acceleration, compilation required, easy bc there is a howto in the forum).[/QUOTE]

Wow, thanks for the tip -- qemu is awesome.  I just got XP up and running within qemu, which is pretty huge.  Only problem is, I haven't been able to establish a network connection from within that virtual OS.  I guess this is because an IP address is already assigned to the same network card in the base OS, so it can't assign two IPs to the same MAC address.  I think?  Any clues on that?  I'll dig around some more too.

Thanks again -- after a little troubleshooting to get it compiled, qemu is really cool.

---

### Post by illiterate_light on 2006-03-23
Wow, just to follow up, I'm amazed at the progress I've been able to make --

I just found an IP masquerading wrapper script that allows the virtual OS running in Qemu to receive an IP address from the host OS, while it runs on top of it.  And then I was able to connect to the printer configured as a shared printer on the Ubuntu host, and I'm already printing postage via the same Windows software, running in XP as a sub-OS, but with Linux as my host OS.

I don't know if Linux has just come this far since the last time I worked with it or what, but being able to do this has pretty much sealed the deal for me to be able to leave Windows behind (edit: at least as a host OS, which is my immediate goal).  Thanks again for the help -- I'm very stoked.

---

### Post by dragonfyre13 on 2006-03-27
I actually had to go the same way with Lightscribe. Once K3b adopts it, that will be immensly helpful, but for now, I have to run VMWare to be able to burn lighscribe labels.

---

