---
title: "Create debain package for offline installation"
date: 2011-07-05
forum: General Help
---

### Post by Yoana148 on 2011-07-05
Here, what I would like:

I have to create debian package of our product. and product is depend on some other python packages (such as python-lxml). so basically I have to add python-lxml in debian/control file (in Depends section). but It could work if end user have internet connectivity or package should have to be present in "/var/cache/apt/archives" folder, for dependency installation.

But unfortunately, end user wants to install package without internet connectivity. So I have included all required debian packages in my_packg.deb.

now, my question is :
Is it possible to move required packages in "/var/cache/apt/archives" folder before execution of control file ? or Is there any way to run dpkg -i/sudo apt-get install commands from any debian files ?

   
Thanks!

---

### Post by Cheesehead on 2011-07-05
How does the offline system currently handle package management?
apt-zip? apt-offline? apt-on-cd? nothing?

---

### Post by Habitual on 2011-07-05
cp the my_packg.deb file to the target system and run 
```
sudo dpkg -i /path/to/my_packg.deb
```
on the target system.

the DEPS can be downloaded with apt-get -d once you know the requirements and installed in the same manner.

---

### Post by Yoana148 on 2011-07-06
> **Habitual said:**
> cp the my_packg.deb file to the target system and run 
```
sudo dpkg -i /path/to/my_packg.deb
```on the target system.

the DEPS can be downloaded with apt-get -d once you know the requirements and installed in the same manner.

but  I have a different problem. I can not manually copy-paste debian  package to end user's machine.:(
I  need some mechanism to do this.

So I thought, to add dependent  packages (.deb packages like python-lxml.deb etc) inside my own  project's debian package (my_package.deb folder). (not a good idea)

and  write some commands  in debian/rules file,  to move those dependent  packages in ""/var/cache/apt/archives" folder.

but when I tried  to run my_package.deb , it runs "debian/control" file first (and  dependent packages are still not moved in proper system folder) So it  gives an error of dependency modules (as not able to download from  internet )

> **Cheesehead said:**
> How does the offline system currently handle  package management?
apt-zip? apt-offline? apt-on-cd? nothing?

I have tried apt-offline but no luck, it seems to be  have different concept.

So I am searching for other way around.  Is it possible to run any other file/script before execution of control  file from debian package? or Is there any good solution ?

Thanks!

---

