---
title: "How to get /etc/samba back when you deleted it?"
date: 2011-05-20
forum: General Help
---

### Post by Roasted on 2011-05-20
So, I thought I knew what I was doing. I removed /etc/samba because I installed Zentyal and decided it was way overkill for what I wanted to do, so I removed it. I wanted to remove the smb.conf file so I decided to nuke the entire samba folder, confident it would come back when I reinstalled samba.

Well, it didn't.

How do I get it back? I just want my samba installation to get back to default.

---

### Post by linuxinstalledfromhdd on 2011-05-20
You don't have to nuke entire folder structure to uninstall anything in ubuntu. :confused:

Just back up your stuff and reinstall Ubuntu. That's honestly the best way in your situation.

---

### Post by capscrew on 2011-05-20
> **linuxinstalledfromhdd said:**
> You don't have to nuke entire folder structure to uninstall anything in ubuntu. :confused:

Just back up your stuff and reinstall Ubuntu. That's honestly the best way in your situation.

@Roasted
What do you think was in the directory /etc/samba ?

The only critical thing is the smb.conf file.  There is a copy at ```
/usr/share/samba/smb.conf
```

Copy the file to /etc/samba and start over.  

I agree; Zentyal is really a bunch of perl scripts to configure the OS and selected packages.  You can use it, but you really don't learn what is really going on.  I have a NAS that I built using 10.04 server and Samba.  It took 5 minutes to configure Samba and the shares I needed.  I spent more time fixing the typos than configuring the system.

@linuxinstalledfromhdd

Why would you advise someone to reinstall the entire OS because 1 package was missing its configuration file.  This is certainly not needed in this situation.  the entire Samba install can be configured from the smb.conf file if you wish.  

If the configuration was done via Nautilus the you need to delete the configuration files at /var/lib/samba/usershares.  These config files are not critical for Samba operation though.

In short, one should never need to resort to such drastic measures as a complete reinstall for such a simple problem.

---

### Post by linuxinstalledfromhdd on 2011-05-20
why would a user nuke a entire folder? You would have to ask them I guess.

---

### Post by Roasted on 2011-05-20
> **linuxinstalledfromhdd said:**
> why would a user nuke a entire folder? You would have to ask them I guess.

Because I suck. I just hit the rm command way too quick without thinking about what I was doing. Total ID-10-T error. :P Thanks guys!

---

