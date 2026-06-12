---
title: "Using &quot;i4l&quot; to create application installers for Linux"
date: 2010-10-26
forum: General Help
---

### Post by gnumaru on 2010-10-26
Installing applications on GNU/Linux has been a longstanding struggle.
Prior to 1993, to have a functional system, it was necessary to build everything, from the kernel, passing by the GNU tools, until the desired applications.
Today it is past, and installing software on GNU/Linux has become something even trivial. Having an internet connection, just a simple command like "apt-get install <program>" or "yum install <program>" suffices to install the desired application. If it is not in the standard distro repositories, it can probably be found in some other repository. If this is not possible, there is always the option to build it from the sources, that although refers to a past where this was the only option, now it becomes necessary only in extreme cases.

However, there is still a way to go.

Windows users are well accustomed to the paradigm NNF (next, next, finish) when it comes to managing applications. Also, are used to download at your own the application installer, which consists of a single executable file that contains everything needed to run the application.

In the GNU/Linux world, things are different.
   The user do not need to open the browser and get into any website to download the installer.
   The "installer" is divided into parts, ie a main package and its dependencies.
   The command to install the program is the same that download's it.

These differences, among others, as the fact of the application files become scattered across the system apart, confuses users coming from Windows or Mac. This difference in paradigm is not a crucial factor in determining whether or not the use of GNU/Linux, but should not be disregarded.

Moreover, we have a classic problem installing applications on offline machines, which I discussed in the folowing site:

[http://www.vivaolinux.com.br/dica/Instalacao-de-programas-em-maquinas-offline](http://www.vivaolinux.com.br/dica/Instalacao-de-programas-em-maquinas-offline)

In order to create an installation system for applications where all packets were available in a single file, and where they could install them on any offline machine, even if it had never updated its list of packages from the repository, I created a project in sourceforge called i4l (installers for linux)

[https://sourceforge.net/projects/i4l/](https://sourceforge.net/projects/i4l/)

i4l is not a new form of package manager. He is a kind of "wrapper" around apt. A package created with i4l contains all the debs needed to install a particular application in any apt based system, even on offline machines, where the list of the repositorie's packages has never been downloaded.

The code is written entirely in shell script and the user interface is made with zenity, or xmessage if zenity is not available. For now, it is compatible with the i386 versions of the following systems: Ubuntu 10.10, 10.04, 9.10, 9.04, 8.04 and Debian lenny.

You can create installers for any application available at your distro's repositories. You can also create installers to a target system different from the distro you are using to create the installer.

Now, I will give instructions on how to use the i4l to create installers.

First, download the latest version of the system preparer (i4l-system-preparer.sh), available on sourceforge

[http://sourceforge.net/projects/i4l/](http://sourceforge.net/projects/i4l/)

Then, run the file and follow the onscreen instructions.
At the end of the process, your system will be ready to create installers.

If you're kind of careful, and do not run any file you download from untrusted sites, open the file in gedit or any other text editor. This file is a bzip2 compressed archive whit a shell-script header, in charge of extracting and executing the file contents. This self-extracting compressed file, as well as installers i4l, are all generated using makeself available on the following page:

[http://megastep.org/makeself/](http://megastep.org/makeself/)

If you only want to extract the contents of the package to see what's inside, run it in terminal with the parameters "--keep --noexec". This will create a folder in the current directory with the entire contents of the package. This also goes for the installers generated with i4l.

After running the system preparer, if you want, run i4l-set-target-system.sh to choose the target system you want to create installers to.

To create an installer, simply run the command

# I4l-installer-creator.sh <app-name>

to generate an installer, which will be placed in your home directory.
Note that <app-name> is the name of any package available in the repositories of your distro.
Examples:

# I4l-installer-creator.sh gimp
# I4l-installer-creator.sh chromium-browser
# I4l-installer-creator.sh broffice.org
# I4l-installer-creator.sh ubuntu-restricted-extras

Conclusion

When creating i4l, My goal was to develop an easy way to install software on offline machines. Furthermore, it proves to be useful for backing up applications for those who have slow connection and do not want to download a program more than once.
It is also possible to use aptoncd for backing up your system cache, but when it comes to backing up a single application, rather than a collection of them, using the i4l shows to be simpler. In fact, initially i4l was inspired by aptoncd. I thank very much to those who created aptoncd, and the creators of makeself, which use to create self-extracting packages.

The i4l is still in early stages but is already able to do what he proposes: Create application installers for GNU/Linux systems.

I Would be extremely grateful to receive suggestions and criticisms of those who use it.
I intend in future to increase i4l's scope to cover rpm based systems.

In the same project on sourceforge, I hosted several application installers for Ubuntu 10.10 and 10.04. Whoever tests them, please, give me your feedback.

Send suggestions and comments to.

gnumaru <at> users <dot> sourceforge <dot> net

Exchanging <dot> with "." and <at>  "@". Standard anti-spam procedure.

I'll be happy if I can guide the development of i4l based on suggestions from users.

And please, excuse me for the bad english. I'm not an english speaker.
This text was first posted at the portuguese ubuntu forum, at:

[http://ubuntuforum-br.org/index.php?topic=74203.0](http://ubuntuforum-br.org/index.php?topic=74203.0)

---

