---
title: "Cannot install Skype on 11.04"
date: 2012-05-11
forum: General Help
---

### Post by RamR on 2012-05-11
I had to reinstall my OS the other day and since then I cannot get Skype to install.  I was previously on 11.04 and that is what I installed again.  As I said, Skype was working before and now I can't even install it.

When I try to install it I get this message; Package dependencies cannot be resolved... and the details are;

```
The following packages have unmet dependencies:

skype: Depends: libc6 (>= 2.4) but 2.13-0ubuntu13.1 is to be installed
       Depends: libgcc1 (>= 1:4.1.1) but 1:4.5.2-8ubuntu4 is to be installed
       Depends: libqt4-dbus (>= 4:4.5.3) but 4:4.7.2-0ubuntu6.3 is to be installed
       Depends: libqt4-network (>= 4:4.5.3) but 4:4.7.2-0ubuntu6.3 is to be installed
       Depends: libqtcore4 (>= 4:4.5.3) but 4:4.7.2-0ubuntu6.3 is to be installed
       Depends: libqtgui4 (>= 4:4.5.3) but 4:4.7.2-0ubuntu6.3 is to be installed
       Depends: libstdc++6 (>= 4.2.1) but 4.5.2-8ubuntu4 is to be installed
```

I have tried installing through Software Centre, Synaptic and the Terminal.

I have also tried, to no avail, to install libqtgui4.  

Any suggestions???

Thanks in advance.

---

### Post by Monotoko on 2012-05-11
It looks as though Skype may have been updated if I'm not mistaken, but are you sure that your version of Ubuntu is completely up to date? (updates + everything done?)

---

### Post by steeldriver on 2012-05-11
I have 2.2.0.35 (beta) running on 11.10 Xubuntu here - no problem installing (it runs flaky though)

I just updated with the latest 32-bit .deb off the website and that appears to have worked ok

---

### Post by RamR on 2012-05-11
Every time I try to check for updates it stalls out and gives the error message "Failed to download repository information", with the details...

```
W:Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/natty/Release.gpg  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/natty-updates/Release.gpg  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/natty/main/source/Sources  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/natty/restricted/source/Sources  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/natty/universe/source/Sources  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/natty/multiverse/source/Sources  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/natty/main/binary-i386/Packages  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/natty/restricted/binary-i386/Packages  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/natty/universe/binary-i386/Packages  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/natty/multiverse/binary-i386/Packages  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/natty-updates/main/source/Sources  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/source/Sources  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/natty-updates/universe/source/Sources  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/source/Sources  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/natty-updates/main/binary-i386/Packages  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/binary-i386/Packages  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/natty-updates/universe/binary-i386/Packages  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/binary-i386/Packages  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/natty/main/i18n/Translation-en  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/natty/multiverse/i18n/Translation-en  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/natty/restricted/i18n/Translation-en  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/natty/universe/i18n/Translation-en  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/natty-updates/main/i18n/Translation-en  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/i18n/Translation-en  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/i18n/Translation-en  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/natty-updates/universe/i18n/Translation-en  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by Ubun2to on 2012-05-11
I downloaded my version of Skype from the [official Skype website]("http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/"). Works like a charm.
In any case, you could easily run the Windows version of Skype under Wine (one time I accidentally downloaded the Windows version, and I went along with it to see if it would work- it did).

---

### Post by mastablasta on 2012-05-12
you can download and use the .deb file foudn on skype website.
regarding your updates it seems that it can't find the server. try changing the server for repositories.

---

### Post by RamR on 2012-05-12
> **mastablasta said:**
> 
regarding your updates it seems that it can't find the server. try changing the server for repositories.

That was it!!  Changed to the main server and it solved the update issue as well as the installing of Skype.

---

### Post by RamR on 2012-05-12
Thanks to mastablasta and anyone else who provided ideas.

---

