---
title: "Synergy help"
date: 2010-05-12
forum: General Help
---

### Post by EJD on 2010-05-12
Trying to get synergy to work in new install, had it working for years in old install.  I'm getting these messages at start:

ejdoney@linux-desktop:/etc$ synergys -f
INFO: synergys.cpp,1042: Synergy server 1.3.1 on Linux 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686
DEBUG: synergys.cpp,1051: opening configuration "/home/ejdoney/.synergy.conf"
DEBUG: synergys.cpp,1058: cannot open configuration "/home/ejdoney/.synergy.conf"
DEBUG: synergys.cpp,1051: opening configuration "/etc/synergy.conf"
DEBUG: synergys.cpp,1062: configuration read successfully
FATAL: synergys.cpp,655: unknown screen name `linux-desktop'

Don't know why it's trying to connect to screen name 'linux-desktop'.  Here's my hosts file:

127.0.0.1    localhost
127.0.0.1    linux-desktop
127.0.0.1    desktop
163.230.1.202    windowspc

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


Any help would be appreciated

---

### Post by EJD on 2010-05-13
Bump, desperate for help here.

---

### Post by howefield on 2010-05-13
You don't appear to have told synergy where the config file is.

Sorry, it worked out where it is, I was on the phone when pressing the submit button.

---

### Post by andrewklau on 2010-05-13
Have you set your alias in your config file?

Remember synergys = server
synergyc = client

---

### Post by howefield on 2010-05-13
If my server side computer was "linux-desktop" and my client side was "laptop", my config file would look something like this

section: screens
        linux-desktop:
        laptop:
end
section: links

        linux-desktop:
                right = laptop
        laptop:
                left = linux-desktop

end

---

