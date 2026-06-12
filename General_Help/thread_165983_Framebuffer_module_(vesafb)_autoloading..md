---
title: "Framebuffer module (vesafb) autoloading."
date: 2006-04-25
forum: General Help
---

### Post by prokher on 2006-04-25
Hiall. 
According to my previous topic ([http://ubuntuforums.org/showthread.php?t=165509](http://ubuntuforums.org/showthread.php?t=165509)) i have a question. Why when i use "splash" with "vga=835" kernel parameters (default) vesafb loads automatically without adding entries to /etc/modules or in any other place. But if i remove "splash" (but vga=835 is still there) vesafb doesn't loaded and i see blackscreen in loading process. How can i force kernel to load vesafb automatically like when "splash" parameter set? Of course i can use /etc/modules, but in this case large part of loading process looks very awful without framebufer.
p.s. i use latest dapper with all updates.

---

