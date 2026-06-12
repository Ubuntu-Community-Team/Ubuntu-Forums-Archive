---
title: "KDEwallet requires password on startup"
date: 2010-09-09
forum: General Help
---

### Post by jurco on 2010-09-09
Hi Guys. I have successfully Kubuntu 10.04 running with Belking wireless USB adapter. There is only one issue.

I use WPA2 key to access my home wifi and after being connected I was asked if kdewallet should remember the password. I clicked yes.

Now evertime my computer starts after booting to Kubuntu I have to enter my kdewallet password in order Network Manager can retrieve password from kdewallet.

Is it possible to to use kdewallet without password?

Or how can I connect to my access point with WPA on startup?

Thanks

---

### Post by ankspo71 on 2010-09-10
Hi,
If you allow wireless access to all users, the password prompt at startup should go away.

See the second and third posts on this link:
[http://forums.linuxmint.com/viewtopic.php?f=109&t=42322&start=0](http://forums.linuxmint.com/viewtopic.php?f=109&t=42322&start=0)

---

### Post by jurco on 2010-09-11
But there is not an option to allow the connection for all users.
There is only "Connect automatically" which is checked and "System connection" which is not checked and is greyed out (read only).
I assume enabling this would help. But it is read only.
I found a thread to bypass this by installing gnome network manager but I didnt manage to run it on startup instad of KNetworkManager.

---

### Post by ankspo71 on 2010-09-11
Hi Again,
Right click on your KNetworkManager icon, then select Network Management Settings. When the window opens, click on the "Other" category on the left side. Then click the "Connection Secrets" tab. Choose Store Connection Secrets: -> "In File (Unencrypted)". It will probably ask for your password again only to confirm the operation. This should work and not ask you for your password again on startup. (My wireless doesn't work in Maverick-Beta to be able to test this though.)

That link I gave you before might have been for Gnome network manager that apparently replaced Knetworkmanger in LinuxMint8. Sorry about that. 

If you would like to use Gnome's network manager instead of Knetworkmanager, here is a link that shows how to do that: [http://digitizor.com/2010/05/21/how-to-replace-the-kde-network-manager-with-the-gnome-network-manager-in-ubuntu/](http://digitizor.com/2010/05/21/how-to-replace-the-kde-network-manager-with-the-gnome-network-manager-in-ubuntu/)
Hope this helps.

---

### Post by jurco on 2010-09-11
Cool, that helped! Thanks a lot!

---

