---
title: "Cant open update manager or synaptic?"
date: 2011-08-02
forum: General Help
---

### Post by dioxholster on 2011-08-02
synaptic tells me:
"you must manually run sudo dpkg configure -a to correct the problem"

update manager tells me the same thing but also that the software index is broken. And it offered a partial upgrade but it doesnt work or do anything just gets me the aformentioned error message. 

I think this was all cause by me interrupting the last update process by pressing cancel, because it froze or something.

---

### Post by wildmanne39 on 2011-08-02
Hi, partial upgrade is always a bad idea.

Run this in a terminal 
```
sudo apt-get update && sudo apt-get upgrade
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by dioxholster on 2011-08-02
> **wildmanne39 said:**
> Hi, partial upgrade is always a bad idea.

Run this in a terminal 
```
sudo apt-get update && sudo apt-get upgrade
```and post the outcome here by clicking on new reply and click # and paste the information between the brackets.

this is what i got:


> W: Failed to fetch [http://ppa.launchpad.net/lorenzo-carbonell/atareao/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/lorenzo-carbonell/atareao/ubuntu/dists/natty/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/lorenzo-carbonell/atareao/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/lorenzo-carbonell/atareao/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 


---

### Post by wildmanne39 on 2011-08-02
Hi, the ppa's are not on the server so you need to remove them by opening synaptic click on settings,repositories,other software after we get synaptic to open again.

Run these commands 
```
sudo dpkg --configure -a 
```
```
sudo apt-get autoclean
```
```
sudo apt-get clean
```
```
sudo apt-get autoremove
```
```
sudo apt-get update && sudo apt-get upgrade
```
if you get any errors post all of them here.

---

### Post by dogafin on 2011-08-02
i have the same problem!

its giving me this error
> W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/main/source/Sources)  404  Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/restricted/source/Sources)  404  Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/universe/source/Sources)  404  Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/multiverse/source/Sources)  404  Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/main/binary-i386/Packages)  404  Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.92.170 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.


---

### Post by wildmanne39 on 2011-08-02
> **dogafin said:**
> i have the same problem!

its giving me this error
Hi, all of these are old, they are not on the server just follow my instructions in my previous post on opening synaptic and delete all those ppa's.

---

### Post by dioxholster on 2011-08-02
> **wildmanne39 said:**
> Hi, the ppa's are not on the server so you need to remove them by opening synaptic click on settings,repositories,other software after we get synaptic to open again.

Run these commands 
```
sudo dpkg --configure -a 
``````
sudo apt-get autoclean
``````
sudo apt-get clean
``````
sudo apt-get autoremove
``````
sudo apt-get update && sudo apt-get upgrade
```if you get any errors post all of them here.

they all worked except for the last commands which gave the same exact error as before.

> W: Failed to fetch [http://ppa.launchpad.net/lorenzo-carbonell/atareao/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/lorenzo-carbonell/atareao/ubuntu/dists/natty/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/lorenzo-carbonell/atareao/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/lorenzo-carbonell/atareao/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
i have no idea what it means, why are these two sources creating a problem? Do i need to change them?

edit: but opening synaptic works so does that mean its fixed?

---

### Post by wildmanne39 on 2011-08-02
Hi, yes you need to delete them like I said in my previous post using synaptic, will it open now so you can delete the ppa's?

If it will not open try to open it from a terminal with 
```
gksu synaptic
``` 
if it does not open it will at least give you error messages.

---

### Post by dioxholster on 2011-08-02
> **wildmanne39 said:**
> Hi, yes you need to delete them like I said in my previous post using synaptic, will it open now so you can delete the ppa's?

If it will not open try to open it from a terminal with 
```
gksu synaptic
```if it does not open it will at least give you error messages.

i deleted the two ppa's and all works now, thanks for the help!

---

### Post by dogafin on 2011-08-02
okay my problem is synaptic wont open for me
its giving me this 
> E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_intrepid-backports_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

---

### Post by wildmanne39 on 2011-08-02
> **dogafin said:**
> okay my problem is synaptic wont open for me
its giving me thisHi, run these two commands and you should be good to go.
```
sudo rm /var/lib/apt/lists/* -vf
```
```
sudo apt-get update
```

---

### Post by wildmanne39 on 2011-08-02
> **dioxholster said:**
> i deleted the two ppa's and all works now, thanks for the help!Hi, your welcome!would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

### Post by dogafin on 2011-08-02
> **wildmanne39 said:**
> Hi, run these two commands and you should be good to go.
```
sudo rm /var/lib/apt/lists/* -vf
```
```
sudo apt-get update
```


thank you so much!! this helped me alot! it still gave me a few errors but the important part is i can now run updates! thank you :popcorn:

---

### Post by wildmanne39 on 2011-08-02
Hi, your welcome! if it is the ppa's just remove them in synaptic because they are no longer on the server.

---

