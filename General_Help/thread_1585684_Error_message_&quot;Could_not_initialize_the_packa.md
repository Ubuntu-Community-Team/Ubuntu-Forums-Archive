---
title: "Error message: &quot;Could not initialize the package information&quot;"
date: 2010-09-30
forum: General Help
---

### Post by techiewannabe on 2010-09-30
I get the following error message when I try to update using Synaptic. (See attached screen shot.)

Your help with this would be appreciated. I'm not real confident with the command line yet, but I can certainly cut and paste suggested commands.

Thanks.

---

### Post by andrewthomas on 2010-10-01
Reboot and then enter into terminal
 
```
 
sudo aptitude update && sudo aptitude safe-upgrade

```
If there are any errors, please post the full output.  
 
Alternately, if it wants to remove something that you are not sure of, then post that output.

---

### Post by techiewannabe on 2010-10-02
andrewthomas:
Thanks for your suggestions and my apologies for taking so long to get back to you. 
I did what you suggested and got the following messages in the terminal:

[INDENT][sudo] password for mountlings: 
W: Duplicate sources.list entry [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_jaunty_partner_binary-i386_Packages)
E: Read error - read (5 Input/output error)
E: The package lists or status file could not be parsed or opened.
W: Duplicate sources.list entry [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_jaunty_partner_binary-i386_Packages)
E: Read error - read (5 Input/output error)
E: The package lists or status file could not be parsed or opened.
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US       
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg [198B]  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg                  
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg [198B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release [57.9kB]    
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release                          
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release [57.9kB]              
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages                        
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Sources                         
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages [118kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages [150kB]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages [243kB]     
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages [323kB]    
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages [9861B]   
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages [3789B]  
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages [2001B]   
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages [2590B]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages                                                   
  Could not open file /var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_jaunty-updates_multiverse_binary-i386_Packages.decomp - open (30 Read-only file system)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages                                                   
  Could not open file /var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_jaunty-updates_restricted_binary-i386_Packages.decomp - open (30 Read-only file system)
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages                                                          
  Could not open file /var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_jaunty-security_main_binary-i386_Packages.decomp - open (30 Read-only file system)
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages                                                    
  Could not open file /var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_jaunty-security_multiverse_binary-i386_Packages.decomp - open (30 Read-only file system)
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages                                                    
  Could not open file /var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_jaunty-security_restricted_binary-i386_Packages.decomp - open (30 Read-only file system)
Fetched 969kB in 30s (31.8kB/s)                                                                                       
W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened.
E: Couldn't rebuild package cache
W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened.

W: Duplicate sources.list entry [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_jaunty_partner_binary-i386_Packages)
E: Read error - read (5 Input/output error)
E: The package lists or status file could not be parsed or opened.
mountlings@mountlings-compaq-laptop:~$ 

[/INDENT]Your ideas?

Thanks.

---

### Post by sikander3786 on 2010-10-02
Try this from a terminal and make sure that you are not running out of disc space.

```

df -h

```

You can manually remove **archive.canonical.com_ubuntu_dists_jaunty_partner_ binary-i386_Packages** from (you'll need root privileges for that)

```

/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_jaunty_partner_ binary-i386_Packages
```

And then run

```

sudo apt-get update

```

And that file should be automatically recreated.

Also you've got duplicate entries in your sources.list. Post the output of

```

cat /etc/apt/sources.list

```

---

### Post by techiewannabe on 2010-10-02
sikander3786:
Thanks for your suggestions. Here is the text from the commands that I entered as you suggested.

[INDENT]mountlings@mountlings-compaq-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              71G   14G   54G  21% /
tmpfs                 565M     0  565M   0% /lib/init/rw
varrun                565M  320K  564M   1% /var/run
varlock               565M     0  565M   0% /var/lock
udev                  565M  156K  565M   1% /dev
tmpfs                 565M   92K  565M   1% /dev/shm
lrm                   565M  2.2M  563M   1% /lib/modules/2.6.28-19-generic/volatile
mountlings@mountlings-compaq-laptop:~$ /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_jaunty_partner_ binary-i386_Packages
bash: /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_jaunty_partner_: No such file or directory
mountlings@mountlings-compaq-laptop:~$ sudo apt-get update
[sudo] password for mountlings: 
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg [198B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US
Get:2 [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg [198B]
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-en_US        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg [198B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release [57.9kB]
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release                          
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release [57.9kB]             
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages                       
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Sources                        
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages [118kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages [150kB]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages [243kB]     
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages [323kB]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages [9861B]
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages [3789B] 
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages [2001B] 
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages [2590B]
Fetched 969kB in 3s (255kB/s)                      
Reading package lists... Error!
W: Duplicate sources.list entry [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_jaunty_partner_binary-i386_Packages)
E: Read error - read (5 Input/output error)
E: The package lists or status file could not be parsed or opened.
mountlings@mountlings-compaq-laptop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main universe restricted multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) jaunty-security universe main multiverse restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe main multiverse restricted
mountlings@mountlings-compaq-laptop:~$ 
[/INDENT]
I'm open to your suggestions.

---

### Post by mörgæs on 2010-10-02
Since support for 9.04 is about to run out, I would go for a clean install of 10.04.

---

### Post by techiewannabe on 2010-10-02
morgaes:

I agree with you but I tried 10.04 and had a lot of trouble with it. I was going to create another partition for 10.04 and play with it until I could get it to work properly. In the meantime, I planned on continuing to use Jaunty.

techiewannabe

---

### Post by sikander3786 on 2010-10-03
You just copied the path I typed above. It was not the command to delete, just the path. Here's the command. Just copy paste it.

```

sudo rm /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_jaunty_partner_ binary-i386_Packages

```

And now again,

```
sudo apt-get update
```

---

### Post by techiewannabe on 2010-10-03
Thanks siklander3786 for your suggestions. 

Here is the text of the message I received after entering the recommended commands:

[PHP]mountlings@mountlings-compaq-laptop:~$ sudo rm /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_jaunty_partner_ binary-i386_Packages
[sudo] password for mountlings: 
rm: cannot remove `/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_jaunty_partner_': No such file or directory
rm: cannot remove `binary-i386_Packages': No such file or directory
mountlings@mountlings-compaq-laptop:~$ 
[/PHP]Other ideas?

I appreciate your willingness to work on this.

---

### Post by sikander3786 on 2010-10-03
Sorry there was a typo in your first post and I just copied that. It is the space between 'partner_' and 'binary-i386'. Try this command,

```
sudo rm /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_jaunty_partner_binary-i386_Packages

```

---

### Post by techiewannabe on 2010-10-03
Thanks for your note, sikander3786.

I believe that I followed your directions accurately. (?) Here is the output.

[PHP]mountlings@mountlings-compaq-laptop:~$ sudo rm /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_jaunty_partner_binary-i386_Packages
[sudo] password for mountlings: 
mountlings@mountlings-compaq-laptop:~$ sudo apt-get update
Hit http://archive.canonical.com jaunty Release.gpg                            
Ign http://archive.canonical.com jaunty/partner Translation-en_US              
Hit http://archive.canonical.com jaunty Release                                
Hit http://archive.canonical.com jaunty/partner Sources                        
Get:1 http://archive.canonical.com jaunty/partner Packages [4333B]         
Hit http://archive.ubuntu.com jaunty Release.gpg                               
Ign http://archive.ubuntu.com jaunty/main Translation-en_US                
Ign http://archive.ubuntu.com jaunty/universe Translation-en_US
Ign http://archive.ubuntu.com jaunty/restricted Translation-en_US
Ign http://archive.ubuntu.com jaunty/multiverse Translation-en_US
Hit http://archive.ubuntu.com jaunty-updates Release.gpg
Ign http://archive.ubuntu.com jaunty-updates/universe Translation-en_US
Ign http://archive.ubuntu.com jaunty-updates/main Translation-en_US
Ign http://archive.ubuntu.com jaunty-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com jaunty-updates/restricted Translation-en_US
Hit http://archive.ubuntu.com jaunty Release
Hit http://security.ubuntu.com jaunty-security Release.gpg          
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_US
Hit http://archive.ubuntu.com jaunty-updates Release
Ign http://security.ubuntu.com jaunty-security/main Translation-en_US
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_US
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_US
Hit http://archive.ubuntu.com jaunty/main Packages
Hit http://archive.ubuntu.com jaunty/universe Packages
Hit http://archive.ubuntu.com jaunty/restricted Packages
Hit http://archive.ubuntu.com jaunty/multiverse Packages
Hit http://security.ubuntu.com jaunty-security Release
Hit http://archive.ubuntu.com jaunty-updates/universe Packages
Hit http://archive.ubuntu.com jaunty-updates/main Packages
Hit http://archive.ubuntu.com jaunty-updates/multiverse Packages
Hit http://archive.ubuntu.com jaunty-updates/restricted Packages
Hit http://security.ubuntu.com jaunty-security/universe Packages
Hit http://security.ubuntu.com jaunty-security/main Packages
Hit http://security.ubuntu.com jaunty-security/multiverse Packages
Hit http://security.ubuntu.com jaunty-security/restricted Packages
Fetched 4333B in 4s (1003B/s)
Reading package lists... Error!
E: Read error - read (5 Input/output error)
E: The package lists or status file could not be parsed or opened.
mountlings@mountlings-compaq-laptop:~$ [/PHP]Again, I appreciate your willingness to work with me on this.

Thanks.

---

### Post by sikander3786 on 2010-10-04
Fist of all deselect all the enabled repositories (the ones from other software tab too) from System > Administration > Software Sources. Reload the package information. Now again enable all the repositories and once again reload the package information. If successful, stop here, if unsuccessful, proceed reading.

Try to remove the package information lists.

```
sudo mv /var/lib/apt/lists /var/lib/apt/lists.bad
```

```
sudo apt-get update
```

If still is unsuccessful, try changing the update servers from Software Sources, select the Main Server preferably and reload.

---

