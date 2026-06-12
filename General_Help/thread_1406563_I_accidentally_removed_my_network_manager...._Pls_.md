---
title: "I accidentally removed my network manager.... Pls help!"
date: 2010-02-14
forum: General Help
---

### Post by scar1 on 2010-02-14
Hi,

I had an issue recently where some of my repositories could not be found and searched on this forum for a fix to understand what needed to be changed. I found the thread below and followed some advice as posted.

[http://ubuntuforums.org/showthread.php?t=339975](http://ubuntuforums.org/showthread.php?t=339975)

sudo rm -f /var/lib/dpkg/info/wpasupplicant.postrm
wget [http://3v1n0.tuxfamily.org/pool/edgy/3v1n0/wpasupplicant_0.5.7+3v1ubuntu3_i386.deb](http://3v1n0.tuxfamily.org/pool/edgy/3v1n0/wpasupplicant_0.5.7+3v1ubuntu3_i386.deb)
sudo dpkg -i wpasupplicant_0.5.7+3v1ubuntu3_i386.deb
sudo rm -f /var/lib/dpkg/info/wpasupplicant.postrm
sudo apt-get remove wpasupplicant
sudo apt-get update
Whilst doing this I now understand that my network manager (gnome) was removed. I now have no network connectivity on this box.

Can anyone help me reinstall this please?
Im thinking I may have to reinstall my network card from a terminal but cannot be sure, it might just be gnome which cannot see any network devices.
Sorry if my terminology is incorrect, I am still pretty green with ubuntu and Unix....

Thanks in advance for any help!

Cheers
Scar

---

### Post by SPr on 2010-02-14
Do you still have an ethernet connection? If so
```

apt-get update
dpkg -r wpasupplicant
apt-get reinstall gnome-network-admin
apt-get install wpasupplicant

```

The repositories "not working" could be a problem with the repo server rather than your PC.

Edit:
The commands need to be prefixed by sudo. Sorry, I'm used to working in a root terminal.

You may have to try
```

wget http://3v1n0.tuxfamily.org/pool/edgy...untu3_i386.deb
sudo dpkg -i wpasupplicant_0.5.7+3v1ubuntu3_i386.deb

```
if the above fails because the wpasupplicant postrm file is missing then repeat the first steps.

The advice in that post was bad. TBH, I'm surprised it worked for anybody.

---

### Post by scar1 on 2010-02-14
Thanks for your quick response here, appreciated.
I will give it a try, I have tried to ping the machine and it just times out. Also checked my router DHCP client list so don't think my box has any network activity.

Will give it a try now and respond.

Cheers again
Scar1

---

### Post by sophicsage on 2010-02-14
> **scar1 said:**
> Thanks for your quick response here, appreciated.
I will give it a try, I have tried to ping the machine and it just times out. Also checked my router DHCP client list so don't think my box has any network activity.

Will give it a try now and respond.

Cheers again
Scar1

Oh, I did the same thing two weeks ago.  I was downloading another wifi manager and somehow that erased my original network manager and I have YET to get it back.  I installed Wicd Network Manager and now I've got a good connection back.  It's a little more processing to get it started than the original one, but now my wifi signal is stronger somehow.  I'd suggest that.

---

### Post by nothingspecial on 2010-02-14
With your ethernet cable plugged in
```

sudo ifconfig eth0 up
sudo dhclient
```

Then try the downloads again.

---

### Post by scar1 on 2010-02-14
Hi,

Thanks for all your help here. With information provided i managed to get back online. Follow in the instructions and then in synaptic manager updated the network manager also there. Now have my icon back for networking as it was before.

Cheers again
Scar1

---

