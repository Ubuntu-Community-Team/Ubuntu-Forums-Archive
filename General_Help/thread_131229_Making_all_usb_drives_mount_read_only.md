---
title: "Making all usb drives mount read only?"
date: 2006-02-16
forum: General Help
---

### Post by alavaliant on 2006-02-16
Anybody know a good way to do this?  My company is a little paranoid about security and files being taken off site.  I've been told by upper management we have two choices for our kubuntu desktop machines.  Either users have no rights to use usb media or else it must always be read only access so they can upload photos and etc they have taken themselves but they can put anything off the pc onto the device.

I've researched into HAL and ivman and both seem to have loads of policy options but non to set the mounts as ro.  Plus they call pmount which a user could call manually without -r if they were smart.

Right now my department is thinking making a setuid c wrapper app to place pmount which just calls a renamed pmount binary with the -r option.  So that way no matter what the user or HAL tells pmount to do all the things pmount mounts will be mounted as read only.

It seems an ugly hack to me so I was wondering if anybody has a better way to do it?

Thanks

---

