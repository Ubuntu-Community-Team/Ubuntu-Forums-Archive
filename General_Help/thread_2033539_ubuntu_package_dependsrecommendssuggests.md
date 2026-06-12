---
title: "ubuntu package: depends/recommends/suggests"
date: 2012-07-26
forum: General Help
---

### Post by asdfA on 2012-07-26
Hello - I noticed that the standard Ubuntu package download page displays a list of related packages: depends/recommends/suggests

I come from the Windows world where a software installation package generally installs dependencies required for the software to be successfully installed and run.

I'm brand new to the Ubuntu world. So do packages generally include the dependencies that are listed on the download page to ensure a proper installation?  Or are the most common dependencies for Ubuntu packages typically installed by default with a core Ubuntu installation?  Or do Ubuntu packages really require the user to explicitly install all of the dependency packages listed on the software download page?

---

### Post by elliotn on 2012-07-26
if u have internet then there is no need to go to that site for software, open terminal

 > sudo apt-get update

then
> sudo apt-get install synaptic 

you can replace synaptic with eg vlc etc but alternatively u can use software center

---

### Post by asdfA on 2012-07-26
elliot - I followed your advice.  First I executed a command for: sudo apt-get update

The terminal printed out several lines to the console in the format: Hit [ubuntu path]

Then I executed a command for: sudo apt-get synaptic

The terminal printed out the following error: "Invalid operation synaptic"

I also tried: sudo apt-get aptitude

The terminal printed out the following error: "Invalid operation aptitude"

So something seems off here....

---

### Post by drmrgd on 2012-07-26
> **asdfA said:**
> Hello - I noticed that the standard Ubuntu package download page displays a list of related packages: depends/recommends/suggests

I come from the Windows world where a software installation package generally installs dependencies required for the software to be successfully installed and run.

I'm brand new to the Ubuntu world. So do packages generally include the dependencies that are listed on the download page to ensure a proper installation?  Or are the most common dependencies for Ubuntu packages typically installed by default with a core Ubuntu installation?  Or do Ubuntu packages really require the user to explicitly install all of the dependency packages listed on the software download page?

If you install packages through the Software Center or using the 'apt-get' utility in the terminal, new packages will generally also install the dependencies required to use the package.  This is the recommended way of installing packages for that reason and for the reason that the packages are checked to be sure they're safe for your system.

If you try to install packages the Windows way (i.e. go to a website, download a package, and manually install it), you'll often have to find and install the dependencies yourself.

---

### Post by drmrgd on 2012-07-26
> **asdfA said:**
> elliot - I followed your advice.  First I executed a command for: sudo apt-get update

The terminal printed out several lines to the console in the format: Hit [ubuntu path]

Then I executed a command for: sudo apt-get synaptic

The terminal printed out the following error: "Invalid operation synaptic"

I also tried: sudo apt-get aptitude

The terminal printed out the following error: "Invalid operation aptitude"

So something seems off here....

Your syntax is not quite right.  You'll need to run (for example):

```
sudo apt-get install synaptic
```

Here is some Ubuntu Community documentation on installing packages that you might find informative:

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

---

### Post by asdfA on 2012-07-26
Thanks for your help everyone. I was able to successfully install aptitude through the terminal.

I was assuming that I would be able to find Aptitude through the top left Search icon in Ubuntu.  For example, type "Aptitude" into the Search bar and the Aptitude program icon would display in the area below.

However, I tried the steps above and the Aptitude program icon did not display.  Is Aptitude a command line program which is why it doesn't display this way?  Also, I thought it was interesting that all the program icons on the left side of Ubuntu display tooltips but the Search icon doesn't.  I wonder why Ubuntu decided not use a tooltip for the Search program?

---

### Post by wheeze on 2012-07-26
> **asdfA said:**
> I was assuming that I would be able to find Aptitude through the top left Search icon in Ubuntu.  For example, type "Aptitude" into the Search bar and the Aptitude program icon would display in the area below.

However, I tried the steps above and the Aptitude program icon did not display.  Is Aptitude a command line program which is why it doesn't display this way?

That is correct. Aptitude is a console application, it runs in a terminal session.

For a GUI package management app Synaptic is the one you want.

---

### Post by drmrgd on 2012-07-26
> **asdfA said:**
> Thanks for your help everyone. I was able to successfully install aptitude through the terminal.

I was assuming that I would be able to find Aptitude through the top left Search icon in Ubuntu.  For example, type "Aptitude" into the Search bar and the Aptitude program icon would display in the area below.

However, I tried the steps above and the Aptitude program icon did not display.  Is Aptitude a command line program which is why it doesn't display this way?  Also, I thought it was interesting that all the program icons on the left side of Ubuntu display tooltips but the Search icon doesn't.  I wonder why Ubuntu decided not use a tooltip for the Search program?

I believe Aptitude is strictly a command line only tool.  FWIW, I think just using the built in package managers will fit your needs most of the time, and if nothing else, I would say add Synaptic to the system as that does seem to give more control, options, and is graphical.

---

