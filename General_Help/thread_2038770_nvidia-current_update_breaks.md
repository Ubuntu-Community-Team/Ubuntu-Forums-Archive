---
title: "nvidia-current update breaks"
date: 2012-08-07
forum: General Help
---

### Post by Statia on 2012-08-07
My system uses an Asus Geforce ENGT430 graphics card. 
This morning there was a security update for the nvidia driver.
I was using nvidia295.40-0ubuntu1 (precise), new version was 295.40-0ubuntu1.1 (precise-security). I got this error after the upgrade:

```
Package: nvidia-current
Error: subprocess installed post-installation script returned error exit status 3
```After I had rebooted, I noticed lower resolution, transparency and other desktop effects gone. Checked modules, found the system was using vesafb instead of nvidia. Reboot again, desktop looks good again, but now I am running the Nouveau drivers. (How? Why?) 
I revert to nvidia295.40-0ubuntu1, but get same error exit status 3. Reboot: vesafb.

Has anyone else had these problems with this update?

I then used the "Additional drivers" program to install nvidia drivers. Am I correct in assuming this gives me the driver straight from Nvidia? Current version according to the Nvidia X Server Settings program is 295.49.

However, if I check in Muon, it lists nvidia-current as installed, with version 295.40 1.1

What is the best action? Leave it like this? Or uninstall nvidia-current to avoid conflicts?

---

### Post by Frogs Hair on 2012-08-07
> Has anyone else had these problems with this update?

I had no problems with Ubuntu using a Nvidia 8 series card.

> I then used the "Additional drivers" program to install nvidia drivers. Am I correct in assuming this gives me the driver straight from Nvidia?  

 This driver is modified for use with Ubuntu. The current version from the Nvidia site for my configuration is different. I always install using the additional drivers jockey. [http://www.nvidia.com/object/linux-display-amd64-295.71-driver.html](http://www.nvidia.com/object/linux-display-amd64-295.71-driver.html) 

If everything is working with the Nouveau drivers stay with them until someone familiar with that graphics card answers your thread.

---

### Post by Statia on 2012-08-07
> **Frogs Hair said:**
> 
 This driver is modified for use with Ubuntu. The current version from the Nvidia site for my configuration is different. I always install using the additional drivers jockey.  

So jockey installs a different (newer) version than Muon?
That is.... special....


> 
If everything is working with the Nouveau drivers stay with them until someone familiar with that graphics card answers your thread.

I am currently not using the Nouveau drivers, I am using 295.49 jockey gave me.
I had planned not to mess up this installation by installing only from Ubuntu-repositories. But now Ubuntu breaks stuff and I have to revert to jockey to repair it, but I have no idea what this will do in the long run.

---

### Post by dino99 on 2012-08-07
use your package manager to:

- purge the installed nvidia packages 
- then reinstall nvidia-current , but only AFTER having cleaned the repositories & updated them :
 a/ sudo apt-get clean
 b/ sudo apt-get autoclean
 c/ sudo apt-get autoremove
 d/ sudo apt-get update

note: i still cant trust muon (never seen so buggy pakage :( )

---

### Post by Statia on 2012-08-07
> **dino99 said:**
> use your package manager to:

- purge the installed nvidia packages 
- then reinstall nvidia-current , but only AFTER having cleaned the repositories & updated them :
 a/ sudo apt-get clean
 b/ sudo apt-get autoclean
 c/ sudo apt-get autoremove
 d/ sudo apt-get update


OK, purged nvidia-current and then did a,b,c,d as suggested.
Next:

```
root@quokka:/# apt-get install nvidia-current
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  nvidia-current
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 58.5 MB of archives.
After this operation, 183 MB of additional disk space will be used.
Get:1 http://security.ubuntu.com/ubuntu/ precise-security/restricted nvidia-current amd64 295.40-0ubuntu1.1 [58.5 MB]
Fetched 58.5 MB in 60s (965 kB/s)                                              
Selecting previously unselected package nvidia-current.
(Reading database ... 264832 files and directories currently installed.)
Unpacking nvidia-current (from .../nvidia-current_295.40-0ubuntu1.1_amd64.deb) ...
Processing triggers for man-db ...
/usr/bin/mandb: can't create index cache /var/cache/man/12149: No such file or directory
Setting up nvidia-current (295.40-0ubuntu1.1) ...
INFO:Enable nvidia-current
DEBUG:Parsing /usr/share/nvidia-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/nvidia-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/nvidia-common/quirks/put_your_quirks_here
DEBUG:Processing quirk Latitude E6530
DEBUG:Failure to match OEM Manufacturer with Dell Inc.
DEBUG:Quirk doesn't match
DEBUG:Processing quirk ThinkPad T420s
DEBUG:Failure to match OEM Manufacturer with LENOVO
DEBUG:Quirk doesn't match
Removing old nvidia-current-295.40 DKMS files...
Loading new nvidia-current-295.40 DKMS files...
Error! DKMS tree already contains: nvidia-current-295.40
You cannot add the same module/version combo more than once.
dpkg: error processing nvidia-current (--configure):
 subprocess installed post-installation script returned error exit status 3
Errors were encountered while processing:
 nvidia-current
E: Sub-process /usr/bin/dpkg returned an error code (1)


```I'll try to decipher that. 
The error about not being able to create /var/cache/man I get with everything I install. I just found out the directory /var/cache/man is missing, so I created one, we'll see if that fixes those errors.
It looks like it thinks I operate a Latitude or a Thinkpad, then wants to run quirks for that but then finds out I don't own one. No problem I guess, as I indeed do not run a Lenovo Thinkpad or Dell Latitude. Next it wants to add a DKMS tree, but it is already there (why not purged?), so that should not really be a problem either. Whether this is the cause for the error 3 I don know.

---

### Post by Statia on 2012-08-08
This is getting pretty annoying....
I get this error now with every package I install, upgrade, purge or remove, whether with apt-get on the command line or with Muon.
Watching the forum I see more (but different) problems with this update. Do we just have to wait until Ubuntu fixes this?

---

### Post by Statia on 2012-08-10
Is it safe to uninstall nvidia-current now that I am using the driver supplied by jockey?

---

