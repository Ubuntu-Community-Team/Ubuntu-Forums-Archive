---
title: "HOWTO: Fix GPG errors for bad/deleted keys"
date: 2009-07-23
forum: General Help
---

### Post by altonbr on 2009-07-23
I don't know what I did, but one day I started using Ubuntu and all my public signature keys for downloading software were all deleted.

This error popped up after running "System > Administration > Update Manager"
> W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY **40976EAF437D05B5**
W: GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY **DCF9F87B6DFBCBAE**
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY **2EBC26B60C5A2783**
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY **40976EAF437D05B5**
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY **40976EAF437D05B5**
W: GPG error: [http://archive.getdeb.net](http://archive.getdeb.net) jaunty-getdeb-testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY **A8A515F046D7E7CF**
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY **40976EAF437D05B5**
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY **6E871C4A881574DE**
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY **28A8205077558DD0**
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY **D739676F7613768D**
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY **8C851674F96FD737**
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY **C0B56813051D8B58**
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY **4874D3686E80C6B7**
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY **60D11217247D1CFF**
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-backports Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY **40976EAF437D05B5**
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY **5A9A06AEF9CB8DB0**
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY **6D975C4791E7EE5E**
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY **5A9BF3BB4E5E17B5**

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY **7FB8BEE0A1F196A8**
W: Failed to fetch [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/dists/jaunty/Release](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/dists/jaunty/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.


The fix for this is to re-download the keys using the hexidecimal numbers given in the error (I bolded them above).

NOTE: Your hexadecimal numbers may be different then mine, so make sure to use the hexadecimals numbers in your error, not mine.

Type this command into the terminal ("Applications > Accessories > Terminal")
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys
```

And then add the hexadecimal numbers to the command (again, these are my keys from my error. Make sure to use your own):
> sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5 DCF9F87B6DFBCBAE 2EBC26B60C5A2783 A8A515F046D7E7CF 6E871C4A881574DE 28A8205077558DD0 D739676F7613768D 8C851674F96FD737 C0B56813051D8B58 4874D3686E80C6B7  60D11217247D1CFF 5A9A06AEF9CB8DB0 6D975C4791E7EE5E 5A9BF3BB4E5E17B5 7FB8BEE0A1F196A8

The output should look like this:
> gpg: requesting key 437D05B5 from hkp server keyserver.ubuntu.com
gpg: requesting key 6DFBCBAE from hkp server keyserver.ubuntu.com
gpg: requesting key 0C5A2783 from hkp server keyserver.ubuntu.com
gpg: requesting key 46D7E7CF from hkp server keyserver.ubuntu.com
gpg: requesting key 881574DE from hkp server keyserver.ubuntu.com
gpg: requesting key 77558DD0 from hkp server keyserver.ubuntu.com
gpg: requesting key 7613768D from hkp server keyserver.ubuntu.com
gpg: requesting key F96FD737 from hkp server keyserver.ubuntu.com
gpg: requesting key 051D8B58 from hkp server keyserver.ubuntu.com
gpg: requesting key 6E80C6B7 from hkp server keyserver.ubuntu.com
gpg: requesting key 247D1CFF from hkp server keyserver.ubuntu.com
gpg: requesting key F9CB8DB0 from hkp server keyserver.ubuntu.com
gpg: requesting key 91E7EE5E from hkp server keyserver.ubuntu.com
gpg: requesting key 4E5E17B5 from hkp server keyserver.ubuntu.com
gpg: requesting key A1F196A8 from hkp server keyserver.ubuntu.com
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: key 6DFBCBAE: public key "Sun Microsystems, Inc. (xVM VirtualBox archive signing key) <info@virtualbox.org>" imported
gpg: key 0C5A2783: public key "Medibuntu Packaging Team <admin@lists.medibuntu.org>" imported
gpg: key 46D7E7CF: public key "GetDeb Archive Automatic Signing Key <archive@getdeb.net>" imported
gpg: key 881574DE: public key "Launchpad PPA for Bisigi" imported
gpg: key 77558DD0: public key "Launchpad PPA for GNOME Do Core Team" imported
gpg: key 7613768D: public key "Launchpad PPA named vlc for Christoph Korn" imported
gpg: key F96FD737: public key "Launchpad PPA for Paul Gevers" imported
gpg: key 051D8B58: public key "Launchpad PPA for GStreamer developers" imported
gpg: key 6E80C6B7: public key "Launchpad PPA for Banshee Team" imported
gpg: key 247D1CFF: public key "Launchpad PPA for OpenOffice.org Scribblers" imported
gpg: key F9CB8DB0: public key "Launchpad PPA for Ubuntu Wine Team" imported
gpg: key 91E7EE5E: public key "Launchpad PPA for XBMC for Linux" imported
gpg: key 4E5E17B5: public key "Launchpad PPA for chromium-daily" imported
gpg: key A1F196A8: public key "Launchpad PPA for Pidgin Developers" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 15
gpg:               imported: 14  (RSA: 12)
gpg:              unchanged: 1

Then you should have no more errors!

---

### Post by ubername on 2009-08-18
> **altonbr said:**
> I don't know what I did, but one day I started using Ubuntu and all my public signature keys for downloading software were all deleted.

This error popped up after running "System > Administration > Update Manager"


The fix for this is to re-download the keys using the hexidecimal numbers given in the error (I bolded them above).

NOTE: Your hexadecimal numbers may be different then mine, so make sure to use the hexadecimals numbers in your error, not mine.

Type this command into the terminal ("Applications > Accessories > Terminal")
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys
```

And then add the hexadecimal numbers to the command (again, these are my keys from my error. Make sure to use your own):


The output should look like this:


Then you should have no more errors!

Thanks, helped me fix after I deleted my jaunty keys.

---

### Post by ben2talk on 2009-11-05
I'm doing this with Karmic.

I imported the key, but am stuck with 'BADSIG 40976EAF437D05B5'

This wasn't fixed by re-importing the key!

---

### Post by altonbr on 2009-11-05
> **ben2talk said:**
> I'm doing this with Karmic.

I imported the key, but am stuck with 'BADSIG 40976EAF437D05B5'

This wasn't fixed by re-importing the key!
Here's a little tutorial that you might find useful: [http://www.drewwithers.com/content/how-fix-ubuntu-gpg-error-badsig](http://www.drewwithers.com/content/how-fix-ubuntu-gpg-error-badsig)

---

### Post by Inherentwired1 on 2009-12-06
I have heard that this key loss thing is happening a lot when upgrading to 9.10, Being new to Ubuntu, I was really glad to find this fix because it works perfectly. Thank You! I'm really getting impressed with this Linux stuff.....

---

### Post by apurvaagarwal87 on 2010-01-16
This is the new address for the blog site to fix the error

[http://www.drewwithers.com/2009/12/how-to-fix-ubuntu-gpg-error-badsig.html](http://www.drewwithers.com/2009/12/how-to-fix-ubuntu-gpg-error-badsig.html)

---

### Post by smokeit on 2010-01-29
Worked great!  Thanks

---

### Post by cosmophobia on 2010-03-19
First, thank you for the good thread. Secondly, the command could be used also if you don't have any imported key. I succeed to import wine key to my repositories.
Thanks again man !

---

### Post by mmosier1 on 2010-04-05
> **altonbr said:**
> I don't know what I did, but one day I started using Ubuntu and all my public signature keys for downloading software were all deleted.

This error popped up after running "System > Administration > Update Manager"


The fix for this is to re-download the keys using the hexidecimal numbers given in the error (I bolded them above).

NOTE: Your hexadecimal numbers may be different then mine, so make sure to use the hexadecimals numbers in your error, not mine.

Type this command into the terminal ("Applications > Accessories > Terminal")
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys
```And then add the hexadecimal numbers to the command (again, these are my keys from my error. Make sure to use your own):


The output should look like this:


Then you should have no more errors! 

I have a similar problem. When I ran the command as you described, here is what I got:

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
gpg: requesting key 437D05B5 from hkp server keyserver.ubuntu.com
gpg: [don't know]: invalid packet (ctb=2f)
gpg: keydb_get_keyblock failed: eof
gpg: [don't know]: invalid packet (ctb=2f)
gpg: /etc/apt/trusted.gpg: copy to `/etc/apt/trusted.gpg.tmp' failed: invalid packet
gpg: error writing keyring `/etc/apt/trusted.gpg': invalid packet
gpg: [don't know]: invalid packet (ctb=2f)
gpg: keydb_search failed: invalid packet
gpg: key 437D05B5: public key "[User ID not found]" imported
gpg: error reading `[stream]': invalid packet
gpg: Total number processed: 0
gpg:               imported: 1

Any idea what's going on here and how to fix it?

Thanks

mm

---

### Post by Grakul on 2010-04-11
Thanks a bunch! I was getting these errors on Karmic, after updating Mythbuntu through auto-builds.

After running the command to re-import the keys, I can now actually believe it when it says there are no updates available! ;)

---

### Post by FirstByté on 2010-05-19
> **altonbr said:**
> I
***[...]***
This error popped up after running "System > Administration > Update Manager"


The fix for this is to re-download the keys using the hexidecimal numbers given in the error (I bolded them above).

***[...]***
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys
```

And then add the hexadecimal numbers to the command (again, these are my keys from my error. Make sure to use your own):

***[...]***
Then you should have no more errors!


This charm fixed my VirtualBox miraculous key problem :D

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys XXXXXXkeyIDXXXXX
```

Thanks man!!! You ROCK solid


How about some caramel of Popcorn and a flask of Cream Ubuntu for you ;)

:popcorn: :-({|= :guitar:

Share the 'bunts!

---

### Post by progone on 2010-06-01
> **mmosier1 said:**
> I have a similar problem. When I ran the command as you described, here is what I got:

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
gpg: requesting key 437D05B5 from hkp server keyserver.ubuntu.com
gpg: [don't know]: invalid packet (ctb=2f)
gpg: keydb_get_keyblock failed: eof
gpg: [don't know]: invalid packet (ctb=2f)
gpg: /etc/apt/trusted.gpg: copy to `/etc/apt/trusted.gpg.tmp' failed: invalid packet
gpg: error writing keyring `/etc/apt/trusted.gpg': invalid packet
gpg: [don't know]: invalid packet (ctb=2f)
gpg: keydb_search failed: invalid packet
gpg: key 437D05B5: public key "[User ID not found]" imported
gpg: error reading `[stream]': invalid packet
gpg: Total number processed: 0
gpg:               imported: 1

Any idea what's going on here and how to fix it?

Thanks

mm

I am having a similar issue as you.  I lost Nautilus a few weeks ago.  I followed instructions to get it up Nautilus and Lucid up and running again.

However, old files are now encrypted.

When I type in:

        ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys

```


The outcome is: ```
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys

```

As you can see, my old  key isn't here.  What do I need to do because not being able to update Lucid is a pain. 

```
W: GPG error: http://ppa.launchpad.net lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7889D725DA6DEEAA
```

---

### Post by progone on 2010-06-01
someone else having the same issue

[http://ubuntuforums.org/showthread.php?p=9392487#post9392487](http://ubuntuforums.org/showthread.php?p=9392487#post9392487)

[https://bugs.launchpad.net/ecryptfs/+bug/588152](https://bugs.launchpad.net/ecryptfs/+bug/588152)

---

### Post by altonbr on 2010-06-01
> **progone said:**
> I am having a similar issue as you.  I lost Nautilus a few weeks ago.  I followed instructions to get it up Nautilus and Lucid up and running again.

However, old files are now encrypted.

When I type in:

        ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys

```
The outcome is: ```
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys

```As you can see, my old  key isn't here.  What do I need to do because not being able to update Lucid is a pain. 

```
W: GPG error: http://ppa.launchpad.net lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7889D725DA6DEEAA
```
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 7889D725DA6DEEAA
```

---

### Post by night1727 on 2010-06-07
[B]I get this output:(
[/B]
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 5A9A06AEF9CB8DB0
gpg: requesting key F9CB8DB0 from hkp server keyserver.ubuntu.com
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
keith@keith-desktop:~$

---

### Post by altonbr on 2010-06-07
> **night1727 said:**
> [B]I get this output:(
[/B]
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 5A9A06AEF9CB8DB0
gpg: requesting key F9CB8DB0 from hkp server keyserver.ubuntu.com
**gpgkeys: HTTP fetch error 7: couldn't connect to host**
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
keith@keith-desktop:~$
Are you running this from the same computer you're posting from? Because it says you can't connect to the keyserver. Maybe it was down at the time you tried? Or you're putting in the wrong key to retrieve.

---

### Post by Jimmeh! on 2010-06-11
The instructions in the first post imported the outstanding keys so it's not complaining at me constantly about untrusted packages. Thanks very much for taking the time to document the solution :)

---

### Post by habana on 2010-06-15
The OP's instructions worked perfectly for me. Thank you!

---

### Post by altonbr on 2010-06-16
> **Jimmeh! said:**
> The instructions in the first post imported the outstanding keys so it's not complaining at me constantly about untrusted packages. Thanks very much for taking the time to document the solution :)

> **habana said:**
> The OP's instructions worked perfectly for me. Thank you!

Thanks everyone, I now added the tutorial on my blog too: [http://blog.brettalton.com/2010/06/16/fix-gpg-errors-for-baddeleted-keys/](http://blog.brettalton.com/2010/06/16/fix-gpg-errors-for-baddeleted-keys/)

---

### Post by Thatlinuxguy on 2010-06-21
So far none of those have worked for me this is what I get when I try to update

```
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://dl.google.com stable Release: Unknown error executing gpgv

W: GPG error: http://archive.canonical.com lucid Release: Unknown error executing gpgv
W: GPG error: http://archive.canonical.com lucid Release: Unknown error executing gpgv
W: GPG error: http://ppa.launchpad.net lucid Release: Unknown error executing gpgv
W: GPG error: http://ppa.launchpad.net lucid Release: Unknown error executing gpgv
W: GPG error: http://ppa.launchpad.net lucid Release: Unknown error executing gpgv
W: GPG error: http://us.archive.ubuntu.com lucid Release: Unknown error executing gpgv
W: GPG error: http://us.archive.ubuntu.com lucid-updates Release: Unknown error executing gpgv
W: GPG error: http://us.archive.ubuntu.com lucid-backports Release: Unknown error executing gpgv
W: GPG error: http://security.ubuntu.com lucid-security Release: Unknown error executing gpgv
W: Failed to fetch http://dl.google.com/linux/deb/dists/stable/Release  

W: Failed to fetch http://ppa.launchpad.net/merlwiz79/aurora/ubuntu/dists/lucid/main/binary-i386/Packages.gz  404  Not Found

W: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by returnofnights on 2010-06-22
Seems the keyserver is still down 11 hours later, this must be a yoyo server, goes up and down all the time.

Hope it comes back soon, I am working on some projects and need the keys for the repositories.

---

### Post by altonbr on 2010-06-23
> **Thatlinuxguy said:**
> So far none of those have worked for me this is what I get when I try to update

```
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://dl.google.com stable Release: Unknown error executing gpgv

W: GPG error: http://archive.canonical.com lucid Release: Unknown error executing gpgv
W: GPG error: http://archive.canonical.com lucid Release: Unknown error executing gpgv
W: GPG error: http://ppa.launchpad.net lucid Release: Unknown error executing gpgv
W: GPG error: http://ppa.launchpad.net lucid Release: Unknown error executing gpgv
W: GPG error: http://ppa.launchpad.net lucid Release: Unknown error executing gpgv
W: GPG error: http://us.archive.ubuntu.com lucid Release: Unknown error executing gpgv
W: GPG error: http://us.archive.ubuntu.com lucid-updates Release: Unknown error executing gpgv
W: GPG error: http://us.archive.ubuntu.com lucid-backports Release: Unknown error executing gpgv
W: GPG error: http://security.ubuntu.com lucid-security Release: Unknown error executing gpgv
W: Failed to fetch http://dl.google.com/linux/deb/dists/stable/Release  

W: Failed to fetch http://ppa.launchpad.net/merlwiz79/aurora/ubuntu/dists/lucid/main/binary-i386/Packages.gz  404  Not Found

W: Some index files failed to download, they have been ignored, or old ones used instead.

```

This is all I could find for you: [http://johnny.chadda.se/article/strange-error-in-debian-40-error-executing-gpgv/](http://johnny.chadda.se/article/strange-error-in-debian-40-error-executing-gpgv/)

I hope it helps.

---

### Post by Thatlinuxguy on 2010-06-23
> **altonbr said:**
> This is all I could find for you: [http://johnny.chadda.se/article/strange-error-in-debian-40-error-executing-gpgv/](http://johnny.chadda.se/article/strange-error-in-debian-40-error-executing-gpgv/)

I hope it helps.

Nothing and this is the output I get when I try to connect to the time server. and the command line I use
```
sudo ntpdate pool.ntp.org
23 Jun 22:14:58 ntpdate[20754]: sendto(qnan.org): Operation not permitted
23 Jun 22:14:58 ntpdate[20754]: sendto(mail.honeycomb.net): Operation not permitted
23 Jun 22:14:58 ntpdate[20754]: sendto(ntp.idealab.com): Operation not permitted
23 Jun 22:14:59 ntpdate[20754]: sendto(qnan.org): Operation not permitted
23 Jun 22:14:59 ntpdate[20754]: sendto(mail.honeycomb.net): Operation not permitted
23 Jun 22:14:59 ntpdate[20754]: sendto(ntp.idealab.com): Operation not permitted
23 Jun 22:15:00 ntpdate[20754]: sendto(qnan.org): Operation not permitted
23 Jun 22:15:00 ntpdate[20754]: sendto(mail.honeycomb.net): Operation not permitted
23 Jun 22:15:00 ntpdate[20754]: sendto(ntp.idealab.com): Operation not permitted
23 Jun 22:15:01 ntpdate[20754]: sendto(qnan.org): Operation not permitted
23 Jun 22:15:01 ntpdate[20754]: sendto(mail.honeycomb.net): Operation not permitted
23 Jun 22:15:01 ntpdate[20754]: sendto(ntp.idealab.com): Operation not permitted
23 Jun 22:15:02 ntpdate[20754]: no server suitable for synchronization found

```

---

### Post by Thatlinuxguy on 2010-06-23
Alright I got that command to work I was just blocking the ntp from going out but that hasn't solved my problems with the GPG issue.

---

### Post by prithvisekhar on 2010-07-02
recently installed 10.04 and after installing some packages to player/stage on run ' sudo apt-get update ' i get the following 
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0

and 
on $ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 5A9A06AEF9CB8DB0
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 5A9A06AEF9CB8DB0
gpg: requesting key F9CB8DB0 from hkp server keyserver.ubuntu.com
gpgkeys: HTTP fetch error 6: Couldn't resolve host 'keyserver.ubuntu.com'
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

and when i go to keyserver.ubuntu.com it say its ok 
the internet connection is in my lab and through a proxy and i have added in /etc/apt.conf
Acquire::http::Proxy "http://username:pass@10.20.0.21:3128";
Acquire::http::Proxy "ftp://username:pass@10.20.0.21:3128";

---

### Post by reakin on 2010-07-08
I don't think the key system works at all when you are behind a firewall.  I keep trying to update from the public library, but get these annoying gpg errors.  Why are they using some strange port, or at least don't give an option just to download from http?  My updates are broken until I find some connection outside a firewall (doesn't seem to be too easy in Sydney).

---

### Post by barney385 on 2010-07-09
I installed an updated kernel yesterday and today I'm getting GPG errors.

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures were invalid: BADSIG 1780999033C3C104 Launchpad GDM2Setup
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures were invalid: BADSIG 35DA01C261E46227 Launchpad Default PPA
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures were invalid: BADSIG 6AF0E1940624A220 Launchpad PPA for TualatriX

I'm behind a library firewall, but that's never made a difference.

There's corrective measures in the opening post, but that's from a year ago.

---

### Post by Eskobar on 2010-08-02
I just installed Lucid tonight and I had some gpg key errors and I found this post via google...and I used the original posters suggestion of " sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys "   worked like a charm...THANKS!

---

### Post by reakin on 2010-08-02
Well I still get the annoying error messages and I still can't install something without a big 'Warming! This package is not authenticated'.

If I had to guess, I tried updating from behind a firewall and the keys could not be downloaded.  Now that I am not behind a firewall, the apt system (I don't know what to call it) still thinks it can't download the keys, although it has.  There must be some way to reset it..

I should file a bug.  Probably will.

---

### Post by Elie-M on 2010-08-24
thx that helped me a lot! :)

---

### Post by reakin on 2010-08-24
Didn't help me.

---

### Post by HfX on 2010-11-30
Hi, I know exactly what happened to me to bring the following error:

W: GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) lucid Release: Die folgenden Signaturen waren ungültig: BADSIG 54422A4B98AB5139 Oracle Corporation (VirtualBox archive signing key) <info@virtualbox.org>

I was at a customer and used their wireless LAN. It was that kind of Wireless Lan where the connection is not encrypted but you get this login pages in your browser like at a hotspot.

When only connected to the AP without internet connection (since not authenticated to the hotspot) my system tried to update. There something went wrong.

I found this wonderful description at virtualbox.org which helped me and removed the errors. (use the exact commands and do not delete a directory, only files).

# sudo -s -H
# apt-get clean
# rm /var/lib/apt/lists/*
# rm /var/lib/apt/lists/partial/*
# apt-get clean
# apt-get update

I hope I could help. The original URL is here: [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)
search for BADSIG there.

Regards

HfX

---

### Post by angelcleff on 2011-04-07
Thanks a lot my friend!
it worked just perfect :o

---

### Post by Gotlieb on 2011-04-18
Hi

I just got this 

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EC7B7B7D4439DBD6

help

---

### Post by MagikGimp on 2011-10-15
Many thanks, easy fix with clear instructions. Now, if only someone could tell me why this happens in the first place (I only had one problematic key after adding the wine repository); doesn't make any sense to me.

---

### Post by raja.genupula on 2011-10-29
hi thank you , this works to me.
thanks again.

---

### Post by Pete Pupalaikis on 2011-11-10
Thanks very much - this solved a problem I had getting a Wine update.

Would a knowledgeable mind explaining the mechanics of what is going on in this case.  I'm assuming that the update manager could not verify the security of the update or something like that, but I'm not sure how following these directions solves the problem or what is going on internally.  Did I force upbuntu to trust the key (I hope not).

Sorry if this is a basic question.
Pete

---

### Post by 741Baus on 2011-11-10
Thanks very much this helped with my update GPG errors via terminal 
          Peter

---

### Post by ghbarratt on 2011-12-07
Just wanted to say that:
[FONT="Courier New"]sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1015216E75198A89[/FONT]
worked for me. Thanks!

---

### Post by bookcrazy on 2012-01-11
Thank you!

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 596D65AB5F0D930C
```

Worked like a charm for me in 11.10!

---

### Post by philsmack1 on 2012-03-06
A big thanks to an old thread! This has been annoying me for weeks.

:D

---

### Post by vkadal on 2012-10-08
I tried the suggested above. Still I am having the problem in Ubuntu 12.04

---

