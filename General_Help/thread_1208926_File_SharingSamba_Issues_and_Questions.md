---
title: "File Sharing/Samba Issues and Questions"
date: 2009-07-09
forum: General Help
---

### Post by Cardnyl on 2009-07-09
I have a few computers on my network with folder shares located within a user's home folder that are set to allow Guest access. The shares were set up while using the desktop manager by creating a folder on the desktop, right clicking the folder and choosing sharing, allowing the workstation to download all of the relevant packages and finally setting the options provided in the sharing dialog window.

What is odd is that none of these settings appear in the smb.conf file on the workstation. I am completely unsure as to where the config files for these shares are kept. Because of this I have been unable to set up a similar share (a folder within a user's directory) exclusively via a console login by modification of the samba configuration file. 

On machines where no desktop manager exist I have only been successful in setting up shares where the base folder is located in the /home directory instead of /home/cardnyl via editing of the smb.conf file. 

```

[public]
    comment = Public Drive
    path = /home/public
    read only = No
    create mask = 0700
    inherit permissions = Yes
    inherit acls = Yes
    inherit owner = Yes
    map hidden = Yes

[test]
    comment = Test
    path = /home/test
    read only = No
    create mask = 0700
    inherit permissions = Yes
    inherit acls = Yes
    inherit owner = Yes
    guest ok = Yes
    map hidden = Yes

[test1]
    path = /home/cardnyl/test1
    read only = No
    create mask = 0700
    inherit permissions = Yes
    inherit acls = Yes
    inherit owner = Yes
    guest only = Yes
    guest ok = Yes



```The snippet above is in use on one of our storage machines. The first 2 shares show up fine and play nicely with our AD server. Users can access these without any issue. The 3rd share does not. Any machines, irregardless of OS are unable to access the test1 share. If the test1 folder is moved out of my home directory and into the base /home folder the share becomes usable. All of the folders in question were set to chmod 777 after creation. Any help with this is appreciated.

---

### Post by doas777 on 2009-07-09
there are a couple fatal flaws to userspace sharing. first, shares are only accessible while the user that created them is logged in on the server. secondly you can't use samba with the network manager, because the host network connection is not enabled until after login (for easy wifi connectivity).

on my samba servers, i always configure my IP in my /etc/network/interfaces file, and install samba via the CLI. then I configure everything samba directly in the config file. I also never share a folder within a users home. 

that way, when samba starts at boot, the network connection is already established, and I can specify user permissions on the share dir without affecting the users security.

my roommate configured samba on a mediabox, but with the GUI install/config and we were never able to get it to work correctly thereafter, even after trying to purge samba and start over from scratch. it may work for you, but we had to rebuild after samba refused to reinstall.

---

### Post by Cardnyl on 2009-07-13
> **doas777 said:**
> there are a couple fatal flaws to userspace sharing. first, shares are only accessible while the user that created them is logged in on the server. secondly you can't use samba with the network manager, because the host network connection is not enabled until after login (for easy wifi connectivity).

on my samba servers, i always configure my IP in my /etc/network/interfaces file, and install samba via the CLI. then I configure everything samba directly in the config file. I also never share a folder within a users home. 

that way, when samba starts at boot, the network connection is already established, and I can specify user permissions on the share dir without affecting the users security.

my roommate configured samba on a mediabox, but with the GUI install/config and we were never able to get it to work correctly thereafter, even after trying to purge samba and start over from scratch. it may work for you, but we had to rebuild after samba refused to reinstall.

Yea I am honestly not sure how these shares really work. I think in a previous edit you mentioned looking within the directory .gvfs but the folder was empty upon inspection. Also the shares ubuntu makes via the sharing dialog box actually allow folks to access them even if no one is signed into the machine and the box is sitting at a login screen. I ended up giving up on trying to figure out how these work and instead moved the folder I wished to share to the base /home directory and sharing it via smb.conf like the rest of the shares I've made thus far. 

Unfortunately a new issue has cropped up that I hadn't expected. The machine hosting the shares are attached to our Windows AD server and authenticate all of the windows users correctly allowing them to do as I wish. Oddly enough its my Linux machines that refuse to allow them to do anything other than create folders. I am trying to figure out if the issue lies in the smb.conf configuration or the cifs mount entry in the fstab file.

---

