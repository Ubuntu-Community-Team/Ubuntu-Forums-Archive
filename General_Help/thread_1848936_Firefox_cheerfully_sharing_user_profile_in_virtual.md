---
title: "Firefox cheerfully sharing user profile in virtual machine simultaneously!!"
date: 2011-09-23
forum: General Help
---

### Post by Rebelli0us on 2011-09-23
Normally I dual-boot Windows/Linux and have Firefox sharing the same profile. It works great and no matter which OS I boot, Firefox is  synchronized.

But I know Firefox does not allow more than ONE instance of a profile to be running. However, I have a VirtualBox VM running Windows as guest OS under 64-bit Ubuntu as host ... and Windows inside the VM can run both Firefox and Thunderbird using the same profiles that are IN USE under Linux. How can that happen? Running profiles are normally locked! I don’t understand how 2 instances of Firefox are using the same profile simultaneously... for example using the same cache, settings and plugins!  The only downside I noticed so far is that the Mozilla apps take forever to start in the VM.

---

### Post by Dangertux on 2011-09-23
> **Rebelli0us said:**
> Normally I dual-boot Windows/Linux and have Firefox sharing the same profile. It works great and no matter which OS I boot, Firefox is  synchronized.

But I know Firefox does not allow more than ONE instance of a profile to be running. However, I have a VirtualBox VM running Windows as guest OS under 64-bit Ubuntu as host ... and Windows inside the VM can run both Firefox and Thunderbird using the same profiles that are IN USE under Linux. How can that happen? Running profiles are normally locked! I don&#8217;t understand how 2 instances of Firefox are using the same profile simultaneously... for example using the same cache, settings and plugins!  The only downside I noticed so far is that the Mozilla apps take forever to start in the VM.

Because Firefox in the guest can't see Firefox in the host.

---

### Post by Rebelli0us on 2011-09-23
> **Dangertux said:**
> Because Firefox in the guest can't see Firefox in the host.

True, Firefox cannot use API to check if another instance is running in the OS ... but Firefox creates a .parentlock file which prevents simultaneous use of the profile. So I don't get what's happening in the VM.

---

### Post by Dangertux on 2011-09-23
Right the file is created on the host and guest respectively. Thus they are separated by the hypervisor still. So in terms of the lock file, it doesn't really effect this. Firefox checks for the existance of the lock file locally, thus they have no ability to see the lock file on the other system.

You can explore the NO_REMOTE option, however in this case I think it will still allow multiple profile instances to be used.

---

### Post by Rebelli0us on 2011-09-23
> **Dangertux said:**
> Right the file is created on the host and guest respectively. Thus they are separated by the hypervisor still. So in terms of the lock file, it doesn't really effect this. Firefox checks for the existance of the lock file locally, thus they have no ability to see the lock file on the other system.

You can explore the NO_REMOTE option, however in this case I think it will still allow multiple profile instances to be used.

What do you mean? The profile is SHARED, two instances of Firefox are using the same profile in a shared folder in a NTFS partition. 

It&#8217;s incredibly convenient, I can switch from Linux to Windows instantly, start up Firefox and it has all the same tabs running... but I'm not getting the usual error message when the 2nd Firefox starts up, so I have a feeling that the profile will probably get trashed.

---

### Post by Dangertux on 2011-09-23
Oh, I understand what you're saying now. I thought you were saying something along the lines of you had your profile on each system one in a VM the other the host. 

Nevermind the virtualization stuff. That is interesting. I definitely think that the profile may end up corrupted using this method though. If you are looking for a way to do what  you said safely without destroying the profile you may consider setting up roaming profiles. That being said this may already have been done which is why you can access it in the manner you are.

[http://kb.mozillazine.org/Roaming_profile](http://kb.mozillazine.org/Roaming_profile)

---

### Post by Rebelli0us on 2011-09-23
> **Dangertux said:**
> Oh, I understand what you're saying now. I thought you were saying something along the lines of you had your profile on each system one in a VM the other the host. 

Nevermind the virtualization stuff. ***That is interesting.*** I definitely think that the profile may end up corrupted using this method though. If you are looking for a way to do what  you said safely without destroying the profile you may consider setting up roaming profiles. That being said this may already have been done which is why you can access it in the manner you are.

[http://kb.mozillazine.org/Roaming_profile](http://kb.mozillazine.org/Roaming_profile)

Yes it IS interesting, that's why I posted. I didn't set up "roaming", I don't even know what it means. I just used Firefox & TB Profile Manager in the VM and pointed to the existing profile. Linux doesn't support file permissions on NTFS partitions so maybe that's how 2 instances share without complaint.

---

### Post by Dangertux on 2011-09-23
> **Rebelli0us said:**
> Yes it IS interesting, that's why I posted. I didn't set up "roaming", I don't even know what it means. I just used Firefox & TB Profile Manager in the VM and pointed to the existing profile. Linux doesn't support file permissions on NTFS partitions so maybe that's how 2 instances share without complaint.

Linux can already read/write to the file, we identified that because you said your profile is properly updated even though it's on a shared partition, what Firefox is checking for is the existance of the .lock file. However, I don't think that is the issue now that you mention you have TB Profile Manager as it can set MOZ_NO_REMOTE=0 which means a profile can be used in multiple locations at the same time. I would consult your TB Profile Manager configuration, first. 


Just my thoughts.

---

### Post by Rebelli0us on 2011-09-23
> **Dangertux said:**
> Linux can already read/write to the file, we identified that because you said your profile is properly updated even though it's on a shared partition, what Firefox is checking for is the existance of the .lock file. However, I don't think that is the issue now that you mention you have TB Profile Manager as it can set MOZ_NO_REMOTE=0 which means a profile can be used in multiple locations at the same time. I would consult your TB Profile Manager configuration, first. 


Just my thoughts.

Profile manager is just a command line option that lets you create a profile and point it to an existing profile, thereby setting up a shared profile.

```


"C:\Program Files\Mozilla Firefox\firefox.exe" -profilemanager



```

---

### Post by Rebelli0us on 2012-08-12
Sharing the same profile simultaneously (locally or remotely) would be wonderful. Even though it appeared to work for me, the profile will most likely become corrupted. A broken email database would be bad!

Finally here’s the solution from one of the devs MattN posted July 26th, 2012, 3:05 am

[http://forums.mozillazine.org/viewtopic.php?f=31&t=2490329]("http://forums.mozillazine.org/viewtopic.php?f=31&t=2490329")

Front end with a script that attempts to “rm” the parent.lock file and if that fails then Thunderbird is already running that profile locally, remotely or from a virtual machine.

**You can still share the profile but not simultaneously**, somebody correct me if I’m wrong. Lastly, I’ve never written a Unix batch/script file, so if somebody has a good one-liner that would help all of us Linux newbies use the same profile form anywhere in the universe.

PS: [this here from mozillazine.org]("http://kb.mozillazine.org/Sharing_profiles_-_mail") suggests that simultaneous sharing may indeed be possible.

---

