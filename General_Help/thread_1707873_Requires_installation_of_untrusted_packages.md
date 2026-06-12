---
title: "Requires installation of untrusted packages"
date: 2011-03-15
forum: General Help
---

### Post by manojps on 2011-03-15
When I tried to update my **ubuntu 10.10** **Maverick** through **update manager**  the following message appeares 
"Requires installation of untrusted packages

The action would require the installation of packages from not authenticated sources."

What to be done????????:(:(

---

### Post by Mark_in_Hollywood on 2011-03-15
If you have "third party" software installed, they are likely to be the reason you are seeing that message.

I can't possibly know what you have installed on your computer, but I sometimes see that message and I go ahead and install anyway. However, I know what is installed and why I'm seeing that message.

If you chose to install those packages, it typically won't do any harm.

---

### Post by manojps on 2011-03-16
On the details window following is displayed

"bash-completion brasero brasero-cdrkit brasero-common libbrasero-media1 libglib2.0-0 libglib2.0-data libpoppler-glib5 libpoppler7 libwxbase2.8-0 libwxgtk2.8-0 linux-firmware pm-utils poppler-utils python-wxgtk2.8 python-wxversion rhythmbox rhythmbox-plugin-cdrecorder rhythmbox-plugins tar tzdata tzdata-java xkb-data xserver-xorg-video-geode xserver-xorg-video-intel"

Please Help.........

---

### Post by Mark_in_Hollywood on 2011-03-16
Either open your Update Manager which is got by clicking

System

Administration

pulling down to Update Manager, and then clicking

Check

wait for the updates and then try to reinstall.

Or open your Terminal and type

sudo apt-get update

with both of the above, you will be asked to enter your password.

with the Terminal, you will have to manually update those packages. With Update Manager, you will no.

Hang in there, I know how scary this looks.

Also, try reading this page:

[https://help.ubuntu.com/community/Repositories/Ubuntu#Authentication%20Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Authentication%20Tab)

but let's keep it simple, first.

---

### Post by manojps on 2011-04-03
Now the following message appears


"Failed to lock the package manager

Check if you are currently running another software management tool, e.g. Synaptic or aptitude. Only one tool is allowed to make changes at a time."


But presently i am using only update manager from the system menu. What to do??????????

---

### Post by Mark_in_Hollywood on 2011-05-08
I apologize for the delay in getting back to you. Shortly after my last response, I got a flu and after a week of bed rest, I had forgotten.

Please try this here:


[http://www.liberiangeek.net/2010/10/fix-requires-installation-untrusted-packages-error-ubuntu-10-10-maverick-meerkat/](http://www.liberiangeek.net/2010/10/fix-requires-installation-untrusted-packages-error-ubuntu-10-10-maverick-meerkat/)

---

### Post by Nodaki on 2011-05-09
Mark in Hollywood's link worked at fixing this problem in my Natty Narwhal install.  Sun Java was the culprit...need it for use of Juniper SSL VPN.

---

### Post by manojps on 2011-05-11
> **Mark_in_Hollywood said:**
> I apologize for the delay in getting back to you. Shortly after my last response, I got a flu and after a week of bed rest, I had forgotten.

Please try this here:


[http://www.liberiangeek.net/2010/10/fix-requires-installation-untrusted-packages-error-ubuntu-10-10-maverick-meerkat/](http://www.liberiangeek.net/2010/10/fix-requires-installation-untrusted-packages-error-ubuntu-10-10-maverick-meerkat/)

It worked:)
Thank you.............:popcorn::KS

---

