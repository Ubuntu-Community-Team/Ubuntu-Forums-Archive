---
title: "How can i use APTonCD on windows"
date: 2009-11-07
forum: General Help
---

### Post by emigrant on 2009-11-07
hi all,
is there a way i can use APTonCD on windows.
bcz, since my home internet is very slow, if i want to install new apps i think APTonCD is a good tool. and all the high speed internet cafes around here are running in MS.

what is the solution for me? :mad:

thank you very much.

---

### Post by mac9416 on 2009-11-07
Hi, emigrant!

APTOnCD is a good tool, but not exactly what you are looking for. The best way to get software onto a slow-connection or offline machine is use [Keryx]("http://keryxproject.org"). It can run on any OS and is very simple to use. You'll want to read the tutorial here: [http://crashsystems.net/2009/01/keryx-tutorial/](http://crashsystems.net/2009/01/keryx-tutorial/)

Once you install APTOnCD on your home machine using debs downloaded with Keryx, you can use it to package any other debs you get onto a CD.

Let me know if you have any trouble!
-mac

---

### Post by emigrant on 2009-11-08
thank you very much mac9416,
this would be really helpful for me.
i will get back to you after trying out what it is in the tutorial.

---

### Post by emigrant on 2009-11-09
Hi mac,
Keryx did perfectly what i wanted to do.
By the way i have a question:
For the first project my download size was about 300 mb. And say in a week i download another 100 mb of updates.
And incase if i format the system and reinstal in the third week, do i have to make new projects again or can i use the same updates which i already have in my first and second projects?  Which will save me from downloading a 400 mb again.
Also is it possible to make use of this same projects in another machine?
I mean in my friends machine who too doesnt have a good internet connection?

Thank you very much for your help.

---

### Post by mac9416 on 2009-11-09
Good to hear Keryx worked well for you, emigrant!

> For the first project my download size was about 300 mb. And say in a week i download another 100 mb of updates.
And incase if i format the system and reinstal in the third week, do i have to make new projects again or can i use the same updates which i already have in my first and second projects? Which will save me from downloading a 400 mb again.As long as you reinstalled the same flavor of Ubuntu, the same updates should work fine. However, for keeping a system up-to-date, the 'sudo dpkg -i' will soon prove itself too primitive. You will instead want to use APT to keep anything from breaking.

_**To install .deb files from Keryx using APT...**_

**Copy the .deb files to the APT cache:**
```
$ gksu nautilus  # WARNING: Using nautilus in super-user mode is very dangerous - proceed with caution.
```
[LIST=1]
[*]Navigate to the Keryx directory on your flash drive
[*]From there, navigate to projects/<project_name>/packages/
[*]Select everything with <ctrl+a> and copy then with <ctrl+c>
[*]Navigate to /var/cache/apt/archives/
[*]Paste with <ctrl+v>
[/LIST]

**Copy the index files to the APT cache:**
If you have exited Nautilus, run the above command again to restart it.
[LIST=1]
[*]Navigate to the Keryx directory on your flash drive
[*]From there, navigate to projects/<project_name>/lists/
[*]Select everything with <ctrl+a> and copy then with <ctrl+c>
[*]Navigate to /var/lib/apt/lists
[*]Paste with <ctrl+c> - if prompted to overwrite, grit your teeth and hit "OK"
[/LIST]

**Installing packages with APT:**
Now you can use the usual 'apt-get install <package_name>' commands to install the software downloaded with Keryx. When you want to install new updates, just repeat the steps above.

> Also is it possible to make use of this same projects in another machine?
I mean in my friends machine who too doesnt have a good internet connection?

Maybe. If you are using the same flavor as they are, then yes, just use the method to install described above. If you are using Ubuntu and he is using Xubuntu, you will have to create a new project for his computer. Also, if you had packages installed on your computer (before creating the project) that he didn't, Keryx will skip those packages, and they will be missing when you try to install on your friend's computer. 
The trick is to try it and, if it works, hooray! If not, you'll want to create a new project.

I hope that isn't too confusing. I believe in the next release, Keryx will greatly simplify the installation process.

---

