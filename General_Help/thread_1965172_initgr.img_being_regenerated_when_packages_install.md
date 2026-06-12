---
title: "initgr.img being regenerated when packages installed"
date: 2012-04-25
forum: General Help
---

### Post by elliott94 on 2012-04-25
Hello.

I was recently working on a Ubuntu system, and noticed that when some packages were installed (for example, update-notifier), that apt was telling me thatupdate-initramfs was running and regenerating initgr.img, even when the packages wern't related to the kernel.

I've done some research, and it looks like this is a core system file that is necessary for booting.

So I guess my question is, why is this particular file being regenerated, even when apt is installing a package that isn't related to the kernel at all? Can this cause any damage?

Here's a sample from an apt log.

 Setting up libgnome2-vfs-perl (1.081-1build1) ...                               
 Setting up libgnome2-perl (1.042-2build1) ...                                   
 Setting up libgnomevfs2-extra (1:2.24.2-1ubuntu2) ...                           
 Processing triggers for libc-bin ...                                            
 ldconfig deferred processing now taking place                                   
 Processing triggers for initramfs-tools ...                                     
 update-initramfs: Generating /boot/initrd.img-2.6.32-31-server                  
 Processing triggers for python-support ...                                      
 
Thanks.

---

