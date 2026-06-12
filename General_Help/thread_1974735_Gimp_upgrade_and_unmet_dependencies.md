---
title: "Gimp upgrade and unmet dependencies"
date: 2012-05-06
forum: General Help
---

### Post by SteveTyrer on 2012-05-06
I am using Ubuntu 11.10, and am trying to upgrade Gimp to 2.8.
I have un-installed Gimp 2.6 via the Ubuntu software center and then tried installing Gimp 2.8 from the repository and get the following.

"Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 gimp : Depends: libgimp2.0 (>= 2.7.5) but 2.6.11-2ubuntu4 is to be installed
        Depends: libgegl-0.0-0 (>= 0.1.3-2) but it is not going to be installed
        Depends: libglib2.0-0 (>= 2.31.2) but 2.30.0-0ubuntu4 is to be installed
E: Unable to correct problems, you have held broken packages."

I have limited experience using the command line, can someone please give some help.

Steve

---

### Post by Enigmapond on 2012-05-06
I had the same problem in 12.04 upgrading to the new GIMP. The way I worked it was to purge everything GIMP...then I installed gimp-data first then gimp then anything else. This seems to have worked as it runs fine now.

---

### Post by SteveTyrer on 2012-05-06
> **Enigmapond said:**
> I had the same problem in 12.04 upgrading to the new GIMP. The way I worked it was to purge everything GIMP...then I installed gimp-data first then gimp then anything else. This seems to have worked as it runs fine now.

Good to hear that you got Gimp working, but sorry to show my ignorance how did you purge Gimp from your system?

---

### Post by SeijiSensei on 2012-05-06
```

sudo apt-get purge gimp gimp-*

```

However if you really want to use GIMP 2.8, you should upgrade to 12.04.  The version of 2.8 in the PPA repository is compiled for Precise and may need libraries you don't have.

I'd suggest running "sudo do-release-upgrade" after backing up any files you need to preserve.  Then, to install GIMP 2.8, you'd just need to run these:

```

sudo add-apt-repository ppa:otto-kesselgulasch/gimp
sudo apt-get update
sudo apt-get install gimp

```

Installed cleanly for me on my Kubuntu 12.04 systems.

---

### Post by SteveTyrer on 2012-05-07
> **SeijiSensei said:**
> ```

sudo apt-get purge gimp gimp-*

```However if you really want to use GIMP 2.8, you should upgrade to 12.04.  The version of 2.8 in the PPA repository is compiled for Precise and may need libraries you don't have.

I'd suggest running "sudo do-release-upgrade" after backing up any files you need to preserve.  Then, to install GIMP 2.8, you'd just need to run these:

```

sudo add-apt-repository ppa:otto-kesselgulasch/gimp
sudo apt-get update
sudo apt-get install gimp

```Installed cleanly for me on my Kubuntu 12.04 systems.

Thanks for your help all working okay now, 
The upgrade to 12.04 was not very smooth but all working now with Gimp 2.8 installed

Again thanks 

Steve

---

