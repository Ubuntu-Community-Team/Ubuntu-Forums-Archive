---
title: "Cant install updates"
date: 2012-07-01
forum: General Help
---

### Post by typos1 on 2012-07-01
I cant install updates for some reason.

I have an mplayer update but it wont install it because it says

"Requires installation of untrusted packages

The action would require the installation of packages from unauthenticated sources.

details - mplayer"

I ve tried to enable 3rd part sources but I cant find how to, plus theres a load of 3rd party software on my system already so it seems strange that there is a problem with mplayer.

also get this in a terminal:

W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner amd64 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-amd64_Packages)
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

but I cant see any duplicates.

---

### Post by jmfal on 2012-07-01
Try this and see if there are duplicates there

```
   
/etc/apt/sources.list.d
```

---

### Post by DJ_Max on 2012-07-01
Post your sources.list

---

### Post by raja.genupula on 2012-07-01
+1 to above .

do as 

```
sudo gedit /etc/apt/sources.list

``` In your terminal . Then look for the same entries  and remove them . 

If you felt confused paste them here , we do the job and post back to you .

---

### Post by typos1 on 2012-07-01
I ve already looked in software sources and couldnt see any duplicates.

terminal list:

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb [http://download.bitdefender.com/repos/deb/](http://download.bitdefender.com/repos/deb/) bitdefender non-free
deb-src [http://download.bitdefender.com/repos/deb/](http://download.bitdefender.com/repos/deb/) bitdefender non-free


Do I have multiverse enabled twice ?

---

### Post by DJ_Max on 2012-07-01
What do you have in your /etc/apt/sources.list.d/ folder?

If you don't know what you are doing, use Update Manager, then click on settings to manage the repositories

---

### Post by typos1 on 2012-07-01
I cant use update manager because it wont install the updates cos of the sources problem. 

I ve looked in software sources and  cant see any duplicates, I think it does show them in the terminal, though, see my above post.

---

### Post by DJ_Max on 2012-07-01
Comment out everything in the Sources.list. Or boot the LiveCD and copy the default sources.list. Then delete everything in /etc/apt/sources.list.d/

run
```
sudo apt-get update
```
Then,
Open the Ubuntu Software Center
Open Edit -> Software Sources...
Enable repo's

---

### Post by typos1 on 2012-07-01
sudo apt get-update doesnt work - it returns the duplicate sources error that I first posted about.

How do you mean "comment out" ? Delete all my sources ?

---

### Post by DJ_Max on 2012-07-01
> **typos1 said:**
> sudo apt get-update doesnt work - it returns the duplicate sources error that I first posted about.

How do you mean "comment out" ? Delete all my sources ?

Of course it's not going to work, you have to comment out all the lines.

Use this instead.
> # deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
#deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates main restricted
#deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
#deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise universe
#deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise universe
#deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates universe
#deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
#deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise multiverse
#deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise multiverse
#deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates multiverse
#deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
#deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
#deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
#deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
#deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
#deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
#deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
#deb [http://download.bitdefender.com/repos/deb/](http://download.bitdefender.com/repos/deb/) bitdefender non-free
#deb-src [http://download.bitdefender.com/repos/deb/](http://download.bitdefender.com/repos/deb/) bitdefender non-free

---

### Post by princemackenzie on 2012-07-01
> **typos1 said:**
> sudo apt get-update doesnt work - it returns the duplicate sources error that I first posted about.

How do you mean "comment out" ? Delete all my sources ?

To 'comment out' a source, place ## in front of the line with the URL in the list.  That will remove it from the list of sources that apt uses.

---

### Post by DJ_Max on 2012-07-01
If you don't know what you are doing, I wouldn't touch that file anymore. Use Ubuntu Software Center to manage the repo's

Make sure you delete everything in /etc/apt/sources.list.d/
```
sudo rm -rf /etc/apt/sources.list.d/*
```

---

### Post by typos1 on 2012-07-01
I ve only ever edited software sources using the GUI so, in that respect I "dont know what I m doing", although from what prioncemakenzie said its not hard, I d just not heard the term "comment out" before.

As I said earlier in software centre it does not show any duplicates. 

From what I can see in the terminal it DOES list duplicates - is that right ?

Why do I need to delete ALL my software sources ?

---

### Post by typos1 on 2012-07-02
I ve uncommented the lines as you said, but it has made no difference whatsoever -  still cannot update - still get this error message :

"Requires installation of untrusted packages

The action would require the installation of packages from unauthenticated sources.

Details:

mplayer"

I installed synaptic and after installing I got a similar duplicate sources message and it listed an amd64 pakage and an i386 package, so I assume the problem is that I ve got the intel processor package as well as the amd64 one, when clearly I should have just. the amd64 one, but these sources are not listed in the output if I get software sources listed in a terminal

I ve tried enabling 3rd party sources, but I cant find where it is in software sources now, dont think I ve done it since software sources has been incorporated into softwarecentre, havent needed to do it for ages as I just upgraded to a newer version every 6 months, this is a new install.

---

### Post by typos1 on 2012-07-02
And now I m STILL getting the same duplicate sources error even though I uncommented the sources as I was told

---

### Post by jmfal on 2012-07-02
Hi  typos1

open the update manager and click on the authentication tab and check for double entries there.

Click on the other sofrware tab and untic the two  entries for independent wait a couple of seconds and put a ckeck back in.
Then run
```
  sudo apt-get update
               sudo apt-get upgrade
```
If you get an error post it.

---

### Post by typos1 on 2012-07-02
Did all that. 

Couldnt see any duplicates at all, still getting the errors, but this time, rather than just list the supposed duplicate sources, it said mplayer update was from an untrusted source and asked did I want to install it. 

I clicked yes and it installed the update, so thats partially sorted the problem. 

But I ve still got duplicate sources and it tells me to run apt-update and apt-upgrade to sort it, so I do and then it tells me that I ve got duplicate sources and to run apt-update and apt-upgrade, so I do and . . . . well you get the picture.

---

### Post by jmfal on 2012-07-02
Yeah I see where that's going.

Try this

```
    ls /etc/apt/sources.list.d    
```

and check for double entries.

---

### Post by matt_symes on 2012-07-02
Hi

> /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner  _binary-amd64_Packages
/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner  _binary-i386_PackagesThis is your problem. You have amd64 and i386 lists cached.

Open a terminal and type (you may find it easier to copy and paste this into the terminal)

```
sudo rm /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-amd64_Packages
```and then 

```
sudo rm /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages
```Enter your password, It will not be echoed to the screen.

Then type 

```
sudo apt-get update
```EDIT:
> 
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/main/binary-**i386**/

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/restricted/binary-**i386**/
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ precise main restrictedThis is the only reference i can see to both i386 and amd64 in your sources. Did you recently disable a cdrom deb source perhaps ?

Are you usin 32 or 64 bit Ubuntu ?

Please post the output of (from the terminal)

```
uname -a
```Kind regards

---

### Post by typos1 on 2012-07-04
> **jmfal said:**
> Yeah I see where that's going.

Try this

```
    ls /etc/apt/sources.list.d    
```and check for double entries.

 Yes I have done that before and unquoted the duplicates but it didnt seem to change anything. 

matt_symes, I thought that having amd64 AND i386 was the problem, as I said in an earlier post. 

But neither are listed in software sources so I didnt know how to remove them.

The sudo remove command is a bit too advanced for me !  

I ve done what you said and now I get this :

```

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) precise InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783 
W: Failed to fetch [http://ppa.launchpad.net/geod/ppa-geod/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/geod/ppa-geod/ubuntu/dists/precise/main/source/Sources)  404  Not Found  
W: Failed to fetch [http://ppa.launchpad.net/geod/ppa-geod/ubuntu/dists/precise/main/binary-amd64/Packages](http://ppa.launchpad.net/geod/ppa-geod/ubuntu/dists/precise/main/binary-amd64/Packages)  404  Not Found  
W: Failed to fetch [http://ppa.launchpad.net/geod/ppa-geod/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/geod/ppa-geod/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found 
W: Failed to fetch [http://ppa.launchpad.net/shnatsel/gimp-paint-studio/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/shnatsel/gimp-paint-studio/ubuntu/dists/precise/main/source/Sources)  404  Not Found  
W: Failed to fetch [http://ppa.launchpad.net/shnatsel/gimp-paint-studio/ubuntu/dists/precise/main/binary-amd64/Packages](http://ppa.launchpad.net/shnatsel/gimp-paint-studio/ubuntu/dists/precise/main/binary-amd64/Packages)  404  Not Found  
W: Failed to fetch [http://ppa.launchpad.net/shnatsel/gimp-paint-studio/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/shnatsel/gimp-paint-studio/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found  
E: Some index files failed to download. 
They have been ignored, or old ones used instead. 
```Output of u name is:  

```

3.2.0-26-generic #41-Ubuntu SMP Thu Jun 14 17:49:24 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux  

```I m using 64bit, recently got a newer pc, this is a fresh install, so have reccently installed lots of software, mostly in a terminal, but I have not enabled i386 sources.

I wouldnt because I know my pc is amd64, although I did notice in a terminal that i386 where enabled whilst something was installing

---

### Post by matt_symes on 2012-07-04
Hi

Excellent. Now you're getting somewhere.

Give me a couple of minutes to look at the sources and i will post back by editing this post.

EDIT 1:

Firstly you are missing a GPG key.

Open a terminal and type

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2EBC26B60C5A2783
```Enter your password. It will not be echoed to the screen.

EDIT 2:

You are referencing some ppa for precise that do not exist. From the terminal type

```
sudo rm /etc/apt/sources.list.d/*geod*
```and then

```
sudo rm /etc/apt/sources.list.d/*gimp*
```Finally type

```
sudo apt-get update
```If any of the rm commands return "No such file or directory" then post the output of

```
ls /etc/apt/sources.list.d
```BTW: In future please use code tags. They make posts much easier to read.

Wrap output from commands like this

[noparse]```
output from command
```[/noparse]

to get output like this

```
output from command
```Kind regards

---

### Post by typos1 on 2012-07-06
Sorry, didnt realise you were going to edit it, I was waiting for an email saying I had a reply to the post, hence delay, doh !

I ve coded this:

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2EBC26B60C5A2783

```And I get this:

```
:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2EBC26B60C5A2783
[sudo] password for user: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.eyuMa0p8Gc --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 2EBC26B60C5A2783
gpg: requesting key 0C5A2783 from hkp server keyserver.ubuntu.com
gpg: key 0C5A2783: public key "Medibuntu Packaging Team <admin@lists.medibuntu.org>" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1
```After running sudo upgrade I still get this:

```
Reading package lists... Done
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ precise/partner amd64 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-amd64_Packages)
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems 
```(I also did the sudo remove commands you told me to run to remove the sources you says dont exist.)

Output of

```

ls /etc/apt/sources.list.d
```is:

```
alexeftimie-ppa-precise.list
alexeftimie-ppa-precise.list.save
cardapio-team-cardapio-ppa-precise.list
cardapio-team-cardapio-ppa-precise.list.save
cardapio-team-unstable-precise.list
cardapio-team-unstable-precise.list.save
medibuntu.list
medibuntu.list.save
nae-team-ppa-precise.list
nae-team-ppa-precise.list.save
openshot_developers-ppa-precise.list
openshot_developers-ppa-precise.list.save
playonlinux.list
playonlinux.list.save
precise-partner.list
precise-partner.list.save
tiheum-equinox-precise.list
tiheum-equinox-precise.list.save
tsbarnes-indicator-keylock-daily-precise.list
tsbarnes-indicator-keylock-daily-precise.list.save
ubuntu-x-swat-x-updates-precise.list
ubuntu-x-swat-x-updates-precise.list.save
venerix-blug-precise.list
venerix-blug-precise.list.save
```


Its still saying I have i386 and amd64, I dont know why, I ve done what I was told to earlier in this thread to remove them.

---

### Post by matt_symes on 2012-07-06
Hi

We are getting there :) (i think)

Let's remove the list files again.

Copy and paste this into a terminal.

```
sudo rm /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-{i386,amd64}_Packages
```then this..

```
sudo rm /etc/apt/sources.list.d/*precise-partner*
```and finally this

```
sudo apt-get update
```Kind regards

---

### Post by typos1 on 2012-07-06
Woo hoo !

Its worked, did sudo update and no duplicate sources ! 

Did a sudo upgrade as well. 

All fine now.

Thanks very much for you help !!

---

