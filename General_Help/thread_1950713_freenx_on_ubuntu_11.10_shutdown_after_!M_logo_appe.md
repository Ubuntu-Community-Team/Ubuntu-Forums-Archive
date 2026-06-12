---
title: "freenx on ubuntu 11.10: shutdown after !M logo appears"
date: 2012-04-01
forum: General Help
---

### Post by ccwu on 2012-04-01
HI
    
    Here is my problem:
    NX Client connects and displays  !M logo and then window just     closes.
    I google about the issue :
    
    
[LIST]
[*]         **Problem**: At the client, the           !M logo window appears, but after a few seconds that window           just closes, even without showing any error message. 
[*]         **Solution**: The issue is due           custom VNC configuration. In the server, access your home           directory and run these commands, 
         sudo rm .Xauthority* touch .Xauthority chmod 600 .Xauthority
[/LIST]
     
      However, it did not work.
      Can someone help me about this problem?
      Thanks a lot

---

