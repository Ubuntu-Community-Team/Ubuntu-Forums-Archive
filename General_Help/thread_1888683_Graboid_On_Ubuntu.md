---
title: "Graboid On Ubuntu"
date: 2011-11-29
forum: General Help
---

### Post by thestagevu on 2011-11-29
Watch the video here :   [http://www.youtube.com/watch?v=V1iHDLN6wd0](http://www.youtube.com/watch?v=V1iHDLN6wd0)



These steps were all done using Ubuntu.
The fist thing you want to do is gather the necessary tools. 

To do this click on System-Administration-Synaptic Packet Manager 

Once the packet manager loads up enter "wine" into the quick search box and scroll down the list until you find Wine 1.2 and a program called WineTricks mark both of these packages for installation by clicking the box beside them and click "apply" at the top. 

This will install Wine, which is a windows compatibility layer needed for Graboid to run its DLL's. Winetricks is a neat little program which makes it easy to download needed items from the linux repositories specifically designed to work with Wine. 

Once the programs are installed you should see a new section under your applications bar that says Wine. Don't worry about editing the config settings or playing around inside your new C: drive because it's about to get deleted in the next step. 

Open up your terminal under applications-accessories-terminal. Type in rm -rf .wine this will delete your Wine folder along with some of the extras that come with the program. This is necessary, because without doing this you will run into a bunch of errors when you try to install .NET Framework. Next, type sh winetricks into your terminal. This will re-create your Wine directory with only the bare essentials needed to run wine, it will also bring up a dialog similar to your package manager. Scroll down the list and select "dotnet20", and click ok.

---

