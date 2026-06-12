---
title: "Install new version of software that is in repositories"
date: 2012-06-11
forum: General Help
---

### Post by thgis on 2012-06-11
Hello.

I'm often compiling and installing software either to get the latest version or simply because the software doesn't exist in a repository.
To keep track on installed software I use checkinstall to generate .deb package files and install using package management tools ( e.g. dpkg -i <generatedDebFile>)
My question:
I believe that some trouble I have had in the past were caused by having installed software in a newer version that the one in repositories. This might be because my approach of installing home build versions is wrong.
So what is the proper way of installing software that is also in repositories?

Thanks in advance for any input:)
(Currently using Ubuntu 12.04 64 bit)

---

### Post by dino99 on 2012-06-11
i dont thing you are doing something wrong, i'm doing the same way too.
but sometimes the archives have libs with older release, and conflict often comes from there.

---

### Post by Zill on 2012-06-11
thgis:  I have been using Linux systems for many years now and have hardly ever had the urge to compile a program!  I have never actually *needed* the latest and greatest version of a program - slightly older (and more stable) versions usually do the job for me. :-)

Linux distributions consist of a set of disparate applications that have all been configured and tweaked to work together.  In particular, common libraries are used that all have to work with particular program versions.

When a distro, such as Ubuntu, is released, this is a snapshot of these applications at a particular point in time.  This means that all the applications involved *should* then work together.

By introducing applications that you have built from source, or from anywhere other than the correct repositories for that release, there is a strong possibility of breakage due to dependency problems.

So, if you want to avoid "trouble" and just keep your system working, I suggest you stick to only installing applications from the specific repositories for your particular release.

---

### Post by Cheesehead on 2012-06-11
Make sure the Backports repo is enabled on your system if you want the latest.

The Ubuntu Backporters team uploads to that repo, and they could sure use your help! Build once and everybody benefits. [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

---

