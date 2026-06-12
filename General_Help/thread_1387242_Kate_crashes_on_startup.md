---
title: "Kate crashes on startup"
date: 2010-01-21
forum: General Help
---

### Post by bcasanov on 2010-01-21
Hi,

I am using Ubuntu Karmic and I have the latest updates installed.  Whenever I click on Kate in the Application menu to start it up, I get a window saying that Kate closed unexpectedly.  Under details, it says: "Executable: kate PID: 7545 Signal: 11 (Segmentation fault).  Thinking that there must be some bug that would be fixed with new updates, I went and enabled the backports repository and installed a new version of kate from there.  I still got the same crash on startup.  When I run "kate" in the terminal, I have a ton of error messages that seem to repeat:

```
trying to create local folder /home/bcsnv/.kde/share: Permission denied
trying to create local folder /home/bcsnv/.kde/cache-Laptop: Permission denied
trying to create local folder /home/bcsnv/.kde/cache-Laptop: Permission denied
trying to create local folder /home/bcsnv/.kde/cache-Laptop: Permission denied
trying to create local folder /home/bcsnv/.kde/cache-Laptop: Permission denied
trying to create local folder /home/bcsnv/.kde/tmp-Laptop: Permission denied  
trying to create local folder /home/bcsnv/.kde/tmp-Laptop: Permission denied  
trying to create local folder /home/bcsnv/.kde/tmp-Laptop: Permission denied  
trying to create local folder /home/bcsnv/.kde/tmp-Laptop: Permission denied  
trying to create local folder /home/bcsnv/.kde/tmp-Laptop: Permission denied  
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/tmp-Laptop: Permission denied  
trying to create local folder /home/bcsnv/.kde/tmp-Laptop: Permission denied  
trying to create local folder /home/bcsnv/.kde/tmp-Laptop: Permission denied  
trying to create local folder /home/bcsnv/.kde/tmp-Laptop: Permission denied  
trying to create local folder /home/bcsnv/.kde/tmp-Laptop: Permission denied  
trying to create local folder /home/bcsnv/.kde/tmp-Laptop: Permission denied  
trying to create local folder /home/bcsnv/.kde/tmp-Laptop: Permission denied  
trying to create local folder /home/bcsnv/.kde/share: Permission denied       
trying to create local folder /home/bcsnv/.kde/socket-Laptop: Permission denied
kdeinit4: Aborting. bind() failed: Permission denied                           
Could not bind to socket '/home/bcsnv/.kde/socket-Laptop/kdeinit4__0'          
trying to create local folder /home/bcsnv/.kde/cache-Laptop: Permission denied 
KCrash: Application 'kate' crashing...                                         
sock_file=/home/bcsnv/.kde/socket-Laptop/kdeinit4__0                           
Warning: connect() failed: : Permission denied                                 
KCrash cannot reach kdeinit, launching directly.                               
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/cache-Laptop: Permission denied 
trying to create local folder /home/bcsnv/.kde/cache-Laptop: Permission denied 
trying to create local folder /home/bcsnv/.kde/cache-Laptop: Permission denied 
trying to create local folder /home/bcsnv/.kde/cache-Laptop: Permission denied 
trying to create local folder /home/bcsnv/.kde/tmp-Laptop: Permission denied   
trying to create local folder /home/bcsnv/.kde/tmp-Laptop: Permission denied   
trying to create local folder /home/bcsnv/.kde/tmp-Laptop: Permission denied   
trying to create local folder /home/bcsnv/.kde/tmp-Laptop: Permission denied   
trying to create local folder /home/bcsnv/.kde/tmp-Laptop: Permission denied   
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied        
trying to create local folder /home/bcsnv/.kde/share: Permission denied
trying to create local folder /home/bcsnv/.kde/share: Permission denied
trying to create local folder /home/bcsnv/.kde/share: Permission denied
trying to create local folder /home/bcsnv/.kde/share: Permission denied
trying to create local folder /home/bcsnv/.kde/share: Permission denied
trying to create local folder /home/bcsnv/.kde/share: Permission denied
trying to create local folder /home/bcsnv/.kde/share: Permission denied
trying to create local folder /home/bcsnv/.kde/share: Permission denied
trying to create local folder /home/bcsnv/.kde/share: Permission denied
trying to create local folder /home/bcsnv/.kde/share: Permission denied
trying to create local folder /home/bcsnv/.kde/share: Permission denied
trying to create local folder /home/bcsnv/.kde/share: Permission denied
trying to create local folder /home/bcsnv/.kde/share: Permission denied
trying to create local folder /home/bcsnv/.kde/share: Permission denied
trying to create local folder /home/bcsnv/.kde/share: Permission denied
trying to create local folder /home/bcsnv/.kde/share: Permission denied
trying to create local folder /home/bcsnv/.kde/share: Permission denied
trying to create local folder /home/bcsnv/.kde/share: Permission denied
trying to create local folder /home/bcsnv/.kde/share: Permission denied
trying to create local folder /home/bcsnv/.kde/share: Permission denied
trying to create local folder /home/bcsnv/.kde/share: Permission denied
trying to create local folder /home/bcsnv/.kde/share: Permission denied
trying to create local folder /home/bcsnv/.kde/share: Permission denied
```

However, when I run "sudo kate" the program runs fine without any problems.  What may be the cause of this and how can I fix this so that I can run kate normally without sudo privileges?

---

### Post by rCXer on 2010-01-21
My guess is that this is a permissions problem.  Go to "/home/bcsnv/.kde" nautilus.  Right click on the whitespace and choose "Properties". On the "Permissions" tab it should have your username as the owner with "Create and Delete files" for folder access.  Your name should also be selected in the Group field.

If it won't let you change the permissions just use...
```
gksudo nautilus
```

---

### Post by bcasanov on 2010-01-21
Thank you for your reply.  It seems that your suggestion worked.  I had to change permissions for the subfolders too, though, but once I did that, kate launched without incident.

---

