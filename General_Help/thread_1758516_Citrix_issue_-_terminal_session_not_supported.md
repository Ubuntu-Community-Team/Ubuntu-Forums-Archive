---
title: "Citrix issue - terminal session not supported"
date: 2011-05-14
forum: General Help
---

### Post by joanna_ford on 2011-05-14
Can anyone help me with my Citrix installation issue on xubuntu?  I followed these instructions:

> First step is to get the tar.gz file from here:

[http://www.citrix.com/English/ss/dow...&productId=186]("http://www.citrix.com/English/ss/downloads/details.asp?downloadId=3323&productId=186")

IMPORTANT!
You want the en.linuxx86.tar.gz one with x86 client - requires OpenMotif 2.2.x 

Save it to your desktop.

Extract en.linnuxx86.tar.gz by double clicking it.
Click the Extract button at the top.
Click create folder and in the blue field that says "Type name of new folder"
put in "icainstall" (without the quotes) hit enter and then click the Extract button in the lower right corner.

You will now have a folder on your desktop named icainstall.

Open a terminal and cd to the icainstall directory.
     Code:
     cd Desktop/icainstall/ 
type the following command:
     Code:
     sudo ./setupwfc 
Give it your regular password when requested.

It should look like this:
     Code:
     Select a setup option:

 1. Install Citrix Presentation Server Client 10.6
 2. Remove Citrix Presentation Server Client 10.6
 3. Quit Citrix Presentation Server Client 10.6 setup

Enter option number 1-3 [1]: 
Enter the default of 1, then at the following prompts for default  location and integration with gnome and kde also use the defaults.

At the end it will present with the setup options choices again, just choose #3 to exit.

At the command prompt, enter the following:
     Code:
     sudo apt-get install libmotif3 
Close the terminal.

Alternatively, using the gui, you can install the  libmotif3 package  from synaptic.  But since the terminal was already open, I figured, what  the heck.  

All Done!!!

You will now have the entries... Applications > Internet > Citrix  CNA and Citrix Presentation Server Client.  You will also have ICA  enabled in Terminal Services Client and the Citrix plugin should be in  Firefox.I get the message "terminal session not supported" when I seem to be in Citrix and trying to access an application.

Somewhere on the web I found a suggested fix saying you needed Sun Java 5 plug-in but this no longer seems to be available.

Can anyone help pleeease?!

Thanks,

Jo :)

---

