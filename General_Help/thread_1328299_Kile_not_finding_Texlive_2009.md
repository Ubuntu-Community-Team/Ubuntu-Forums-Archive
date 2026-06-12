---
title: "Kile not finding Texlive 2009"
date: 2009-11-16
forum: General Help
---

### Post by tdc500 on 2009-11-16
Following this set of instructions

[http://texblog.net/latex-archive/linux/kile-texlive-2008-equivs/](http://texblog.net/latex-archive/linux/kile-texlive-2008-equivs/)

I installed texlive 2009 and Kile 2.1b onto my computer (virtual machine running Kubuntu Netbook remix) and can start Kile fine, however when i come to compile it I recieve an error (127) and using the system check tool i discover that Kile cannot find the latex or tex installation.

Could someone help me please

Cheers,
Tim

---

### Post by tdc500 on 2009-11-16
oh the irony, been trying to solve this all day, and i get it working 20 mins after posting something here.

The solution was from here [http://ubuntuforums.org/showthread.php?t=1311444&highlight=texlive+2009](http://ubuntuforums.org/showthread.php?t=1311444&highlight=texlive+2009)

modify the ~/.profile file so it reads ```
# ~/.profile: executed by the command interpreter for login shells.
# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# exists.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/profile; for setting the umask
# for ssh logins, install and configure the libpam-umask package.
#umask 022

# if running bash
if [ -n "$BASH_VERSION" ]; then
    # include .bashrc if it exists
    if [ -f "$HOME/.bashrc" ]; then
	. "$HOME/.bashrc"
    fi
fi

# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi
if [ -d "/usr/local/texlive/2009/bin/i386-linux" ] ; then
    PATH="/usr/local/texlive/2009/bin/i386-linux:$PATH"
fi
if [ -d "/usr/local/texlive/2009/texmf" ] ; then
    export TEXMFMAIN="/usr/local/texlive/2009/texmf"
fi
if [ -d "/usr/local/texlive/2009/texmf-dist" ] ; then
    export TEXMFDIST="/usr/local/texlive/2009/texmf-dist"
fi
if [ -d "/usr/local/texlive/texmf-local" ] ; then
    export TEXMFLOCAL="/usr/local/texlive/texmf-local"
fi
if [ -d "$HOME/texmf" ] ; then
    export TEXMFHOME="$HOME/texmf"
fi
if [ -d "$HOME/.texlive2009/texmf-config" ] ; then
    export TEXMFCONFIG="$HOME"
fi
if [ -d "/usr/local/texlive/2009/texmf-config" ] ; then
    export TEXMFSYSCONFIG="/usr/local/texlive/2009/texmf-config"
fi
if [ -d "$HOME/.texlive2009/texmf-var" ] ; then
    export TEXMFVAR="$HOME"
fi
if [ -d "/usr/local/texlive/2009/texmf-var" ] ; then
    export TEXMFSYSVAR="/usr/local/texlive/2009/texmf-var"
fi
```

---

### Post by gitane79 on 2009-11-18
Hello, I followed +- the same approach as tcd500, but Kile still cannot find LaTeX installed from the Texlive 2009 distribution :-?
Below I will summarise the followed approach on a machine with Ubuntu 9.10 using Kile 2.0.83 a.k.a. 2.1 beta 2, kernel 2.6.31-15

- Can somebody please tell what is missing here? -

**Install Texlive 2009**

[LIST=1]
[*]Start the Synaptic package manager and remove all packages related to Kile and Texlive
[*]Download the Texlive network installer from [html]http://www.tug.org/texlive/acquire-netinstall.html[/html] This installer can be used to download and install the latest version of Texlive
[*]Extract the installer to $HOME/install-tl
[*]Start the graphical Texlive installer with perl:```
sudo apt-get update
``````
sudo apt-get install perl-tk
``````
sudo $HOME/install-tl/install-tl --gui=perltk
```
[*]Select the elements to be installed, or simply choose “Selected scheme”: medium scheme (plain,latex,recommended packages and some languages). This will require about 600 Mb. Finish the installation
[*]Tell Bash where to look for the Texlive programs:```
sudo gedit $HOME/.profile
```Add the following lines at the end and save:```
if [ -d "/usr/local/texlive/2009/bin/i386-linux" ] ; then 
    PATH="/usr/local/texlive/2009/bin/i386-linux:$PATH" 
fi 
if [ -d "/usr/local/texlive/2009/texmf" ] ; then 
    export TEXMFMAIN="/usr/local/texlive/2009/texmf" 
fi 
if [ -d "/usr/local/texlive/2009/texmf-dist" ] ; then 
    export TEXMFDIST="/usr/local/texlive/2009/texmf-dist" 
fi 
if [ -d "/usr/local/texlive/texmf-local" ] ; then 
    export TEXMFLOCAL="/usr/local/texlive/texmf-local" 
fi 
if [ -d "$HOME/texmf" ] ; then 
    export TEXMFHOME="$HOME/texmf" 
fi 
if [ -d "$HOME/.texlive2009/texmf-config" ] ; then 
    export TEXMFCONFIG="$HOME" 
fi 
if [ -d "/usr/local/texlive/2009/texmf-config" ] ; then 
    export TEXMFSYSCONFIG="/usr/local/texlive/2009/texmf-config" 
fi 
if [ -d "$HOME/.texlive2009/texmf-var" ] ; then 
    export TEXMFVAR="$HOME" 
fi 
if [ -d "/usr/local/texlive/2009/texmf-var" ] ; then 
    export TEXMFSYSVAR="/usr/local/texlive/2009/texmf-var" 
fi
```
[*]Remove Texlive installation files:```
rm -R -f $HOME/install-tl
```
[/LIST]
**Trying to make it work with Kile**
In order to be able to install Kile, it will require that its dependencies are satisfied. As Texlive 2009 is not available from the repositories, we need to confirm the installation of Texlive 2009 to Kile by creating a dummy package for Texlive:

[LIST=1]
[*]```
sudo apt-get install equivs && cd $HOME/install-tl && gedit ./texlive.ctl
```Add the following lines and save:```
Section: tex 
Package: texlive-dummy 
Provides: tex-common, texlive-common, texlive-latex-base, texlive-metapost, texlive-xetex, texlive-base-bin, texlive-base-bin-doc 
Description: texlive dummy package 
 This package provides dpkg with the 
 information that there are certain tex 
 packages installed.
```(note that the lines below “Description” must begin with one white space)
[*]```
equivs-build texlive.ctl && sudo dpkg -i texlive-dummy_1.0_all.deb
```
[*]Next, install Kile:```
sudo apt-get install kile
```
[/LIST]

---

### Post by beke on 2009-11-30
@gitane: Did you logout/login? 

This is necessary to use the updated .profile.

---

### Post by gitane79 on 2009-12-02
> **beke said:**
> @gitane: Did you logout/login? 

This is necessary to use the updated .profile.

Thanks for your reply.
Yes I did, I even restarted the computer but to no avail: I still cannot compile directly from Kile using Texlive2009.

Somehow it should be possible to point Kile to the latex program...

Compiling works fine from terminal, but this method is rather cumbersome. I prefer to just press alt+6 in Kile to compile directly.

Did anyone find a solution?

---

