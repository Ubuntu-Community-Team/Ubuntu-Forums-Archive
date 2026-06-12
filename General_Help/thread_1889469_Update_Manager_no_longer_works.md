---
title: "Update Manager no longer works"
date: 2011-12-01
forum: General Help
---

### Post by jkorten on 2011-12-01
I have spent the better part of a day trying all of the fixes I see for update manager. Reloading keys, rewriting the apt config file etc. And still for 38 days I have not been able to upgrade my system.

I have dropped to the terminal and run the apt-get update. I'm wondering if this is keeping me up to date and the Update Manager just doesn't know this?

I must say release 11.10 has been trying for me. So many issues that I've had to research and fix. I think this release was a tad premature.

Any advice on Update Manager? I've also tried re-installing it. I've tried the following:

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5 16126D3A3E5C1192

Which was advised in another thread. All to no avail. Each time I try to run Update Manager I get the following message:

"Failed to Download Repository Information"

and the details states:

W:Failed to fetch [http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.


Has Ubuntu changed a server location?

BTW I have even tried to remove audio-dev but cannot find it and don't know what library it is associated with.

But none of the rest of my software shows as being updated either.

Any help would be appreciated.

Thanks,


Jerry

---

### Post by BC59 on 2011-12-01
The 2 repositories you have problem belong to the Ubuntu Audio Development Team and maybe there out. Just uncheck them from Software Sources and update.

---

### Post by Elfy on 2011-12-01
[http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/)

There is no oneiric version.

---

### Post by jkorten on 2011-12-01
> **BC59 said:**
> The 2 repositories you have problem belong to the Ubuntu Audio Development Team and maybe there out. Just uncheck them from Software Sources and update.


So simple a solution. So difficult my effort. At least this won't be forgotten!

Thanks much BC59!!!

---

### Post by BC59 on 2011-12-01
You are welcome. Happy to help you.

---

