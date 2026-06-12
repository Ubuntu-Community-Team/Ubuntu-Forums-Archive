---
title: "Help installing Ubuntu without gui"
date: 2010-07-07
forum: General Help
---

### Post by Mitchell314 on 2010-07-07
With Ubuntu 9.04, how do I install it without Gnome? I've done a quick google search, but all that comes up are references to an install menu selection I don't have or by typing in some parameter stuff, but I don't know where.

Also, this is more of a minor thing, but what are the system requirements of Ubuntu minus gui?

---

### Post by philinux on 2010-07-07
> **Mitchell314 said:**
> With Ubuntu 9.04, how do I install it without Gnome? I've done a quick google search, but all that comes up are references to an install menu selection I don't have or by typing in some parameter stuff, but I don't know where.

Also, this is more of a minor thing, but what are the system requirements of Ubuntu minus gui?

Do you mean the server edition?

---

### Post by snowpine on 2010-07-07
Use the Ubuntu Minimal CD and choose the "Command-Line Install" option. A good how-to here: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

System requirements: [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

Keep in mind 9.04 only has a few months of support left; is there a reason you don't want to use the current release (10.04)?

---

### Post by Mitchell314 on 2010-07-07
> **snowpine said:**
> Use the Ubuntu Minimal CD and choose the "Command-Line Install" option. A good how-to here: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

System requirements: [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

Keep in mind 9.04 only has a few months of support left; is there a reason you don't want to use the current release (10.04)?

Thanks.

I'm using 9.04 because I already have it and I'm too lazy to wait half a day to download a newer distro. I'm running it in a virtual box and I'm trying to conserve RAM since I only have one gigabyte to begin with.

> **philinux said:**
> Do you mean the server edition?

Sorry for the newb question, but what is the server edition?

---

### Post by snowpine on 2010-07-07
> **Mitchell314 said:**
> Thanks.

I'm using 9.04 because I already have it and I'm too lazy to wait half a day to download a newer distro. I'm running it in a virtual box and I'm trying to conserve RAM since I only have one gigabyte to begin with.

You're welcome! :) Actually, you will have to download the same amount whichever version you choose, so you might as well use the latest 10.04. The reason for this is that the 9.04 Live CD you already have isn't capable of doing a Command Line Install (as far as I know). But it will not be a huge download, certainly much less than the roughly 700mb for the full GUI Ubuntu.

If you already have 9.04 installed, and your goal is to trim your memory usage, the easiest option may be to simply boot your existing install into text mode. This would give you the same functionality and RAM usage as a minimal install. I am not 100% sure but I think you accomplish this by disabling the GDM login service. 

> **Mitchell314 said:**
> Sorry for the newb question, but what is the server edition?

Similar to the minimal command line only install, but it also has tools for acting as a file server, print server, hosting web pages, etc.

---

