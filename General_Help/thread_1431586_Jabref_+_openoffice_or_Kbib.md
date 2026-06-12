---
title: "Jabref + openoffice or Kbib"
date: 2010-03-16
forum: General Help
---

### Post by Hesediel on 2010-03-16
I'm trying to use Jabref for references...i read there is a plugin for work jabref with write of openoffice...

[http://www.itk.ntnu.no/ansatte/Alver_Omholt_Morten/jabref/OOPlugin.html](http://www.itk.ntnu.no/ansatte/Alver_Omholt_Morten/jabref/OOPlugin.html)


But some one can tell me how to install it??


I tryed Kbib too...but how can i add my references to openoffice if i select "add reference i got in the server pipe--??

---

### Post by n0dix on 2010-03-16
Did you try in [this]("http://jabref.sourceforge.net/resources.php") way?

---

### Post by Hesediel on 2010-03-17
i've installed jabref 203 from repositories, and there isn't a plugin manager. I downloaded the .jar of jabref but i didn't understand how to install it

---

### Post by Hesediel on 2010-03-19
nobody can help me?

---

### Post by daudi on 2010-05-12
Thread is a bit old but in case it helps anyone I have just installed the plugin without any problem. I am using the latest version is version of jabref (2.6) and followed the instructions on the jabref website.

---

### Post by caitifty on 2010-08-08
Definitely an old thread, but with a current 10.04 install, do:

Admin -> Synaptic

Search for and install Jabref.  Search for and install openoffice.org-java-common (it probably wasn't automatically installed when openoffice was installed).

Open a browser and go to:

[http://www.itk.ntnu.no/ansatte/Alver_Omholt_Morten/jabref/OOPlugin.html](http://www.itk.ntnu.no/ansatte/Alver_Omholt_Morten/jabref/OOPlugin.html)

Scroll to the bottom of the page to the downloads section, right click the link that says 'the plugin', and select 'copy link address' (or your browser's equivalent).

Open Jabref.  Click Plugins -> Manage plugins

Click the button labeled 'Download Plugin'

In the url field that opens, paste the link you just copied.
You should get a message saying the plugin was successfully installed and that you need to restart Jabref.  Restart Jabref.

In the plugins menu there should now be an 'openoffice.org panel' item.  Clicking it will add a panel on the left with all the options provided by the plugin.  Restart openoffice.

Some post-install issues:

- you need at least one style file before jabref will let you connect to openoffice.  Easiest way to get one is go back to [http://www.itk.ntnu.no/ansatte/Alver_Omholt_Morten/jabref/OOPlugin.html](http://www.itk.ntnu.no/ansatte/Alver_Omholt_Morten/jabref/OOPlugin.html), scroll down to the downloads section, right-click on 'example style file' and 'save link as..' to your desktop or somewhere similar.  Back in jabref, click the 'select style file' button in the openoffice.org panel, click 'add file' and navigate to the style file you just downloaded.

- there's two 'connect' buttons in the openoffice.org panel in jabref.  Click the left-most 'auto connect' button.  If this gives you a failure message, click the 'manual connect' button, and delete everything in the 'path to openoffice library dir' field.  Click connect again and this time it should work.  You may need to restart openoffice too.

---

### Post by eming on 2010-11-25
> **caitifty said:**
> Definitely an old thread, but with a current 10.04 install, do:

Admin -> Synaptic

Search for and install Jabref.  Search for and install openoffice.org-java-common (it probably wasn't automatically installed when openoffice was installed).

Open a browser and go to:

[http://www.itk.ntnu.no/ansatte/Alver_Omholt_Morten/jabref/OOPlugin.html](http://www.itk.ntnu.no/ansatte/Alver_Omholt_Morten/jabref/OOPlugin.html)

Scroll to the bottom of the page to the downloads section, right click the link that says 'the plugin', and select 'copy link address' (or your browser's equivalent).

Open Jabref.  Click Plugins -> Manage plugins

Click the button labeled 'Download Plugin'

In the url field that opens, paste the link you just copied.
You should get a message saying the plugin was successfully installed and that you need to restart Jabref.  Restart Jabref.

In the plugins menu there should now be an 'openoffice.org panel' item.  Clicking it will add a panel on the left with all the options provided by the plugin.  Restart openoffice.

Some post-install issues:

- you need at least one style file before jabref will let you connect to openoffice.  Easiest way to get one is go back to [http://www.itk.ntnu.no/ansatte/Alver_Omholt_Morten/jabref/OOPlugin.html](http://www.itk.ntnu.no/ansatte/Alver_Omholt_Morten/jabref/OOPlugin.html), scroll down to the downloads section, right-click on 'example style file' and 'save link as..' to your desktop or somewhere similar.  Back in jabref, click the 'select style file' button in the openoffice.org panel, click 'add file' and navigate to the style file you just downloaded.

- there's two 'connect' buttons in the openoffice.org panel in jabref.  Click the left-most 'auto connect' button.  If this gives you a failure message, click the 'manual connect' button, and delete everything in the 'path to openoffice library dir' field.  Click connect again and this time it should work.  You may need to restart openoffice too.
-------------------------------------------------
Now, the problem is the style file.
In fact, there's only an example style file for formating paper. If one journal  rejects this paper, we need to change another style. It's not conveniently to write another style file for a new journal. 
Is there a plug-in containing most SCI journal style files?

---

