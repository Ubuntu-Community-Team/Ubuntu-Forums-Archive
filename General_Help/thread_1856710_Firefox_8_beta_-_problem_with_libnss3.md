---
title: "Firefox 8 beta - problem with libnss3"
date: 2011-10-08
forum: General Help
---

### Post by curts on 2011-10-08
I have successfully installed firefox-8.0b2 for amd_64 on my 64-bit 11.04 installation (2.6.38-11-generic).  It works well - it's the Firefox I've been waiting for since Firefox4 arrived on the scene, except for a small problem with the Flash plug-in.

```
/local/x86_64/bin/firefox-8.0b2/plugin-container: /usr/lib/libnss3.so: version `NSS_3.12.10' not found (required by /local/x86_64/bin/firefox-8.0b2/libxul.so)
```

The new libxul.so depends on libnss3.so v3.12.10, but both Natty and Oneiric provide 3.12.9+ckbi-1.82-0ubuntu2.1 and 3.12.9+ckbi-1.82-0ubuntu6, respectively.

I successfully installed the libnss3-1d_3.12.11-3_amd64.deb and libnss3-dev_3.12.11-3_amd64.deb packages built from nss_3.12.11-3.dsc (and resolved its dependencies), but there was no replacement for the libnss3.so lib.  After a lot of searching with Google, I'm a bit stumped at this point.

Can anyone point me to either suitable .deb pkgs or source to resolve this dependency?  Or do I need to take this issue to the Mozilla forums?  I gather many of the RPM based distros have moved beyond nss v3.12.9.

I'm not putting a [64 bit] prefix on this post, as I expect this problem impacts both 32-bit & 64-bit Ubuntu.

Thanks,

Curt

---

### Post by lovinglinux on 2011-10-10
How did you install Firefox 8 and Flash?

I would suggest that you use a mopzillateam ppa. See [Firefox 7 & Beyond Mega Thread](http://ubuntuforums.org/showthread.php?t=1712247)

If your problem is flash, you can try [Flash-Aid](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

I am running Firefox 8.0b without issues, but on a 32bit system.

---

### Post by curts on 2011-10-10
I installed Firefox 8 by downloading the pre-built AMD64 bzip2 archive from the Mozilla release FTP site and installed it in /usr/local/bin.  I've been doing this for years, so it is not inexperience with installing a Firefox build.  I do not wish to *replace* the standard Firfox installation with a beta build, so I do not wish to use a mopzillateam ppa, hence the install to /usr/local.  I do not believe it is a problem with my Flash install, as it was working just fine with my Firefox 7 beta install to /usr/local that I was using prior to the standard Firefox for 11.04 being updated to Firefox 7.

It has occured to me that if I were to build Firefox 8 beta from source maybe it would build a libxul.so that uses the libnss3 available in 11.04 or the configure script will tell me what the minimum acceptable libnss3 version is for Firefox 8.  It is likely to be several days before I would have an opportunity to explore this.

I was hoping I was just missing something stupid and could be pointed to the resources for libnss3 3.12.11-3 to go with the libnss3-1d 3.12.11-3 I've built.

---

### Post by lovinglinux on 2011-10-10
> **curts said:**
> I installed Firefox 8 by downloading the pre-built AMD64 bzip2 archive from the Mozilla release FTP site and installed it in /usr/local/bin.  I've been doing this for years, so it is not inexperience with installing a Firefox build.  I do not wish to *replace* the standard Firfox installation with a beta build, so I do not wish to use a mopzillateam ppa, hence the install to /usr/local.  I do not believe it is a problem with my Flash install, as it was working just fine with my Firefox 7 beta install to /usr/local that I was using prior to the standard Firefox for 11.04 being updated to Firefox 7.

It has occured to me that if I were to build Firefox 8 beta from source maybe it would build a libxul.so that uses the libnss3 available in 11.04 or the configure script will tell me what the minimum acceptable libnss3 version is for Firefox 8.  It is likely to be several days before I would have an opportunity to explore this.

I was hoping I was just missing something stupid and could be pointed to the resources for libnss3 3.12.11-3 to go with the libnss3-1d 3.12.11-3 I've built.

I am not sure why this is happening. I just tested Firefox 8.0b2 and it is working with libnss3.so v3.12.9 on 32bit.

Have you checked the downloaded file hash? It could be a corruption. Try to download and install it again.

---

### Post by curts on 2011-10-11
OK, it turns out I did have a bad signature for the archive, so I re-downloaded (good signature this time) and re-installed, but no change in behavior.  Tested Firefox 8 on Ubuntu AMD64 10.04 with both the distributed 32-bit, wrapped Flash plug-in and the beta 64-bit plug-in, but neither worked.  Verified Flash plug-in still works in Firefox 7 (also installed in /usr/local).

Downloaded the Firefox 8 source package and built a copy on Ubuntu AMD64 10.04.  Still get the same error with libxul.so wanting version `NSS_3.12.10' when Firefox 8 tries to use the Flash plug-in.  Clarification: it is not a start-up error - you have to actually try displaying Flash content to see the error.

