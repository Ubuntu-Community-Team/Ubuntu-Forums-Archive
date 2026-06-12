---
title: "Ubuntu Software Center"
date: 2010-02-24
forum: General Help
---

### Post by JacobVengeance on 2010-02-24
I recently installed some updates and bug fixes and now Ubuntu Software Center will not open. It starts to load and never opens. Is there a command I can use to fix it or rollback?

---

### Post by spiderbatdad on 2010-02-24
Are you able to launch synaptic package manager?
Asking to determine whether dpkg is in an unusable state.

---

### Post by JacobVengeance on 2010-02-24
> **spiderbatdad said:**
> Are you able to launch synaptic package manager?
Asking to determine whether dpkg is in an unusable state.

It did not run at first, but I put in a command I found and got that working. USC does not though.

---

### Post by mpt on 2010-03-06
> **JacobVengeance said:**
> It did not run at first, but I put in a command I found and got that working. USC does not though.

What happens if you type “software-center” in a Terminal window? If you get an error message, can you copy and paste it here?

---

### Post by patrick@e-lelie.be on 2010-03-08
I got the same problem

mark@mark-laptop:~$ software-center
Traceback (most recent call last):
  File "/usr/bin/software-center", line 78, in <module>
    from softwarecenter.app import SoftwareCenterApp
  File "/usr/share/software-center/softwarecenter/app.py", line 41, in <module>
    from view.viewswitcher import ViewSwitcher, ViewSwitcherList
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 19, in <module>
    import apt
ImportError: No module named apt
mark@mark-laptop:~$ sudo apt-get install apt
[sudo] password for mark: 
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd       
De status informatie wordt gelezen... Klaar
apt is reeds de nieuwste versie.
0 pakketten opgewaardeerd, 0 pakketten nieuw geïnstalleerd, 0 te verwijderen en 0 niet opgewaardeerd.
mark@mark-laptop:~$ 

Can somebody help ?

---

### Post by mpt on 2010-03-08
> **patrick@e-lelie.be said:**
> ImportError: No module named apt

That’s really weird. Do you have python-apt installed?

Otherwise, use “ubuntu-bug software-center” to report the bug, and copy and paste that Traceback into the bug report. Thanks!

---

### Post by patrick@e-lelie.be on 2010-03-10
yes,  I got python-apt installed
shall I remove it ?

---

### Post by mpt on 2010-03-10
No, please just report a bug in the way I described. Thanks!

---

### Post by Running_Dualboot on 2010-03-10
> **patrick@e-lelie.be said:**
> I got the same problem

mark@mark-laptop:~$ software-center
Traceback (most recent call last):
  File "/usr/bin/software-center", line 78, in <module>
    from softwarecenter.app import SoftwareCenterApp
  File "/usr/share/software-center/softwarecenter/app.py", line 41, in <module>
    from view.viewswitcher import ViewSwitcher, ViewSwitcherList
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 19, in <module>
    import apt
ImportError: No module named apt
mark@mark-laptop:~$ sudo apt-get install apt
[sudo] password for mark: 
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd       
De status informatie wordt gelezen... Klaar
apt is reeds de nieuwste versie.
0 pakketten opgewaardeerd, 0 pakketten nieuw geïnstalleerd, 0 te verwijderen en 0 niet opgewaardeerd.
mark@mark-laptop:~$ 

Can somebody help ?

Try running as root buy typing:

```
su
Software-center
```

---

### Post by mpt on 2010-03-10
Why would that make any difference?

---

### Post by patrick@e-lelie.be on 2010-03-11
you are right MPT
I tried and it doesn't make a difference 
Can you give me some more explication about reporting a bug ?
Where do I past this info ?

---

### Post by plucky on 2010-03-11
> **patrick@e-lelie.be said:**
> you are right MPT
I tried and it doesn't make a difference 
Can you give me some more explication about reporting a bug ?
Where do I past this info ?

Alt-F2 and type in > ubuntu-bug software-center and it will gather information about your system and take you to launchpad to report the bug assuming you have a launchpad account.

Good Luck

---

### Post by patrick@e-lelie.be on 2010-03-11
I think I got a problem ;-)

```
mark@mark-laptop:~$ ubuntu-bug
Traceback (most recent call last):
  File "/usr/share/apport/apport-gtk", line 16, in <module>
    from apport import unicode_gettext as _
  File "/usr/lib/python2.6/dist-packages/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/usr/lib/python2.6/dist-packages/apport/report.py", line 21, in <module>
    import fileutils
  File "/usr/lib/python2.6/dist-packages/apport/fileutils.py", line 16, in <module>
    from packaging_impl import impl as packaging
  File "/usr/lib/python2.6/dist-packages/apport/packaging_impl.py", line 18, in <module>
    import apt
ImportError: No module named apt

```

What do I do now ?

---

