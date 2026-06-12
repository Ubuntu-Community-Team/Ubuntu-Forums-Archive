---
title: "Kpackagekit was rejecting (correct!) password"
date: 2010-01-12
forum: General Help
---

### Post by Jota37 on 2010-01-12
Hi,

This is not a question really, but a solution to an annoying problem I've had for a while and solved today, by reading a couple of posts that did NOT have the same problem as mine... but the solution worked for me too, so there! :-)

The problem: when kpackagekit would prompt me to update packages, it would ask for my password. I would enter it, and the dialog would reject it with the message "incorrect password, please try again". Over and over. The password WAS correct -- it worked in Synaptic and on the command line using sudo, and obviously it also worked for logging in.

I suddenly had a hunch that kpackagekit might not be the culprit, and that authentication was being done by a different program -- and lo and behold, the dialog actually said policykit up there...

So, searching for policykit problems out there, I ended up seeing someone reinstalling theirs for their problem (which happened to be different from mine). The code to do that, in the command line:

```
sudo apt-get install --reinstall policykit
```

After that, entering the password after kpackagekit prompts me to has worked fine and the updates happen as nature intended. :-)

I hope I save someone some grief with this post, heh.

Cheers
J

---

### Post by upa on 2010-02-06
I have the same problem, but when uninstalling packages. "Incorrect password, please try again". I reinstalled policykit, and now the behavior changed, after entering my password in kpackageKit, always when uninstalling packages, a windows stays on top with the following title: "Unknown role type - KPackageKit" and the text "Waiting for the service to start", and with a button "Hide". By clicking "Hide" it returns to KPackageKit main window but the selected packages are not removed. 

I appreciate any help. Thanks in advance

---

### Post by Jota37 on 2010-02-06
Yeah, I still don't know what's going on. I thought I had solved it, but I spoke too soon.

If I reinstall policykit, it works ONCE only. So, **every time** I want to upgrade packages, I need to reinstall policykit **before** I can do it. A pain in the neck.

And since I have been doing it the fastest way (on the command-line), it is much better to just suck it up and upgrade the packages from there and be done with it:

```
sudo apt-get upgrade
```

This is a very irritating issue.

---

### Post by upa on 2010-02-07
In my case it olny rejects correct password when uninnstalling packages. It did not fail when validating my password in Settings-->Edit Software Sources for example. I am using Synaptic Package Manager as a workaround, it works well, but I want to fix this problem.

---

### Post by upa on 2010-02-07
I have found a workaround to my problem. It is not the solution I wanted because now KpackageKit does not prompt for any password at all, but at least I can uninstall packages.

[https://bugs.launchpad.net/ubuntu/+bug/518416](https://bugs.launchpad.net/ubuntu/+bug/518416)

---

