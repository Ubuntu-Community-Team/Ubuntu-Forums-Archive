---
title: "Synaptic, Amarok, others not working (libstdc++.so.6)"
date: 2006-02-28
forum: General Help
---

### Post by wyred4sound on 2006-02-28
I'm not sure what I've done, but whenever I try and start any program including Synaptic and Amarok, I recieve the following error:

[PHP]synaptic: /opt/openoffice.org2.0/program/libstdc++.so.6: version `GLIBCXX_3.4.4' not found (required by synaptic)
synaptic: /opt/openoffice.org2.0/program/libstdc++.so.6: version `GLIBCXX_3.4.4' not found (required by /usr/lib/libapt-pkg-libc6.3-6.so.3.10)
[/PHP]

I've looked everywhere for solutions to this, have tried to install gcc-3.4.4 (and the other packages associated with it), but have not been able to resolve this.

Any help with this would be greatly appreciated!

---

### Post by wyred4sound on 2006-02-28
I just found a solution. I re-downloaded the libstdc++6  and libstdc++6-4.0-dev packages from [http://packages.ubuntu.com](http://packages.ubuntu.com). The did the following actions:

[PHP]rm -r /opt/openoffice.org2.0/program/libstdc++.so.6
 ln /usr/lib/libstdc++.so.6 --target-directory=/opt/openoffice.org2.0/program/[/PHP]

I'm guessing this is a problem specifically with a file corruption in OpenOffice, but otherwise, things are working fine now! I'm still 100% glad I made the switch from Windows.

---

