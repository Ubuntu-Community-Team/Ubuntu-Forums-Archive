---
title: "Update Manager - Ubuntu 9.0.4"
date: 2009-08-11
forum: General Help
---

### Post by n_s_simpson on 2009-08-11
Hi, I've using a completely fresh install of Ubuntu 9.0.4.

I've just run the Update Manager and it's done a load of updates but it's struggling with one...

A pop-up box comes up saying "Could not download all repository indexes". This is the info if gives about it:

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/source/Sources.bz2)  Hash Sum mismatch
Some index files failed to download, they have been ignored, or old ones used instead.

I've been able to download sources.bz2 via Firefox.

Can anyone advice?

Thanks

Nick

---

### Post by n_s_simpson on 2009-08-11
Tried going into settings and telling it to access the main server instead of the GB one. Same error but different reasons...

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release](http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by michy99 on 2009-08-11
Go to System->Administration->Software Sources. Where it says Download from: choose a different server.

EDIT: I see you already tried that. See below.

---

### Post by michy99 on 2009-08-11
Enter this in a terminal:```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 437D05B5
```

---

### Post by n_s_simpson on 2009-08-11
Interestingly, changing it back to UK server again and now there's no errors.

Perhaps it somehow remembered it was unable to access it the first time and then doesn't bother to try again.

Thanks for your reply anyway. I assume this is a known issue.

EDIT:- Thinking about it when it's checking all the packages the first time it takes over a minute to download them all (42 in total). When you reload the Update Manager it is seconds so perhaps my assumption is right. I have no idea so I am guessing.

Just out of interest what does that code do?

---

### Post by n_s_simpson on 2009-08-11
michy...

Sorry to ask but I was hoping Firefox would update to 3.5.2 but it didn't (I think it updated slightly to 3.0.13 from 3.0.8 but I'm not sure).

Reading Firefox it says if the Update option is disabled it's dealt with by the Linux OS. Since it's not updated to the latest version do I simply have to follow the instructions on the Firefox website and why is the update option within Firefox disabled?

---

### Post by michy99 on 2009-08-11
The code would add the key for that repository to the trusted list. Probably, your regular repository was temporarily off-line, and is back now.

---

### Post by michy99 on 2009-08-11
Firefox 3.0 will not update to 3.5. If you want it, you have to install it separately. Read this thread to learn several different ways to do this:

[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by n_s_simpson on 2009-08-11
How come the auto update option is disabled? Are the Ubuntu team trying to stop people updating? Will it become a Managed Update shortly?

Also are all other programs updated by Update Manager, such as OpenOffice.

Sorry it's just last time I used Linux everything was manual. I didn't know the Linux Community knew the meaning of Auto :)

Got to say I'm thinking of leaving Vista because if I can get used to Ubuntu it seems much quicker on my aging laptop.


EDIT:- Just reading your link (thanks) and it says it'll be available as an official update via Update Manager eventually. Any idea of ETA's?

Also how come there's no easy update facility such as in Windows (ie an executable)? It seems Linux still requires manual coding for some updates. Is that more the software people at fault for not making their updates easier?

---

