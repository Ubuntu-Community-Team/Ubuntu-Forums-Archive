---
title: "Can't install GDM2 in Natty"
date: 2011-05-02
forum: General Help
---

### Post by Aboomer90 on 2011-05-02
Hey guys!

Sorry if this is in the wrong spot.

I tried to install GDM2 Setup to change my login screen theme on  my fresh Natty x64 install.

Through the terminal, I get this message:

$ sudo apt-get install python-gdm2setup
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 python-gdm2setup : Depends: python (< 2.7) but 2.7.1-0ubuntu5 is to be installed
E: Broken packages


Python is too new...?

Installing through the .deb results in the same error.

Any ideas? or any way for me to manually add GDM2 themes to Natty?

---

### Post by wilee-nilee on 2011-05-02
> **Aboomer90 said:**
> Hey guys!

Sorry if this is in the wrong spot.

I tried to install GDM2 to change login screen on my fresh Natty x64 install.

Through the terminal, I get this message:

$ sudo apt-get install python-gdm2setup
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 python-gdm2setup : Depends: python (< 2.7) but 2.7.1-0ubuntu5 is to be installed
E: Broken packages


Python is too new...?

Installing through the .deb results in the same error.

Any ideas? or any way for me to manually add GDM2 themes to Natty?

Fair warning there are multiple threads on login problems so be careful here. Have that baby backed up if it is your main setup.

---

### Post by Aboomer90 on 2011-05-02
> **wilee-nilee said:**
> Fair warning there are multiple threads on login problems so be careful here. Have that baby backed up if it is your main setup.

Whoops, my bad... I can log in to Ubuntu just fine, I just wanted to be able to change the theme to a custom theme (particularly an OSX theme). Updated my first post to clarify.

---

### Post by ~Plue on 2011-05-02
> **Aboomer90 said:**
> 
Any ideas? or any way for me to manually add GDM2 themes to Natty?
[Add gnome-appearance-properties to gdm autostart applications]("http://ubuntuforums.org/showpost.php?p=10240432&postcount=3")

---

### Post by Aboomer90 on 2011-05-02
I remember seeing that somewhere else. It works, but the theme that I want to install refuses.

If that's the solution, then this thread is solved.

---

