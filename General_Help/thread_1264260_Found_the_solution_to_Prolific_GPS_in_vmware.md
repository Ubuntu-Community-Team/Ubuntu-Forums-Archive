---
title: "Found the solution to Prolific GPS in vmware"
date: 2009-09-12
forum: General Help
---

### Post by oakgrove on 2009-09-12
If you have been trying to get the GPS that comes with Microsoft Streets and Trips working in vmware using any kernel after 2.6.26 and couldn't get it to work, I have a solution.  First let me say, I have been wrestling with this problem for months and months now and have searched the net up and down to no avail.  I even dropped Ubuntu and went to Debian as with the rolling testing distro they have, I could keep the official 2.6.26 kernel and still get upgrades to everything else like Gnome 2.26 and KDE4.  But now 26 is getting a little stale and I'd love to move back to Ubuntu...  But enough about that.  Here's what worked for me.

I plug in the GPS receiver, then at the terminal, I do;
```

$ sudo modprobe -r pl2303

```
This unloads the pl2303 kernel module that automatically loads when you plug it in.  I'm not sure why but the module doesn't initialize properly.

Then, I boot up the virtual machine.  At which point I do the above command again as it seems to reload the module when vmware probes USB devices.  I then connect the GPS adapter to the virtual machine using the Removable Devices in the VM menu in vmware and presto! it works.

So that you don't have to do this every time, you can just blacklist the pl2303 module like this:
```

sudo cp /etc/modprobe.d/blacklist.conf /etc/modprobe.d/blacklist.conf.bak
sudo echo 'blacklist pl2303' >> /etc/modprobe.d/blacklist.conf

```
Now, it should never be automatically invoked again.

Hope this helps someone and if further explanation on any points is requested, just say so.

---

