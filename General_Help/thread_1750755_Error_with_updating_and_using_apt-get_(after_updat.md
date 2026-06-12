---
title: "Error with updating and using apt-get (after update to 11.04)"
date: 2011-05-05
forum: General Help
---

### Post by grimslider75 on 2011-05-05
this message comes up during either removing, installing or updating:
```
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

```

Any suggestion?

BTW, I have checked other posts, but I cannot understand what they say. I dislike fixing things, but I like understanding them, so if an issue can be simplified, that would be great for me =)
AND
I recently updated from 11.04 by updating through ubuntu 10.04. This problem was non-existent before the upgrade. 

thanks in advance =)

---

### Post by drs305 on 2011-05-05
Try this:

Open Synaptic. Settings > Repositories > Ubuntu Software tab. Untick the (main) box, wait a second or two, then reselect it. Click the Reload button. 

This should force Ubuntu to redownload the main repository package list and may correct the error.

---

### Post by grimslider75 on 2011-05-06
> **drs305 said:**
> Try this:

Open Synaptic. Settings > Repositories > Ubuntu Software tab. Untick the (main) box, wait a second or two, then reselect it. Click the Reload button. 

This should force Ubuntu to redownload the main repository package list and may correct the error.
I cannot even access the synaptic Package manager, it fails upon opening with this message,
> E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.


---

### Post by grimslider75 on 2011-05-06
and I also receive this message after attempting to open the update manager:

> Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

---

### Post by drs305 on 2011-05-06
We can move the 'offending' file, which should allow APT to reload a correct Package list:

```
sudo mv /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_bina ry-i386_Packages ~/Desktop/Packages.bad
sudo apt-get update
```

If it runs without error, you will have a 'root-owned' file on your Desktop, Packages.bad, which you should delete. Open Nautilus as root and use SHIFT-DEL to remove the file:
```
gksu nautilus ~/Desktop
```

---

### Post by azend on 2011-05-06
Don't forget to change to your specific Ubuntu mirror.
> **drs305 said:**
> ```
sudo mv /var/lib/apt/lists/_**us**_.archive.ubuntu.com_ubuntu_dists_natty_main_bina ry-i386_Packages ~/Desktop/Packages.bad
sudo apt-get update
```
In my case it was:
```
sudo mv /var/lib/apt/lists/_**ca**_.archive.ubuntu.com_ubuntu_dists_natty_main_bina ry-i386_Packages ~/Desktop/Packages.bad
sudo apt-get update
```

---

### Post by azend on 2011-05-06
Alright, after further research, and my above post's instructions not working, I have found a solution that does.

The solution I came upon is to just remove all of your package listings and rebuild them. NOTE: this does not mean removing your package repositories, just the listings of the packages inside of them. Removing the package listings will force apt-get to rebuild everything so it is normal for it to take a bit longer.

```

# First delete all of the previously available listings
sudo rm /var/lib/apt/lists/* -vf

# And then use apt-get to rebuild your package listings
sudo apt-get update

```

