---
title: "Cannot Update Software Catalog"
date: 2010-06-28
forum: General Help
---

### Post by ThatOneGuy2012 on 2010-06-28
I am trying to get lightning or sunbird on Lucid, but apparently i need to update the software catalog... doesn't seem like it should be a problem from what I've seen on the net, but when i go into the screen where the "update now" options should be available, it isn't there. is there a command line way or something to do this update, or am i going to have to compile it on my own?

---

### Post by Woody1987 on 2010-06-28
Try running "sudo apt-get update" in a terminal

---

### Post by ThatOneGuy2012 on 2010-06-28
I ran it without any results. can i install lightning from terminal?

---

### Post by bogdanjcnd on 2010-06-28
Yup,
sudo apt-get update  works in terminal 
  if  you  have results like this

  Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_CA
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                   
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid Release.gpg                   
Get:1 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_CA [10.3kB]
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_CA
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_CA
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_CA
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                          
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                    
Get:2 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_CA [425B]
Get:3 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_CA [663B]
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates Release.gpg           
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_CA
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_CA
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_CA
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid Release 
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/multiverse Sources
Fetched 11.4kB in 1s (6,514B/s)
Reading package lists... Done
  it means   you updated  repository database. Another way is to try synaptic. Works fine for me

---

### Post by ThatOneGuy2012 on 2010-06-29
thats what i got, but i still cannot install lightning.

---

### Post by plucky on 2010-06-29
> **ThatOneGuy2012 said:**
> thats what i got, but i still cannot install lightning.

Do you have the **universe** repository enabled?

**System > Administration > Software Sources** and make sure the universe repository is enabled and then run the command in a terminal ```
sudo apt-get update
sudo apt-get install lightning
```

If that doesn't work,post the output from the terminal window.

Good Luck

---

### Post by ThatOneGuy2012 on 2010-06-29
i was able to install the program, but i still cannot update the catalog. i dont know how the software sources got changed, or how i missed something that simple, but thanks for pointing that out. ill post the output for sudo apt-get update in a few minutes

---

### Post by ThatOneGuy2012 on 2010-06-29
```

Hit http://security.ubuntu.com lucid-security Release.gpg
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid-updates Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://security.ubuntu.com lucid-security Release
Hit http://us.archive.ubuntu.com lucid Release 
Hit http://security.ubuntu.com lucid-security/main Packages          
Hit http://us.archive.ubuntu.com lucid-updates Release
Hit http://security.ubuntu.com lucid-security/restricted Packages    
Hit http://security.ubuntu.com lucid-security/main Sources
Hit http://security.ubuntu.com lucid-security/restricted Sources
Hit http://security.ubuntu.com lucid-security/universe Packages
Hit http://security.ubuntu.com lucid-security/universe Sources
Hit http://us.archive.ubuntu.com lucid/main Packages
Hit http://us.archive.ubuntu.com lucid/restricted Packages
Hit http://us.archive.ubuntu.com lucid/main Sources
Hit http://us.archive.ubuntu.com lucid/restricted Sources
Hit http://us.archive.ubuntu.com lucid/universe Packages
Hit http://us.archive.ubuntu.com lucid/universe Sources
Hit http://security.ubuntu.com lucid-security/multiverse Packages
Hit http://security.ubuntu.com lucid-security/multiverse Sources
Hit http://us.archive.ubuntu.com lucid/multiverse Packages
Hit http://us.archive.ubuntu.com lucid/multiverse Sources
Hit http://us.archive.ubuntu.com lucid-updates/main Packages
Hit http://us.archive.ubuntu.com lucid-updates/restricted Packages
Hit http://us.archive.ubuntu.com lucid-updates/main Sources
Hit http://us.archive.ubuntu.com lucid-updates/restricted Sources
Hit http://us.archive.ubuntu.com lucid-updates/universe Packages
Hit http://us.archive.ubuntu.com lucid-updates/universe Sources
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Sources
Reading package lists... Done

```

---

### Post by supergrav on 2010-06-29
I hope i'm not wrong or miss anything but your update seems ok, if this is the only thing you get from apt-get update.

---

### Post by ThatOneGuy2012 on 2010-06-29
the problem i am having is not with the main update, but with the so called "software catalog" in the software center. here is a screenshot to give you an idea. there should be an update now button somewhere on this window.

---

### Post by supergrav on 2010-06-29
> **ThatOneGuy2012 said:**
> the problem i am having is not with the main update, but with the so called "software catalog" in the software center. here is a screenshot to give you an idea. there should be an update now button somewhere on this window.

Correct me if I'm wrong, but I don't think there should be an option of update there...

---

### Post by ThatOneGuy2012 on 2010-06-29
if there isn't, then i missed something. is there a way to update this thing then?

---

### Post by plucky on 2010-06-29
> **ThatOneGuy2012 said:**
> the problem i am having is not with the main update, but with the so called "software catalog" in the software center. here is a screenshot to give you an idea. there should be an update now button somewhere on this window.

That's not your problem.I think it is up to the developer of that software to update the Software Catalog with new updates.You could go to the Mozilla site and see whether there are any updates for that application.Not all the software in the repositories are maintained by Canonical.


Good Luck

---

### Post by ThatOneGuy2012 on 2010-06-29
well thanks for the help then...

---

### Post by spurlo51 on 2010-07-02
I am having the same issue as [ThatOneGuy2012]("http://ubuntu-virginia.ubuntuforums.org/member.php?u=1091298") - I am attempting to install Sun/Java plug-in and it says I need to update my software catalog.... So is it Sun that needs to complete the update or me?

I am confused, normally everything just updates..

Am I missing something? Has this already been answered, is there somewhere else I can go to get Java?

THANKS!!

---

### Post by charly17201 on 2010-07-23
Yes, I too was having the same problems at ThatOneGuy2012 with the software catalog 'needing update'.  I followed the above guidance by doing the following:

sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install lightning

which worked - to an extent

went to Thunderbird, clicked the tools/add ons/install to install Lightning (which it did show there) and got a version incompatibility.

Checking Mozillas site, the version of Thunderbird I'm running is 3.0.5 but the version that Lightning is apparently written for is 3.1.1

Now my problem is getting the 3.1.1 version of Thunderbird on the computer.

If it makes any difference, I'm running 10.04 NBR - I don't think it should and I'm finding a lot of software packages in the "Software Center' needing the catalog to be updated (after enabling the Multi/Universe in Synaptic and multiple sudo apt-get update/dist-upgrade(s). I think this is most likely an Ubuntu bug as opposed to a Mozilla problem.

---

