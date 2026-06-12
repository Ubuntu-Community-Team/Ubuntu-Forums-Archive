---
title: "Issues with installing BURG. Terminal contents inside."
date: 2010-07-05
forum: General Help
---

### Post by MrOneEyedBoh on 2010-07-05
Im having an issue installing berg via the terminal. Here is the Terminal saved contents...

mroneeyedboh@Ubuntu-01:~$ sudo add-apt-repository ppa:bean123ch/burg
[sudo] password for mroneeyedboh: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv A267D98DF71B10F601CFAC1B55708F1EE06803C5
gpg: requesting key E06803C5 from hkp server keyserver.ubuntu.com
gpg: key E06803C5: "Launchpad burg" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
mroneeyedboh@Ubuntu-01:~$ sudo apt-get update && sudo apt-get install burg burg-themes
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                          
Get:1 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release.gpg [189B]                 
Ign [http://wine.budgetdedicated.com/apt/](http://wine.budgetdedicated.com/apt/) hardy/main Translation-en_US          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/bean123ch/bur/ubuntu/](http://ppa.launchpad.net/bean123ch/bur/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                    
Get:2 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release [1,016B]                   
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release                              
Get:3 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]                           
Ign [http://ppa.launchpad.net/bean123ch/burg/ubuntu/](http://ppa.launchpad.net/bean123ch/burg/ubuntu/) lucid/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Ign [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable/main Translation-en_US              
Get:4 [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release.gpg [197B]                   
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/free Translation-en_US                
Get:5 [http://dl.google.com](http://dl.google.com) stable Release [2,544B]                             
Get:6 [http://dl.google.com](http://dl.google.com) stable/main Packages [1,066B]                       
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                             
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US    
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US       
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/non-free Translation-en_US            
Get:7 [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release [6,854B]                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Packages                        
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg                     
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/free Packages                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages                       
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
  404  Not Found
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/non-free Packages                      
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/non-free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/non-free Packages
Fetched 11.0kB in 31s (349B/s)
W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: Failed to fetch [http://ppa.launchpad.net/bean123ch/bur/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/bean123ch/bur/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
mroneeyedboh@Ubuntu-01:~$ sudo burg-install "(hd0)"
sudo: burg-install: command not found
mroneeyedboh@Ubuntu-01:~$

---

### Post by MrOneEyedBoh on 2010-07-05
bumpp

---

### Post by MrOneEyedBoh on 2010-07-05
up again ](*,)

---

### Post by MrOneEyedBoh on 2010-07-06
Again?

---

### Post by pedro_orange on 2010-07-06
> **MrOneEyedBoh said:**
>                        
W: Failed to fetch [http://ppa.launchpad.net/bean123ch/bur/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/bean123ch/bur/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

There's a typo in your link. 

[http://ppa.launchpad.net/bean123ch/burg/ubuntu/dists/lucid/main/binary-i386/](http://ppa.launchpad.net/bean123ch/burg/ubuntu/dists/lucid/main/binary-i386/)
[http://ppa.launchpad.net/bean123ch/bur/ubuntu/dists/lucid/main/binary-i386/](http://ppa.launchpad.net/bean123ch/bur/ubuntu/dists/lucid/main/binary-i386/)

Top one works, bottom one doesn't. Hence the 404. 

Have a nice day

---

### Post by MrOneEyedBoh on 2010-07-06
Thanks pedro.

Seems that its something in the link here

[http://www.omgubuntu.co.uk/2010/01/make-grub-themes-beautiful-look-nicer.html](http://www.omgubuntu.co.uk/2010/01/make-grub-themes-beautiful-look-nicer.html)

When I type 

" sudo apt-get update && sudo apt-get install burg burg-themes " 

Thats when I get the error in the terminal content.  Is there any other ways to DL BURG?

---

### Post by stinkeye on 2010-07-06
Try installing using Burg-manager.
[**_http://ubuntuforums.org/showthread.php?t=1514922_**]("http://ubuntuforums.org/showthread.php?t=1514922")

---

### Post by MrOneEyedBoh on 2010-07-07
Thanks. I think thats going to get it to work.

no help. It says to install it enter the drive name.. But where do I get that drive name from? Im coming from windows, so I know C: is the harddrive and so on. But what do I put there for Ubuntu? Thanks!

---

### Post by stinkeye on 2010-07-07
It's usually /dev/sda.
You only need to put **sda** in the burg-manager.
Run the attached script.(Once downloaded you'll need to extract it to your home folder)  

To run the script in the terminal enter
```
sudo bash boot_info_script055.sh
```

You will now have a **RESULTS.txt** file in your home folder.
At the top of the file there will be a section telling you where grub is installed.
eg...

```
============================= Boot Info Summary: ==============================

[I] => Grub 2 is installed in the MBR of /dev/[COLOR="Purple"]sda[/COLOR] and looks on the same drive in 
    partition #1 for /boot/burg.[/I]
```
[COLOR="#800080"]Use this value[/COLOR]

---

### Post by MrOneEyedBoh on 2010-07-07
Thanks the SDA worked, but I get this when I try to run that code in the terminal


bash: boot_info_script055.sh: No such file or directory

---

### Post by stinkeye on 2010-07-07
Is the script in your home directory?
You have to extract the script from the tar.gz file to your home folder.
tar.gz is just a compressed file like zip.

---

### Post by MrOneEyedBoh on 2010-07-07
Will do now.

---

### Post by MrOneEyedBoh on 2010-07-07
Worked great. Thanks again..


Hmm.. It says installed but when I reboot it still comes up with the text style bootloader. Is that because I have to reapply the theme I want in the BURG GUI?

---

### Post by stinkeye on 2010-07-07
Ok,good.
Enjoy your burger! :o

Try running
```
sudo update-burg
```

or

in the burg-manager > edit burg parameters ...click on the apply changes button.(does the same as sudo update-burg)

At the burg boot screen you can press "t" to change the theme.

---

### Post by MrOneEyedBoh on 2010-07-07
I did hit T in the bootloader and nothing happened.. this is crazy lol. But at least Im learning something on the way...

---

### Post by MrOneEyedBoh on 2010-07-07
Now im getting this when I try and update


sudo: update-burg: command not found


I did check the RESULTS.txt you said to check and it did say installed.

---

### Post by stinkeye on 2010-07-07
Post your RESULTS.TXT  file.

This is confusing me because I didn't use the burg-manager to install.
I used this [**_[COLOR="DarkRed"]guide[/COLOR]_**]("http://www.omgubuntu.co.uk/2010/01/make-grub-themes-beautiful-look-nicer.html") which says to install use
```
sudo burg-install [COLOR="#800080"]"(hd0)"[/COLOR]
```

but the manager just gives as an example [COLOR="Purple"]sda[/COLOR]


Try in terminal
```
sudo burg-install "(hd0)"
```
then
```
sudo update-burg
```

---

### Post by MrOneEyedBoh on 2010-07-07
I tired what you said and


mroneeyedboh@Ubuntu-01:~$ sudo burg-install "(hd0)"
[sudo] password for mroneeyedboh: 
sudo: burg-install: command not found


and attached is the RESULTS

---

### Post by stinkeye on 2010-07-07
Oh well, as I can't verify that the burg-manager actually works I would just
use the guide I gave a link for to install, as at least I know this worked for me.
Just need to run 4 commands in the terminal.

---

### Post by MrOneEyedBoh on 2010-07-07
I did try that but I was getting an error. if you click on my name and then look for threads I started you'll see it under there.

---

### Post by stinkeye on 2010-07-07
Give it another try.
I just ran the first 2 commands n terminal with no errors.
Goto synaptic > settings > repositories > other software
and delete the **bean123ch/burg** repository and click reload.
Then try again.

---

### Post by MrOneEyedBoh on 2010-07-07
Doing so now. 

Where should I start at again?

---

### Post by stinkeye on 2010-07-07
Do as above and then just follow the the [**_[COLOR="DarkRed"]guide[/COLOR]_**]("http://www.omgubuntu.co.uk/2010/01/make-grub-themes-beautiful-look-nicer.html") here.

---

### Post by MrOneEyedBoh on 2010-07-07
haha good as gold. I got alot more interaction this time aroudn following that link. I did it before but got no where. Maybe is was because I had several bean's in my repository? None the less thanks!

---

### Post by stinkeye on 2010-07-07
[SIZE="6"]Hooray[/SIZE] , I can go for a surf now!
I thought it may be a repo issue. Good luck.
:lolflag::guitar::popcorn:):P

---

### Post by MrOneEyedBoh on 2010-07-07
WAIT haha

( have fun surfing. )

Lastly, how come I have several entries for Ubuntu and Windows7? Like different ubuntu versions and memtest etc?

---

### Post by stinkeye on 2010-07-07
Lucky I had one last look.
F7 or f I think hides the other entries.
In the burg-manager you can test using the burg-emu button.
):P):P):P):P):P):P

---

### Post by MrOneEyedBoh on 2010-07-07
I appreciate it. Thanks again!!
):P):P):P):P):P:guitar:

---

