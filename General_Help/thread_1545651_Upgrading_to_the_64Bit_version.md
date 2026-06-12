---
title: "Upgrading to the 64Bit version"
date: 2010-08-04
forum: General Help
---

### Post by Forkaster on 2010-08-04
Hi,

I have Ubuntu 10.04 32Bit installed. Is i possible to upgrade to Ubuntu 64Bit without a clean install?

If not, what is the best way to back up configurations and installed packages in order to do a clean install and upgrade to 64bit?

---

### Post by dragos240 on 2010-08-04
I wondered this a while ago. It's possible, like everything is, but you'd need to reorganize your libraries, and reinstall most packages, which would be a nightmare. I'd suggest doing a clean install if you feel you need 64 bit. If you don't need it, it's good to stick to 32 bit.

---

### Post by oldos2er on 2010-08-04
> **Forkaster said:**
> I have Ubuntu 10.04 32Bit installed. Is i possible to upgrade to Ubuntu 64Bit without a clean install?


No. If you have your home folder on its own partition, all your personal settings will be saved if you don't format it during the install.

---

### Post by Zorgoth on 2010-08-04
You can upgrade only by doing a clean install, but it wouldn't be a nightmare;

First save your markings from Synaptic, *being sure to check the box that says "Save full state, not just changes."*  I believe this option is under File>.

Then back up your home directory.

Do a clean install with a temporary user.

Add any external repositories you may use.

Load the Synaptic markings to get all your old packages, and run an update.

Then install any programs you compiled or used a downloaded *.deb to install.

Then create a user with your normal username, and put the backed up home directory in place of /home/<your_user_name>.

Then you should be able to log in as yourself, 64-bit, no more problems.

---

### Post by ed-koala on 2010-08-04
Personally, I doubt there is enough of a performance issue to even worry about it right now.

I'd wait until you intend to upgrade to a different Ubuntu version and then just do a clean install of the 64 bit version then.

---

### Post by Forkaster on 2010-08-05
I might do hjust that. With 2 or 3 months away from the next release there is no need :)

I just want to keep my compiz settings, these were the ones that took me the longest to set up.

---

