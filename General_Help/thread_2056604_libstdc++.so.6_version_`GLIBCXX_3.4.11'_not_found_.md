---
title: "libstdc++.so.6: version `GLIBCXX_3.4.11' not found (required by writedap)"
date: 2012-09-11
forum: General Help
---

### Post by surja1 on 2012-09-11
Sir, I am trying to get opendap server in my system.I install libDAP and loadDAP without any error, but When I tried to run this I met the following problem

 /ocean/ROMS/Roms_tools/Opendap_tools/UBUNTU/writedap: /usr/local/MATLAB/R2011b/sys/os/glnx86/libstdc++.so.6: version `GLIBCXX_3.4.11' not found (required by /ocean/ROMS/Roms_tools/Opendap_tools/UBUNTU/writedap)
/ocean/ROMS/Roms_tools/Opendap_tools/UBUNTU/writedap: /usr/local/MATLAB/R2011b/sys/os/glnx86/libstdc++.so.6: version `GLIBCXX_3.4.11' not found (required by /usr/local/lib/libdapclient.so.3)
/ocean/ROMS/Roms_tools/Opendap_tools/UBUNTU/writedap: /usr/local/MATLAB/R2011b/sys/os/glnx86/libstdc++.so.6: version `GLIBCXX_3.4.11' not found (required by /usr/local/lib/libdap.so.10)


In my system libstdc++.so.6 script is in /usr/local/MATLAB/R2011b/sys/os/glnx86/libstdc++.so.6

Please help me to solve this problem.

---

### Post by surja1 on 2012-09-11
Sir, I am trying to get opendap server in my system.I install libDAP and loadDAP without any error, but When I tried to run this I met the following problem

/ocean/ROMS/Roms_tools/Opendap_tools/UBUNTU/writedap: /usr/local/MATLAB/R2011b/sys/os/glnx86/libstdc++.so.6: version `GLIBCXX_3.4.11' not found (required by /ocean/ROMS/Roms_tools/Opendap_tools/UBUNTU/writedap)
/ocean/ROMS/Roms_tools/Opendap_tools/UBUNTU/writedap: /usr/local/MATLAB/R2011b/sys/os/glnx86/libstdc++.so.6: version `GLIBCXX_3.4.11' not found (required by /usr/local/lib/libdapclient.so.3)
/ocean/ROMS/Roms_tools/Opendap_tools/UBUNTU/writedap: /usr/local/MATLAB/R2011b/sys/os/glnx86/libstdc++.so.6: version `GLIBCXX_3.4.11' not found (required by /usr/local/lib/libdap.so.10)


In my system libstdc++.so.6 script is in /usr/local/MATLAB/R2011b/sys/os/glnx86/libstdc++.so.6

Please help me to solve this problem.

---

### Post by critin on 2012-09-11
Did you install MATLAB  from Synaptic package Manager?  
You can open Synaptic and click on STATUS, then enter MATLAB in the search bar.  Or (vice-versa)  at the bottom of the page it will tell you if any packages are broken, you can 'fix broken' through the Edit tab.

You can also click on installed-upgradeable and mark them to be upgraded if that is the problem.
You can also enter MATLAB in search and it will bring all of it up,  you can mark Reinstall to pick up any missing apps.

And if the problem is not Matlab at all,  search for what you need.

This looks like the dev of writedap

[https://groups.google.com/a/opendap.org/forum/?fromgroups=#!msg/support/jK3U7ntH65c/4YrPN82NuX8J](https://groups.google.com/a/opendap.org/forum/?fromgroups=#!msg/support/jK3U7ntH65c/4YrPN82NuX8J)

---

### Post by oldos2er on 2012-09-11
Post moved to its own thread.

Threads merged. Please don't post your question at the end of older threads, in the future start a new thread.

---

