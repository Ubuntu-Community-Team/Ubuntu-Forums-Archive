---
title: "Virtual Box"
date: 2010-09-08
forum: General Help
---

### Post by ankit.vader on 2010-09-08
i've recently started using VirtualBox for running XP. I want a Folder in ubuntu( /home/ankit/folder) to be accessed from windows XP. i tried adding it in shared folder but it didn't work. I also tried transferring that folder to my pendrive, but virtual box didn't show any pendrive. Can someone help me with this...

---

### Post by CharlesA on 2010-09-08
Are you using OSE or the version from virtualbox.org?

File sharing between VM and host can be a bit of a pain in the butt.

Note: You can always create a share in WinXP and connect to it from Ubuntu.

---

### Post by geirha on 2010-09-08
Did you install the guest additions in the windows guest? I think you need those for smb shares to work properly.

---

### Post by ankit.vader on 2010-09-08
> Are you using OSE or the version from virtualbox.org?
I'm using OSE.

> Did you install the guest additions in the windows guest?
No, how can i do that?

---

### Post by CharlesA on 2010-09-08
There should be an option under the devices menu.

Devices > Install Guest additions.

---

### Post by AlexandreP on 2010-09-08
Without installing Guests Additions, you should be able to share folders between your host OS (Ubuntu) and your guest OS (Windows) if you configure your Network settings in VirtualBox to use a bridged connection.

By default, VirtualBox creates a NAT connection between your guest and host, resulting in both OSes can't communicate directly. Using a bridged connection, your guest OS becomes visible in your LAN, just like if your guest OS was running in its own computer. Then, you can manage network shares exactly like if you had two distinct computers.

In VirtualBox, when your virtual machine is not running:
  - Select your virtual machines;
  - Click on "Configuration";
  - Go to "Network" section;
  - In the first tab, which is your guest OS network card, select "Bridge" mode for your connection type;
  - If you have more than one network interface in your physical computer (i.e. WiFi and a wired connection), be sure to bridge your VM connection with your physical connection that is linked to Internet;
  - Finally, apply all the changes and restart your VM.

You should now be able to manage network shares exactly like if you had two distinct computers running two OSes.

---

