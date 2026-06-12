---
title: "Apt authentication issue"
date: 2011-01-21
forum: General Help
---

### Post by shadow85 on 2011-01-21
I keep getting the following error:
[I]
Apt Authentication issue

Problem during package list update. The package list update failed with a authentication failure. This usually happens behind a network proxy server. Please try to click on the "Run this action now" button to correct the problem or update the list manually by running Update Manager and clicking on "Check".

[/I]After clicking run this action now, it installs uptill the last package, and then i get the error:

*W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>*

What is the solution?

---

### Post by plucky on 2011-01-21
> **shadow85 said:**
> I keep getting the following error:
[I]
Apt Authentication issue

Problem during package list update. The package list update failed with a authentication failure. This usually happens behind a network proxy server. Please try to click on the "Run this action now" button to correct the problem or update the list manually by running Update Manager and clicking on "Check".

[/I]After clicking run this action now, it installs uptill the last package, and then i get the error:

*W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>*

What is the solution?


Open **Applications > Ubuntu Software Centre > Edit > Software Sources** and change your Download server to the Main server and then "Close" and it will ask you to "Reload", Do So, and see if the error has gone.

Sometimes download servers get out of step.

Remember to change back to your servers so you get the fastest download.

If you still get the error,open a terminal **(Applications > Accessories > terminal)** and copy and paste this command ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
``` should add the signature key.


Good Luck

---

