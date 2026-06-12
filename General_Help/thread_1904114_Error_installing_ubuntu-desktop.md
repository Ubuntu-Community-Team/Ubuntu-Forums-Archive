---
title: "Error installing ubuntu-desktop"
date: 2012-01-04
forum: General Help
---

### Post by mrbambocha on 2012-01-04
Im getting the error that the installation cant download these files from the server, and ask if I want to continue. Should I proceed?

Message:

W: Misslyckades med att hämta [http://ro.archive.ubuntu.com/ubuntu/pool/main/b/banshee/banshee_2.2.1-1ubuntu2_i386.deb](http://ro.archive.ubuntu.com/ubuntu/pool/main/b/banshee/banshee_2.2.1-1ubuntu2_i386.deb)
  404  Not Found


W: Misslyckades med att hämta [http://ro.archive.ubuntu.com/ubuntu/pool/main/b/banshee/banshee-extension-soundmenu_2.2.1-1ubuntu2_i386.deb](http://ro.archive.ubuntu.com/ubuntu/pool/main/b/banshee/banshee-extension-soundmenu_2.2.1-1ubuntu2_i386.deb)
  404  Not Found


W: Misslyckades med att hämta [http://ro.archive.ubuntu.com/ubuntu/pool/main/u/ubuntuone-client/python-ubuntuone-client_2.0.0-0ubuntu2.2_all.deb](http://ro.archive.ubuntu.com/ubuntu/pool/main/u/ubuntuone-client/python-ubuntuone-client_2.0.0-0ubuntu2.2_all.deb)
  404  Not Found


W: Misslyckades med att hämta [http://ro.archive.ubuntu.com/ubuntu/pool/main/u/ubuntuone-client/ubuntuone-client_2.0.0-0ubuntu2.2_all.deb](http://ro.archive.ubuntu.com/ubuntu/pool/main/u/ubuntuone-client/ubuntuone-client_2.0.0-0ubuntu2.2_all.deb)
  404  Not Found


W: Misslyckades med att hämta [http://ro.archive.ubuntu.com/ubuntu/pool/main/u/ubuntuone-client/libsyncdaemon-1.0-1_2.0.0-0ubuntu2.2_i386.deb](http://ro.archive.ubuntu.com/ubuntu/pool/main/u/ubuntuone-client/libsyncdaemon-1.0-1_2.0.0-0ubuntu2.2_i386.deb)
  404  Not Found


W: Misslyckades med att hämta [http://ro.archive.ubuntu.com/ubuntu/pool/main/b/banshee/banshee-extension-ubuntuonemusicstore_2.2.1-1ubuntu2_i386.deb](http://ro.archive.ubuntu.com/ubuntu/pool/main/b/banshee/banshee-extension-ubuntuonemusicstore_2.2.1-1ubuntu2_i386.deb)
  404  Not Found


W: Misslyckades med att hämta [http://ro.archive.ubuntu.com/ubuntu/pool/main/u/unity/unity-services_4.24.0-0ubuntu2b1_i386.deb](http://ro.archive.ubuntu.com/ubuntu/pool/main/u/unity/unity-services_4.24.0-0ubuntu2b1_i386.deb)
  404  Not Found


W: Misslyckades med att hämta [http://ro.archive.ubuntu.com/ubuntu/pool/main/u/unity/libunity-core-4.0-4_4.24.0-0ubuntu2b1_i386.deb](http://ro.archive.ubuntu.com/ubuntu/pool/main/u/unity/libunity-core-4.0-4_4.24.0-0ubuntu2b1_i386.deb)
  404  Not Found


W: Misslyckades med att hämta [http://ro.archive.ubuntu.com/ubuntu/pool/main/u/unity/unity-common_4.24.0-0ubuntu2b1_all.deb](http://ro.archive.ubuntu.com/ubuntu/pool/main/u/unity/unity-common_4.24.0-0ubuntu2b1_all.deb)
  404  Not Found


W: Misslyckades med att hämta [http://ro.archive.ubuntu.com/ubuntu/pool/main/u/unity/unity_4.24.0-0ubuntu2b1_i386.deb](http://ro.archive.ubuntu.com/ubuntu/pool/main/u/unity/unity_4.24.0-0ubuntu2b1_i386.deb)
  404  Not Found


W: Misslyckades med att hämta [http://ro.archive.ubuntu.com/ubuntu/pool/main/u/unity-lens-applications/unity-lens-applications_0.4.12-0ubuntu2_i386.deb](http://ro.archive.ubuntu.com/ubuntu/pool/main/u/unity-lens-applications/unity-lens-applications_0.4.12-0ubuntu2_i386.deb)
  404  Not Found

---

### Post by 73ckn797 on 2012-01-04
Maybe change the server that you are down loading from. Software Sources is where you can change it.

---

### Post by mrbambocha on 2012-01-04
I did it. But bow its says theres a missing file in lubuntu and it wants to delte the lubuntu -desktop. What should I do? (And ubuntu wasnt installed)

---

### Post by Catharsis on 2012-01-05
> **mrbambocha said:**
> I did it. But bow its says theres a missing file in lubuntu and it wants to delte the lubuntu -desktop. What should I do? (And ubuntu wasnt installed)

What's saying there's a missing file? Did you get that message while trying to install ubuntu-desktop? I'm confused.

Could you please post the output of:
```
sudo apt-get update && sudo apt-get install -f
```
Just don't agree to remove anything.

---

