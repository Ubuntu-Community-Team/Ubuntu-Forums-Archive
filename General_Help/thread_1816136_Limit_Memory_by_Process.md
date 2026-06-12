---
title: "Limit Memory by Process"
date: 2011-08-01
forum: General Help
---

### Post by jfreak53 on 2011-08-01
Is there a way to limit memory usage by process name?  Like cpulimit does with cpu usage.  I know of ulimit but that is based on shell usage.

I am running an app as a daemon and I want to limit how much ram it uses, cold hard RAM.  I know it spawns two or three version of itself while running, so that's why I don't think ulimit will work.

I want to limit it to 80MB total used by all processes together.  Any ideas on how to do this?

---

### Post by bodhi.zazen on 2011-08-01
Yes, the new method is to use cgroups.

Fedora / RHEL has the best documentation on this, but, as it is driven by the kernel should be the same on Ubuntu or most any distro:

[http://docs.fedoraproject.org/en-US/Fedora/15/html/Resource_Management_Guide/ch01.html](http://docs.fedoraproject.org/en-US/Fedora/15/html/Resource_Management_Guide/ch01.html)

---

### Post by jfreak53 on 2011-08-12
Ok, I've done some reading on it and control groups sounds awesome.  Problem is this will be implemented on a VPS unit and that requires a custom compiled kernel, kind of hard.

Is there any other way to limit memory usage?  I tried ulimit and it didn't seem to work very good actually.

---

### Post by bodhi.zazen on 2011-08-12
Suppose it depends on what you are using for a "VPS" openvz ?

---

### Post by jfreak53 on 2011-08-13
That's the deal yes, OpenVZ.  Xen from what I hear does have the ability to do custom kernels, but normally they are a bit more expensive and also my NOC will then charge me to re-compile since I have "0" experience doing that.

So I am wondering if there is another solution, maybe not as good ha ha, but something comparable.

It would be OpenVZ with CentOS 5 probably, though I could do Ubuntu if it comes with something better of course.

---

### Post by bodhi.zazen on 2011-08-13
Do you have access to the host node ?

Yes, for openvz I would use either Centos or Proxmox. Proxmox is Debian and has a web interface.

In general you would set the resources available to the VPS (beancounters) and quotas. 

See:

[http://wiki.openvz.org/Resource_management](http://wiki.openvz.org/Resource_management)

[http://www.techrepublic.com/blog/opensource/gain-fine-control-in-openvz-with-resource-management/636](http://www.techrepublic.com/blog/opensource/gain-fine-control-in-openvz-with-resource-management/636)

But I do not think you can get finer grained control then that.

If, however, you can access the host node you may be able to use cgroups, I am not sure I have not done that with openvz.

---

### Post by jfreak53 on 2011-08-13
Yeah :(, unfortunately I can't access anything as far as that goes, since it's a purchased VPS not on my own server.  Ok, well thanks I might have to go the route then of Xen, thanks for the help.

---

