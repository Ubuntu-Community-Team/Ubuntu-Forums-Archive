---
title: "Ubuntu Update manager"
date: 2010-05-29
forum: General Help
---

### Post by Bharath Kumar V on 2010-05-29
Dear All,

I am presently usinng Ubuntu 9.10 Karmic Koala and I want to upgrade to Ubuntu 10.04 LTS

When I open the Update Manager, and Check for latest available updates, I get this following error message:

Quote:

[I][COLOR=Navy]W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg)  Could not resolve 'in.archive.ubuntu.com'
W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_IN.bz2)  Could not resolve 'in.archive.ubuntu.com'
W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_IN.bz2)  Could not resolve 'in.archive.ubuntu.com'
W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_IN.bz2)  Could not resolve 'in.archive.ubuntu.com'
W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_IN.bz2)  Could not resolve 'in.archive.ubuntu.com'
W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg)  Could not resolve 'in.archive.ubuntu.com'
W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_IN.bz2)  Could not resolve 'in.archive.ubuntu.com'
W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_IN.bz2)  Could not resolve 'in.archive.ubuntu.com'
W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_IN.bz2)  Could not resolve 'in.archive.ubuntu.com'
W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_IN.bz2)  Could not resolve 'in.archive.ubuntu.com'
W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg)  Could not resolve 'in.archive.ubuntu.com'
W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_IN.bz2)  Could not resolve 'in.archive.ubuntu.com'
W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_IN.bz2)  Could not resolve 'in.archive.ubuntu.com'
W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_IN.bz2)  Could not resolve 'in.archive.ubuntu.com'
W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_IN.bz2)  Could not resolve 'in.archive.ubuntu.com'
W: Failed to fetch [http://dl.google.com/linux/deb/dists/stable/Release.gpg](http://dl.google.com/linux/deb/dists/stable/Release.gpg)  Could not resolve 'dl.google.com'
W: Failed to fetch [http://dl.google.com/linux/deb/dists/stable/main/i18n/Translation-en_IN.bz2](http://dl.google.com/linux/deb/dists/stable/main/i18n/Translation-en_IN.bz2)  Could not resolve 'dl.google.com'
W: Some index files failed to download, they have been ignored, or old ones used instead.
[/COLOR][/I]
Unquote

I am unable to upgrade to Ubuntu 10.04 LTS, please suggest me what should I do to upgrade.

Regards
Bharath Kumar V

---

### Post by dcstar on 2010-05-29
> **Bharath Kumar V said:**
> Dear All,

I am presently usinng Ubuntu 9.10 Karmic Koala and I want to upgrade to Ubuntu 10.04 LTS

When I open the Update Manager, and Check for latest available updates, I get this following error message:

```
W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg)  **Could not resolve 'in.archive.ubuntu.com**'
```
........

You have DNS/Network problems. Fix them and things will work.

---

### Post by gandalf2000 on 2010-06-01
I am having the same problem just not as extensive.  It would be good if someone with a decent answer would reply.

---

### Post by gandalf2000 on 2010-06-02
Found the answer last night.  Apparently the servers are down and they don't know when they'll be back up.  Try every couple days is my advise, that's what I'll be doing.

---

### Post by philinux on 2010-06-02
Try changing the server to main in update manager.

---

### Post by Bharath Kumar V on 2010-06-03
> **philinux said:**
> Try changing the server to main in update manager.

I am not clear. Could you please explain in detail?

Regards
Bhaarath Kumar V

---

### Post by plucky on 2010-06-03
> **Bharath Kumar V said:**
> I am not clear. Could you please explain in detail?

Regards
Bhaarath Kumar V

**System > Administration > Software Sources** and on the "Ubuntu Software" tag,look for the **Download from** box and select the **Main Server**.Then exit and select reload to download the package lists.

Good Luck

---

### Post by Bharath Kumar V on 2010-06-07
> **plucky said:**
> **System > Administration > Software Sources** and on the "Ubuntu Software" tag,look for the **Download from** box and select the **Main Server**.Then exit and select reload to download the package lists.

Good Luck

Thanks for explaining. I have carried out the changes and selected reload the packages lists. But, the problem persists.

Regards
Bharath Kumar V

---

### Post by mexicanseaf00d on 2010-06-07
my provider had some bizarre DNS problems once, since then I use OpenDNS servers, which are easily entered in the network manager  i cant remember if you have to register or not, their IP's are: 208.67.222.222  208.67.220.220  [http://www.opendns.com/](http://www.opendns.com/)

---