---

### Post by lovinglinux on 2011-10-11
Have you tried the 32bit Firefox, just to make sure this isn't something affecting only the 64bit build?

If you do that, you will need to put the 32bit flash object in the profile folder, otherwise flash won't work.

---

### Post by curts on 2011-10-11
OK, downloaded and installed the 32-bit versions of Firefox 8 and Flash plug-in and installed on my Ubuntu AMD64 10.04 install.  I still get the same error:

/local/x86_32/bin/firefox-8.0b2/plugin-container: /usr/lib32/libnss3.so: version `NSS_3.12.10' not found (required by /local/x86_32/bin/firefox-8.0b2/libxul.so)

---

### Post by lovinglinux on 2011-10-12
> **curts said:**
> OK, downloaded and installed the 32-bit versions of Firefox 8 and Flash plug-in and installed on my Ubuntu AMD64 10.04 install.  I still get the same error:

/local/x86_32/bin/firefox-8.0b2/plugin-container: /usr/lib32/libnss3.so: version `NSS_3.12.10' not found (required by /local/x86_32/bin/firefox-8.0b2/libxul.so)

Try to disable crash protection (plugin-container) and check if the problem persists.

[http://kb.mozillazine.org/Plugin-container_and_out-of-process_plugins](http://kb.mozillazine.org/Plugin-container_and_out-of-process_plugins)

---

### Post by curts on 2011-10-13
Well, I found 'dom.ipc.plugins.enabled.libflashplayer.so' was not in the profile, so I tried adding it.  I tried both true & false values but it didn't have any effect.

---

### Post by lovinglinux on 2011-10-13
> **curts said:**
> Well, I found 'dom.ipc.plugins.enabled.libflashplayer.so' was not in the profile, so I tried adding it.  I tried both true & false values but it didn't have any effect.

You need to restart Firefox to take effect. If that doesn't disable the flash plugin container, use just *dom.ipc.plugins.enabled*.

---

### Post by curts on 2011-10-13
OK, I had not restarted Firefox.  I also didn't have it configured correctly on the first try (I had mistakenly created a string instead of Boolean entry).  Additionally, I'm not certain whether it uses the actual .so name or the name it finds in the plugin directory (mine are sym-linked so I can have both the wrapped 32-bit and beta 64-bit plugins present and then disable in Firefox the one I don't want to use).  This attempt I also set *dom.ipc.plugins.enabled* = false, since that was the setting shown in the Mozilla article you pointed me to.

With these settings in place, I am able to successfully use the beta 64-bit Flash plugin with the pre-built AMD64 Firefox 8 installation.

With the correct individual .so entry in place, I was able to set *dom.ipc.plugins.enabled* = true and still have Flash work.

What is the next step towards a long-term solution?

---

### Post by lovinglinux on 2011-10-13
> **curts said:**
> OK, I had not restarted Firefox.  I also didn't have it configured correctly on the first try (I had mistakenly created a string instead of Boolean entry).  Additionally, I'm not certain whether it uses the actual .so name or the name it finds in the plugin directory (mine are sym-linked so I can have both the wrapped 32-bit and beta 64-bit plugins present and then disable in Firefox the one I don't want to use).  This attempt I also set *dom.ipc.plugins.enabled* = false, since that was the setting shown in the Mozilla article you pointed me to.

With these settings in place, I am able to successfully use the beta 64-bit Flash plugin with the pre-built AMD64 Firefox 8 installation.

What is the next step towards a long-term solution?

I would report the problem to Ubuntu [https://bugs.launchpad.net](https://bugs.launchpad.net)

Unfortunately, I have no idea why this is happening.

---

### Post by curts on 2011-10-18
Not a problem in Ubuntu AMD64 11.10.

---

### Post by lovinglinux on 2011-10-18
> **curts said:**
> Not a problem in Ubuntu AMD64 11.10.

Great.

---

