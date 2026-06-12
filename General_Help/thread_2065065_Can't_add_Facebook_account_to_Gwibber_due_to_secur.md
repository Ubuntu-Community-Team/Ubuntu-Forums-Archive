---
title: "Can't add Facebook account to Gwibber due to security warning"
date: 2012-10-01
forum: General Help
---

### Post by luctor on 2012-10-01
When I try to add my Facebook account to Gwibber I get the following message and although it says "Succes" my Facebook account isn't added to Gwibber.

> Succes
SECURITY WARNING: The above URL is NOT NOT VALID FOR A CASH CARD OR GIFT CARD. Giving away the URL may result in your account being HIJACKED.

[IMG]http://i.imm.io/GhfE.png[/IMG]

---

### Post by stepking2 on 2012-10-01
Have you tried reinstalling Gwibber?
```
sudo apt-get purge gwibber
sudo apt-get install gwibber
```

Have you tried logging in with Pidgin?

---

### Post by lunalui on 2012-10-01
Hi, I've got the very same problem since yesterday, after upgrading to Precise pangolin from Lucid.
The problem persists after reinstalling gwibber as suggested.
I seem to be able to login with Pidgin.
thanks

---

### Post by daslinkard on 2012-10-01
You should be able to purge Gwibber

```
sudo apt-get purge gwibber
```

and then install the following ppa
```
sudo add-apt-repository ppa:gwibber/daily
```

Then run your update
```

sudo apt-get update
```

Reboot your machine and see if this fixes the issue for you?

---

### Post by lunalui on 2012-10-01
Hi,
thanks for your reply. I did purge gwibber when I reinstalled it yesterday.
Unfortunately I cannot add the repository you suggest for I get the following error message:

> Cannot access PPA ([https://launchpad.net/api/1.0/~gwibber/+archive/daily](https://launchpad.net/api/1.0/~gwibber/+archive/daily)) to get PPA information, please check your internet connection.

although my internet connection is up and running.

---

### Post by sandyd on 2012-10-01
small typo
```
sudo apt-add-repository ppa:gwibber-daily/ppa
```

---

### Post by lunalui on 2012-10-01
I tried what you suggest, but nothing changes :sad:

PS I reinstalled before restarting: maybe I should have restarted before reinstalling?

---

### Post by lunalui on 2012-10-02
PS I also tried to remove the gwibber application on facebook, purge gwibber and reinstall. I could access facebook from gwibber, but when granting permissions to the gwibber application at the very end I got again the same message....

---

### Post by a3dbox on 2012-10-02
Having the same issues here.. :(

Fresh install of Ubuntu 12.04 with all updates yesterday and getting exactly the same error.

Reading on another forum someone was saying that its the fault of the Facebook API and Gwibber not having enough request allocation on Facebook since its got so popular.  Don't know how true this is though...  

Either way very annoying.  Any updates appreciated.

---

### Post by lunalui on 2012-10-03
UPDATE 
the message has changed: now it onlt says success, but facebook is not added.
Also the gwibber application page could not be loaded on facebook (not sure there's a relation though)

---

### Post by lunalui on 2012-10-12
looks like the bug has been acknowledged 
[https://bugs.launchpad.net/ubuntu/+source/gwibber/+bug/1058672](https://bugs.launchpad.net/ubuntu/+source/gwibber/+bug/1058672)

---

