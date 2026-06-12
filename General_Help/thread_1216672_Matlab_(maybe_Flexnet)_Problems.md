---
title: "Matlab (maybe Flexnet) Problems"
date: 2009-07-18
forum: General Help
---

### Post by nmaster on 2009-07-18
Matlab used to work perfectly, but last night I realized that it won't start.  I don't think that I've installed anything that could interfere.  Apparently Matlab can't access my school's license server.  I tried looking at the link, but I don't really understand it. Here's the error message from the terminal.

```

neal@ubuntu:~$ matlab
License checkout failed.
License Manager Error -15
MATLAB is unable to connect to the license server. 
Check that the license manager has been started, and that the MATLAB client machine can communicate
with the license server.

Troubleshoot this issue by visiting: 
http://www.mathworks.com/support/lme/R2009a/15

Diagnostic Information:
Feature: MATLAB 
License path: /home/neal/.matlab/R2009a_licenses:/usr/local/matlab/licenses/license.dat:/usr/local/matlab/licenses
/network.lic: 
FLEXnet Licensing error: -15,570. System Error: 115


```

---

### Post by nmaster on 2009-07-19
I guess no one knew any answers, but it started to work again today.  I suppose it was a problem with the license server and not with me.  Thanks to anyone who read this though.

---