Hope everything runs smoothly!
Also, if you need any more information, I found the fix at this launchpad post: 
[https://answers.launchpad.net/ubuntu/+source/update-manager/+question/155062]("https://answers.launchpad.net/ubuntu/+source/update-manager/+question/155062")

---

### Post by grimslider75 on 2011-05-06
> **azend said:**
> Alright, after further research, and my above post's instructions not working, I have found a solution that does.

The solution I came upon is to just remove all of your package listings and rebuild them. NOTE: this does not mean removing your package repositories, just the listings of the packages inside of them. Removing the package listings will force apt-get to rebuild everything so it is normal for it to take a bit longer.

```

# First delete all of the previously available listings
sudo rm /var/lib/apt/lists/* -vf

# And then use apt-get to rebuild your package listings
sudo apt-get update

```

Hope everything runs smoothly!
Also, if you need any more information, I found the fix at this launchpad post: 
[https://answers.launchpad.net/ubuntu/+source/update-manager/+question/155062]("https://answers.launchpad.net/ubuntu/+source/update-manager/+question/155062")
that worked just fine, thanks for the help everyone! This makes me more appreciative of the internet =)

---

### Post by GoldNugget on 2011-05-07
Thanks. That worked for me too.

---

### Post by Samanathon on 2011-05-15
> **azend said:**
> Alright, after further research, and my above post's instructions not working, I have found a solution that does.

The solution I came upon is to just remove all of your package listings and rebuild them. NOTE: this does not mean removing your package repositories, just the listings of the packages inside of them. Removing the package listings will force apt-get to rebuild everything so it is normal for it to take a bit longer.

```

# First delete all of the previously available listings
sudo rm /var/lib/apt/lists/* -vf

# And then use apt-get to rebuild your package listings
sudo apt-get update

```

Hope everything runs smoothly!
Also, if you need any more information, I found the fix at this launchpad post: 
[https://answers.launchpad.net/ubuntu/+source/update-manager/+question/155062]("https://answers.launchpad.net/ubuntu/+source/update-manager/+question/155062")
Dude, you're awesome! That worked great!!

---

### Post by 942kid on 2011-05-15
I haven't seen the update windows for a long time. Thank you all for the awesome post that solves my problem!

---

### Post by Jordanbadangayon on 2011-06-04
> **azend said:**
> Alright, after further research, and my above post's instructions not working, I have found a solution that does.

The solution I came upon is to just remove all of your package listings and rebuild them. NOTE: this does not mean removing your package repositories, just the listings of the packages inside of them. Removing the package listings will force apt-get to rebuild everything so it is normal for it to take a bit longer.

```

# First delete all of the previously available listings
sudo rm /var/lib/apt/lists/* -vf

# And then use apt-get to rebuild your package listings
sudo apt-get update

```

Hope everything runs smoothly!
Also, if you need any more information, I found the fix at this launchpad post: 
[https://answers.launchpad.net/ubuntu/+source/update-manager/+question/155062]("https://answers.launchpad.net/ubuntu/+source/update-manager/+question/155062")
You're awesome mate.. Thank you so much.. For a moment, I was almost ready to do a reinstallation. :)

---

### Post by rainbow82 on 2011-07-02
Thanks a lot!!, that worked for me..

---

### Post by augusto on 2011-07-06
> **azend said:**
> Alright, after further research, and my above post's instructions not working, I have found a solution that does.

The solution I came upon is to just remove all of your package listings and rebuild them. NOTE: this does not mean removing your package repositories, just the listings of the packages inside of them. Removing the package listings will force apt-get to rebuild everything so it is normal for it to take a bit longer.

```

# First delete all of the previously available listings
sudo rm /var/lib/apt/lists/* -vf

# And then use apt-get to rebuild your package listings
sudo apt-get update

```

Hope everything runs smoothly!
Also, if you need any more information, I found the fix at this launchpad post: 
[https://answers.launchpad.net/ubuntu/+source/update-manager/+question/155062]("https://answers.launchpad.net/ubuntu/+source/update-manager/+question/155062")

Thanks, worked great for me too!

---

### Post by utnubu resu on 2011-08-02
Just installed 11.04 on my Mother-in-law's computer and this issue came up. Thanks for your help, this solved the problem.

Jim

---

### Post by Pres_ on 2011-09-21
Works! I am running Ubuntu on a VM and this was simple / worked! Thanks for sharing ^_^

---

### Post by dhavalthakor on 2011-11-01
after executing this script i m getting this..plz help me frndz

mv: cannot stat `/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_natty_main_bina': No such file or directory
mv: cannot stat `ry-i386_Pachages': No such file or directory
:confused::confused::confused:

---

### Post by drs305 on 2011-11-01
> **dhavalthakor said:**
> after executing this script i m getting this..plz help me frndz

mv: cannot stat `/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_natty_main_bina': No such file or directory
mv: cannot stat `ry-i386_Pachages': No such file or directory
:confused::confused::confused:
dhavalthakor,

Welcome to the Ubuntu Forums.

It looks like you split the name 'in.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Pachages' into two parts.

Perhaps you should look at the folder and accomplish what you want to do with Nautilus (as root):
```
gksu nautilus /var/lib/apt/lists/
```

---

### Post by incognita on 2011-11-11
> **azend said:**
> Alright, after further research, and my above post's instructions not working, I have found a solution that does.

The solution I came upon is to just remove all of your package listings and rebuild them. NOTE: this does not mean removing your package repositories, just the listings of the packages inside of them. Removing the package listings will force apt-get to rebuild everything so it is normal for it to take a bit longer.

```

# First delete all of the previously available listings
sudo rm /var/lib/apt/lists/* -vf

# And then use apt-get to rebuild your package listings
sudo apt-get update

```

Hope everything runs smoothly!
Also, if you need any more information, I found the fix at this launchpad post: 
[https://answers.launchpad.net/ubuntu/+source/update-manager/+question/155062]("https://answers.launchpad.net/ubuntu/+source/update-manager/+question/155062")

Lovely solution, mate! Thanks!

---

### Post by infineet on 2011-12-10
hi im newbie just started jump in ubuntu 
this just solve the problem
thanks guys

---

### Post by wisstnb on 2012-04-23
> **azend said:**
> alright, after further research, and my above post's instructions not working, i have found a solution that does.

The solution i came upon is to just remove all of your package listings and rebuild them. Note: This does not mean removing your package repositories, just the listings of the packages inside of them. Removing the package listings will force apt-get to rebuild everything so it is normal for it to take a bit longer.

```

# first delete all of the previously available listings
sudo rm /var/lib/apt/lists/* -vf

# and then use apt-get to rebuild your package listings
sudo apt-get update

```

hope everything runs smoothly!
Also, if you need any more information, i found the fix at this launchpad post: 
[https://answers.launchpad.net/ubuntu/+source/update-manager/+question/155062]("https://answers.launchpad.net/ubuntu/+source/update-manager/+question/155062")



thanks that worked like a charm!):p

---

### Post by heckur on 2012-07-23
Solution posted by azend worked for me on a recently upgraded 11.10 to 12.04 which suddenly (no idea how) started getting this error.

---

### Post by lemel on 2012-10-11
> # First delete all of the previously available listings
sudo rm /var/lib/apt/lists/* -vf

# And then use apt-get to rebuild your package listings
sudo apt-get update

Dude you rock! Thanks

---

