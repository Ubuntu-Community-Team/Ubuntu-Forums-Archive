---
title: "Tried to update graphics, now cant install anything? Dont know what to do"
date: 2010-09-27
forum: General Help
---

### Post by ICANSEEYOU7687 on 2010-09-27
So first I noticed that ATI's linux driver had an udpate from what I had, so I went ahead and downloaded it and ran the file

$sh ati-file.run

everything installed great except for an error message that said something about the DKMS failed to install...

So I then tried to go under Administrator menu (I think it was the administrator user) -> hardware and enable the ATI driver that this found.  But it gave me some fglrs (something like that) error

So i went into synaptic and reinstalled and and rebooted everything seemed fine (but still nothing updated) until i rebooted again.

No everytime I boot it tells me I am in low graphics mode...

and if I try to install/unistall ANYTHING I get an error that says 

E: /var/cache/apt/archives/fglrx_2%3a8.723.1-0ubuntu5_amd64.deb: subprocess new pre-installation script returned error exit status 1

I have no idea why this is happening or how to fix it, and I feel im going to have to reinstall ubuntu :(

thanks

---

### Post by andrewthomas on 2010-09-27
[http://ubuntuforums.org/showpost.php?p=9867591&postcount=9](http://ubuntuforums.org/showpost.php?p=9867591&postcount=9)

Check out this post.  Maybe read the entire thread.

---

### Post by ICANSEEYOU7687 on 2010-09-28
woo thanks.  I'll give it a shot.

Unfortunately right after you posted out power went out, and I could not fiddle with anything.  Now im at work, ill have to give it a try at lunch.

Thanks

---

### Post by ICANSEEYOU7687 on 2010-09-28
Finally got a chance to try, but I get an error...

It seems I cannot fully install fglrx, or unistall it (tried also through terminal) also now when I go into hardware drivers, ubuntu is telling me "No propietary drivers found"

here is what the terminal spits out

```

[Warning] Uninstall : inst_path_default or inst_path_override
 does not exist in /etc/ati.  This suggests that the ATI driver
 is not installed, the ATI driver is only partially installed,
 or the current ATI driver installed is an older version than the
 one this script was designed for.  Both files listed above are
 required for determining where installed files are located.
 To force uninstallation of the driver by guessing where the
 uninstallation files are located, set the FORCE_ATI_UNINSTALL
 environment variable and re-run /usr/share/ati/fglrx-uninstall.sh (this is not recommended).

dpkg: error processing /var/cache/apt/archives/fglrx_2%3a8.723.1-0ubuntu5_amd64.deb (--unpack):


```

Any help would be greatly appreciated, I really dont wanna have to reinstall everything :(

---

### Post by Soul-Sing on 2010-09-28
```
sudo dpkg --remove --force-remove-reinstreq fglrx_2%3a8.723.1-0ubuntu5_amd64.deb
```

better:

```
sudo dpkg --remove --force-remove-reinstreq fglrx
```

> FORCE_ATI_UNINSTALL
 environment variable and re-run /usr/share/ati/fglrx-uninstall.sh

you could run it (uninstall.sh)

---

### Post by ICANSEEYOU7687 on 2010-09-28
thanks for the quick reply! sorry im still learning terminal stuff....

I have tried the uninstall shell script and it tells me that basically not all of the files are there and cannot do it.

I tried the two commands listed above, and it tells me that I need to use that to uninstall the packages and not the  individual files ><

*EDIT*
I replaced my xorg.conf with a backup that I had created, and reinstalled xorg files.  And everything seems ok... im actually vnc'd to it from work atm (shh dont tell anyone)

NOW... its running with catalyst 10.8 and (like originally I was trying to upgrade it to the 10.9 from the .run file from ati.  But this gives me an error.
Also (not to keep pounding questions... but wuts the difference from using the one from the ATI site, and going to System -> administrator - > hardware drivers

which comes with with an unfree ati driver.

thanks!!

*EDIT*
If I try to install the packages from ATI i get a dkms error while installing.... but it "completes successfully"
but the catalyst control center still says 10.8 (should be the 10.9)

so I just went back to the package manager and reinstalled fglrx and its doing the same thing as it was.  But I noticed that my xorg.conf is blank whenever I try to install these.  I dont know why

---

